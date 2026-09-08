---
description: Realiza o processo de salvamento e cálculo do contrato.
---

# Calcular

O `/calculate` salva os dados enviados no contrato e devolve o prêmio calculado. É o mesmo endpoint para todos os produtos: o que muda é o conteúdo de `fields` e `coverages`.

Os campos de cada produto estão em:

* [Calcular — Empresarial](empresarial/calcular.md)
* [Calcular — Responsabilidade Civil](responsabilidade-civil/calcular.md)

## Endpoint

<mark style="color:green;">`POST`</mark> {**URL**}/calculate

**Headers**

| Name                      | Value               |
| ------------------------- | ------------------- |
| Content-Type              | `application/json`  |
| ocp-apim-subscription-key | { Chave de acesso } |
| Authorization             | `Bearer <token>`    |
| username                  | { Username }        |

## Envelope do body

```json
{
    "contractId": "Opcional. Ausente cria um novo contrato.",
    "ProductCode": "Código do produto",
    "CalculationSettings": { },
    "fields": [ ],
    "coverages": [ ]
}
```

> **contractId:** Identificador do contrato. **Opcional**.

> **ProductCode:** Código do produto. Obtido em [Buscar produtos](servicos-de-consulta/calculo.md#buscar-produtos). Obrigatório ao criar um contrato.

> **CalculationSettings:** Configurações de comissão, desconto e agravo. **Opcional**.

> **fields:** Array com os dados da cotação.

> **coverages:** Array com as coberturas selecionadas por item.

{% hint style="info" %}
As propriedades de primeiro nível não diferenciam maiúsculas de minúsculas (`contractId` e `ContractId` funcionam), mas a convenção é camelCase.

Já as chaves internas em kebab-case, como `calculation-settings`, `coverage-code` e `coverage-lmi`, são fixas.
{% endhint %}

## Criar e recalcular

O mesmo endpoint cria o contrato e o recalcula. O comportamento depende de `contractId`.

> **Sem `contractId`:** cria um contrato novo, aplica os valores padrão do produto e devolve o `contractId` gerado. Guarde esse identificador para as chamadas seguintes (proposta, transmissão e documentos).

> **Com `contractId`:** salva as alterações no contrato existente e recalcula. Um `contractId` inexistente retorna **400**.

> **Com `contractId` e sem `fields`:** apenas recalcula, sem alterar dados. Nesse caso o `itemId` do primeiro nível filtra um item específico; enviar `"0"` recalcula todos os itens.

{% hint style="warning" %}
O cálculo só é permitido enquanto o contrato está na etapa de **cotação**.

Depois que a proposta é gerada, o endpoint retorna **400**. Contratos cancelados também retornam **400**.
{% endhint %}

## CalculationSettings

```json
{
    "calculation-settings": {
        "vp-contract": {
            "label": "",
            "value": ""
        },
        "commission-percentage": "25.0",
        "discount-percentage": "0.0",
        "increase-percentage": "0.0"
    },
    "co-brokerage": []
}
```

> **vp-contract:** Contrato VP aplicado à cotação. Enviar com `value` vazio quando não houver.

> **commission-percentage:** Comissão.

> **discount-percentage:** Desconto.

> **increase-percentage:** Agravo.

> **co-brokerage:** ❗Aceito e **ignorado** neste endpoint. A co-corretagem é aplicada na proposta, em `CoBrokerageDistribution`.

{% hint style="warning" %}
O objeto `CalculationSettings` é opcional, mas se `calculation-settings` for enviado os três percentuais passam a ser obrigatórios.

Os percentuais são texto e aceitam os formatos `"10"`, `"10.5"` e `"1.234,56"`.

Geram **restrição** na resposta: comissão fora da faixa permitida para a corretora, desconto acima do teto, agravo acima do teto, e desconto junto com agravo na mesma cotação.
{% endhint %}

## Regras de fields

`fields` é um array de objetos que descrevem os dados da cotação. Os códigos aceitos dependem do produto.

> **code:** Identificador do campo. **Obrigatório**.

> **value:** Valor do campo. **Obrigatório** e sempre do tipo **String**, inclusive para números e booleanos.

> **label:** Texto exibido do valor selecionado. É guardado junto do campo e usado nas cartas e PDFs.

> **itemId:** Associa o campo a um item da cotação.

> **clear:** Booleano. Quando `true`, limpa o campo em vez de atualizá-lo.

{% hint style="info" %}
* Um campo de item enviado **sem** `itemId` é ignorado.
* `clear: true`, ou `value` vazio, limpa o valor.
* Código desconhecido é ignorado silenciosamente, sem erro.
* Reenviar o cálculo no mesmo contrato **mescla** os campos: o que não for enviado mantém o valor anterior.
{% endhint %}

## Regras de coverages

`coverages` é um array por item. Cada entrada tem o `itemId` e a lista de coberturas contratadas daquele item.

```json
[
    {
        "itemId": "1",
        "coverages": []
    }
]
```

O conteúdo de cada cobertura muda por produto e está descrito na página do produto.

{% hint style="warning" %}
É necessário informar **no mínimo uma cobertura** por item, senão o retorno é **400**.

Diferente de `fields`, as coberturas são **substituídas** a cada chamada: toda cobertura que não for reenviada é removida do item.
{% endhint %}

## Resposta

O retorno traz o `contractId` e o prêmio calculado.

```json
{
    "contractId": "EM9539994702",
    "response": {
        "prize": {
            "items": [],
            "totalValue": 6219.83,
            "netValue": 5792.35,
            "taxValue": 427.48,
            "success": true
        }
    }
}
```

| Campo                                                              | Onde                  | Descrição                                        |
| ------------------------------------------------------------------ | --------------------- | ------------------------------------------------ |
| `planId`, `date`, `referenceDate`, `calculationDate`               | `prize`               | Identificação e datas do cálculo                 |
| `needsRecalculation`                                               | `prize`               | Indica que o contrato precisa ser recalculado    |
| `totalValue`, `netValue`, `taxValue`                               | `prize` e cada item   | Prêmio total, prêmio líquido e IOF               |
| `mocked`, `cached`, `success`, `isEmptyPrize`                      | `prize` e cada item   | Situação do cálculo                              |
| `items`                                                            | `prize`               | Um objeto por item calculado                     |
| `itemId`, `calculationId`                                          | cada item             | Identificação do item calculado                  |
| `coverages`                                                        | cada item             | Prêmio por cobertura                             |
| `id`, `totalValue`, `taxValue`                                     | cada cobertura        | Código da cobertura e valores                    |

{% hint style="info" %}
Campos com valor nulo, `false` ou zero são omitidos do retorno.

Dentro de `coverages` **não** vêm `netValue` nem `mocked`: esses valores existem apenas no item e no total.
{% endhint %}

## Erros

O endpoint tem dois formatos de erro.

**Notificações.** Retornadas em autenticação inválida, contrato não encontrado, etapa inválida e contrato cancelado. O corpo é um **array**.

{% tabs %}
{% tab title="400" %}
```json
[
    {
        "code": "3f2a1c9e-7b21-4f0e-9a55-2f8f5a0d1c44",
        "type": "Error",
        "message": "Step Proposal inválido para realizar essa operação."
    }
]
```
{% endtab %}

{% tab title="401" %}
```json
[
    {
        "code": "8c14b7d2-19af-4e63-8b0c-6d2e7a4f9b31",
        "type": "Error",
        "message": "Provided token is unvalid."
    }
]
```
{% endtab %}
{% endtabs %}

**Restrições de cálculo.** Retornadas quando os dados são válidos mas alguma regra comercial impede o cálculo. O corpo é um **objeto**.

{% tabs %}
{% tab title="400" %}
```json
{
    "warnings": [],
    "restrictions": [
        {
            "message": "Comissão fora da faixa permitida.",
            "itemId": "1"
        }
    ]
}
```
{% endtab %}
{% endtabs %}

| Status | Significado                                                              |
| ------ | ------------------------------------------------------------------------ |
| `200`  | Cálculo realizado                                                        |
| `400`  | Notificação de negócio ou restrição de cálculo                           |
| `401`  | Chave de acesso ou token inválidos                                       |
| `500`  | Erro interno. Tente novamente ou entre em contato                        |
