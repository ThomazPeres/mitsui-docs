# Calcular

Campos do produto **MS Construção** (`constructionworks`).

{% hint style="info" %}
Endpoint, headers, envelope do body, criação e recálculo do contrato, formato da resposta e erros estão em [Calcular](../calcular.md).
{% endhint %}

## Calcular

<mark style="color:green;">`POST`</mark> {**URL**}/calculate

**Body**

[**Aqui**](calcular.md#definindo-campos-de-envio)**, segue uma explicação dos campos**

```postman_json
{
    "ProductCode": "constructionworks",
    "CalculationSettings": {
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
    },
    "fields": [
        {
            "code": "quotation-type",
            "value": "new"
        },
        {
            "code": "insured-identity",
            "value": "12345678000199"
        },
        {
            "code": "insured-name",
            "value": "EMPRESA EXEMPLO LTDA"
        },
        {
            "code": "iof-exempt",
            "value": "false"
        },
        {
            "code": "works-start-date",
            "value": "2026-12-01T00:00:00-03:00"
        },
        {
            "code": "works-end-date",
            "value": "2027-05-30T00:00:00-03:00"
        },
        {
            "code": "vigency-start-date",
            "value": "2026-12-01T00:00:00-03:00"
        },
        {
            "code": "risk-value",
            "value": "1000000.00"
        },
        {
            "code": "occupation",
            "label": "Aeroportos",
            "value": "01"
        },
        {
            "code": "classification-id",
            "label": "Obras e/ou Instalação de elevadores e/ou escadas rolantes - LADO TERRA",
            "value": "001-03"
        },
        {
            "locationId": "1",
            "code": "risk-location-zipcode",
            "value": "90240-601"
        },
        {
            "locationId": "1",
            "code": "risk-location-street",
            "value": "Av. Paraná"
        },
        {
            "locationId": "1",
            "code": "risk-location-number",
            "value": "1761"
        },
        {
            "locationId": "1",
            "code": "risk-location-neighborhood",
            "value": "São Geraldo"
        },
        {
            "locationId": "1",
            "code": "risk-location-city",
            "label": "Porto Alegre",
            "value": "Porto Alegre"
        },
        {
            "locationId": "1",
            "code": "risk-location-state",
            "label": "RS",
            "value": "RS"
        }
    ],
    "coverages": [
        {
            "itemId": "1",
            "coverages": [
                {
                    "coverage-code": "67001",
                    "coverage-lmi": "R$500.000,00",
                    "coverage-deductible": {
                        "label": "10% prej. ind. Min R$ 25.000,00",
                        "value": "1-2-99999-99999-0-30000000.00-99999"
                    },
                    "coverage-risk-profile": [
                        {
                            "code": "01",
                            "label": "Não",
                            "value": "2"
                        },
                        {
                            "code": "02",
                            "label": "Não",
                            "value": "2"
                        },
                        {
                            "code": "04",
                            "label": "Não",
                            "value": "2"
                        },
                        {
                            "code": "05",
                            "label": "Não",
                            "value": "2"
                        },
                        {
                            "code": "06",
                            "label": "Não",
                            "value": "2"
                        },
                        {
                            "code": "07",
                            "label": "Não",
                            "value": "2"
                        }
                    ]
                },
                {
                    "coverage-code": "67074",
                    "coverage-lmi": "R$500.000,00",
                    "coverage-deductible": {
                        "label": "10% prej. ind. Min R$ 25.000,00",
                        "value": "1-2-99999-99999-0-30000000.00-99999"
                    }
                }
            ]
        }
    ]
}
```

{% hint style="info" %}
Segmento, tipo de obra, LMI e franquia do exemplo são ilustrativos. Use os valores retornados pelas [consultas do produto](consultas.md).
{% endhint %}

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
    "contractId": "MC9043703374",
    "response": {
        "prize": {
            "planId": "1",
            "items": [
                {
                    "itemId": "1",
                    "calculationId": "300041210",
                    "coverages": [
                        {
                            "id": "67001",
                            "totalValue": 536.90
                        },
                        {
                            "id": "67074",
                            "totalValue": 536.90
                        }
                    ],
                    "totalValue": 1073.80,
                    "netValue": 1000.00,
                    "taxValue": 73.80,
                    "success": true
                }
            ],
            "totalValue": 1073.80,
            "netValue": 1000.00,
            "taxValue": 73.80,
            "success": true
        }
    }
}
```
{% endtab %}

{% tab title="400" %}
```json
{
    "warnings": [],
    "restrictions": [
        {
            "message": "Tipo de obra deve ser informado.",
            "itemId": "1"
        }
    ]
}
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Retorno completo e catálogo de erros em [Resposta](../calcular.md#resposta) e [Erros](../calcular.md#erros).
{% endhint %}

## Definindo campos de envio.

> **Product Code:** `constructionworks`.
>
> \
> **Produtos disponiveis neste endpoint:** [Buscar Produto.](../servicos-de-consulta/calculo.md#buscar-produtos)

> **CalculationSettings:** Comissão, desconto e agravo. Ver [CalculationSettings](../calcular.md#calculationsettings).

{% hint style="info" %}
As regras de preenchimento de `fields` (obrigatoriedade, `label`, `itemId`, `clear` e o que acontece ao reenviar o cálculo) estão em [Regras de fields](../calcular.md#regras-de-fields).
{% endhint %}

{% hint style="warning" %}
**A ordem dos campos dentro de `fields` importa:**

* Envie `occupation` **antes** de `classification-id`. Trocar o segmento limpa o tipo de obra já gravado.
* Em cada local da obra, envie `risk-location-has-no-zipcode` (quando usado) **antes** dos demais campos do local. Mudar essa opção limpa o endereço do local.
{% endhint %}

### Contrato

> **quotation-type:** Tipo de cotação. Único valor aceito: `new` (Seguro novo). Não envie outro valor.

> **modality** e **plan-modality:** Não precisam ser enviados. O contrato é criado com a modalidade `5` e o plano `00005`. Se enviados, devem ter exatamente esses valores.

> **insured-identity:** CNPJ do segurado, com ou sem máscara. ❗Somente Pessoa Jurídica. Na proposta o CNPJ precisa constar como ativo.

> **insured-name:** Razão social do segurado. Caracteres especiais são removidos: `&` vira `E`, hífen e apóstrofo viram espaço e vírgulas são retiradas.

> **iof-exempt:** Isenção de IOF. Exatamente `"true"` ou `"false"`. Padrão `"false"`.

> **works-start-date:** Data de início da obra, em ISO 8601 (ex.: `2026-12-01T00:00:00-03:00`). A data é considerada como escrita, sem conversão de fuso.

> **works-end-date:** Data de fim da obra, em ISO 8601. ❗Obrigatório. Deve ser posterior ao início de vigência. Define o fim da vigência da apólice.

> **vigency-start-date:** Início de vigência, em ISO 8601. Opcional: o padrão é a data de criação do contrato. Não pode ser anterior ao início da obra.

> **risk-value:** Valor em risco da obra. ❗Obrigatório. Aceita `"1000000.00"` ou `"1.000.000,00"`.
>
> ❗Não use ponto como separador de milhar sem casas decimais: `"1.500"` é lido como 1,5.

> **occupation:** Segmento (as opções podem ser consultadas neste [endpoint](consultas.md#buscar-segmentos)). ❗Obrigatório.
>
> **label:** Descrição do segmento.

> **classification-id:** Tipo de obra (as opções podem ser consultadas neste [endpoint](consultas.md#buscar-tipos-de-obra), filtrando pelo segmento). ❗Obrigatório.
>
> **label:** Descrição do tipo de obra.

> **item-name:** Nome do item (**opcional**). O item `1` é criado automaticamente como "Plano 1".
>
> **itemId:** Sempre `"1"`. O MS Construção possui item único.

{% hint style="warning" %}
**Regras de vigência:**

* A vigência vai do `vigency-start-date` até o `works-end-date`.
* O início de vigência precisa estar dentro da janela permitida para a corretora.
* Vigência inferior a **5 dias** ou superior a **1.826 dias** gera restrição e não pode ser cotada por esta API.
* O tipo de cálculo é definido pelo servidor a partir do prazo: prazo curto (menos de 1 ano), anual ou plurianual.
{% endhint %}

### Campos preenchidos pelo servidor

Não envie estes campos. Se enviados, são ignorados.

| Campo                                                        | Como é preenchido                                                      |
| ------------------------------------------------------------ | ---------------------------------------------------------------------- |
| `vigency-end-date`                                           | Igual ao `works-end-date`                                              |
| `works-duration`, `works-progress`                           | Calculados a partir das datas da obra                                  |
| `calculation-type`                                           | Prazo curto, anual ou plurianual, conforme o prazo                     |
| `maintenance-vigency-start-date`, `maintenance-vigency-end-date` | Com a cobertura `67074`: do fim da obra até 12 meses depois        |
| `fire-vigency-start-date`, `fire-vigency-end-date`           | Com a cobertura `67093`: do fim da obra até 1 mês depois               |

{% hint style="warning" %}
**Campos de outros produtos que não existem no MS Construção** e são ignorados se enviados: `item-address-*`, `category-id`, `lost-profits`, `coverage-clause`, `tied-policy-*`, `co-insured-*`, os campos de renovação congênere e todos os campos de Pessoa Física.
{% endhint %}

### Locais da obra

Os endereços da obra são enviados em `fields`, com o `locationId` em cada campo. Cada `locationId` diferente cria um local. Envie ao menos um.

| Campo                             | Obrigatório                 | Descrição                                                                 |
| --------------------------------- | --------------------------- | ------------------------------------------------------------------------- |
| `risk-location-has-no-zipcode`    | Não                         | `"true"` quando o local não tem CEP. Padrão `"false"`                     |
| `risk-location-zipcode`           | Sim, com CEP                | CEP, com ou sem máscara                                                   |
| `risk-location-street`            | Sim, com CEP                | Logradouro                                                                |
| `risk-location-number`            | Sim, com CEP                | Número                                                                    |
| `risk-location-complement`        | Não                         | Complemento                                                               |
| `risk-location-complement-type`   | Não                         | Tipo de complemento (Andar, Apartamento, Bloco, Box, Casa, Conjunto, Frente, Lote, Quadra, Sala, Setor, Sobrado, Térreo) |
| `risk-location-neighborhood`      | Sim, com CEP                | Bairro                                                                    |
| `risk-location-city`              | Sim                         | Cidade, por extenso                                                       |
| `risk-location-state`             | Sim                         | UF (ex.: `RS`)                                                            |
| `risk-location-latitude`          | Sim, sem CEP                | Latitude com ponto decimal (ex.: `"-23.5505"`). Precisa estar no Brasil   |
| `risk-location-longitude`         | Sim, sem CEP                | Longitude com ponto decimal (ex.: `"-46.6333"`). Precisa estar no Brasil  |

```json
{
    "locationId": "1",
    "code": "risk-location-zipcode",
    "value": "90240-601"
}
```

> **locationId:** Identificador do local, definido por você. Qualquer texto serve. Os locais são numerados na ordem em que foram criados ("Local 1", "Local 2"), e essa numeração aparece nas mensagens de restrição.

> Para remover um local, envie um campo com o `locationId`, sem `code` e com `clear: true`.

{% hint style="warning" %}
Os locais da obra **não entram no cálculo do prêmio**. Eles são exigidos ao gerar a proposta: sem local, ou com endereço incompleto, a proposta é recusada.
{% endhint %}

### Coverages (Coberturas)

Coberturas selecionadas, as coberturas disponiveis para contratação seguem disponiveis nesse endpoint: [Buscar Coberturas](consultas.md#buscar-coberturas)

O que enviar no objeto de coverages:

{% code overflow="wrap" %}
```json
{
    "itemId": "1",
    "coverages": [
        {
            "coverage-code": Código da cobertura,
            "coverage-lmi": Valor da cobertura (dentro de lmiLimit),
            "coverage-deductible": {
                "label": Descrição da franquia selecionada,
                "value": Código da franquia selecionada
            },
            "coverage-risk-profile": [
                {
                    "code": Código da pergunta (riskProfile.questions[].code),
                    "label": Descrição da resposta (opcional),
                    "value": Código da resposta (1 = Sim, 2 = Não)
                }
            ]
        }
    ]
},
```
{% endcode %}

> **itemId:** Sempre `"1"`.

> **coverage-lmi:** Obrigatório. Deve estar dentro do `lmiLimit` da cobertura. Aceita `"500000.00"`, `"500.000,00"` ou `"R$500.000,00"`.

> **coverage-deductible:** ❗Obrigatório em todas as coberturas. O `value` deve ser uma das franquias retornadas para a cobertura, e o LMI deve estar dentro da faixa (`lmiLimit`) da franquia escolhida.

> **coverage-risk-profile:** Respostas das perguntas de perfil de risco. Enviado somente na cobertura básica `67001`.

{% hint style="warning" %}
**Regras de validação das coberturas:**

* A cobertura básica `67001` é obrigatória. As adicionais são opcionais.
* O LMI de uma adicional não pode ser maior que o LMI da básica.
* Na `67001`, responda as perguntas `01`, `02`, `04`, `05`, `06` e `07`. Responda a `03` somente quando `02` = Sim.
* Responder pergunta em outra cobertura, ou a `03` com `02` = Não, gera restrição.
* Sim nas perguntas `01`, `03` ou `04` recusa o risco.
* Códigos de cobertura que não existem no produto são descartados sem erro.
{% endhint %}

### Restrições comuns

| Mensagem                                                                                   | Causa                                                    |
| ------------------------------------------------------------------------------------------ | -------------------------------------------------------- |
| `Segmento deve ser informado.`                                                             | `occupation` ausente                                     |
| `Tipo de obra deve ser informado.`                                                         | `classification-id` ausente ou limpo pela troca de segmento |
| `Valor do risco deve ser informado.`                                                       | `risk-value` ausente                                     |
| `Valor em risco não deve ser superior a {valor}.`                                          | Valor em risco acima do teto da corretora                |
| `Data de fim da obra deve ser informada.`                                                  | `works-end-date` ausente                                 |
| `A data de fim da obra deve ser posterior ao início de vigência.`                          | Fim da obra igual ou anterior ao início de vigência      |
| `O início de vigência não pode ser anterior ao início da obra.`                            | `vigency-start-date` anterior a `works-start-date`       |
| `Vigência inferior a 5 dias, fora do limite de aceitação automática. (...)`                 | Vigência menor que 5 dias                                |
| `A vigência deve ter no máximo 1826 dias. (...)`                                           | Vigência maior que 1.826 dias                            |
| `É necessário contratar a cobertura básica.`                                               | `67001` ausente                                          |
| `LMI da cobertura '{cobertura}' deve estar dentro do limite de: {mínimo} e {máximo}.`     | LMI fora do `lmiLimit`                                   |
| `O LMI da cobertura '{cobertura}' não pode ser superior ao maior LMI das coberturas básicas ({valor}).` | Adicional com LMI maior que a básica          |
| `Franquia da cobertura '{cobertura}' não está dentro da faixa de LMI permitida de {mínimo} à {máximo}.` | Franquia incompatível com o LMI               |
| `Pergunta {código} não respondida. (...)`                                                  | Pergunta de perfil de risco sem resposta                 |
| `Risco recusado. (...)`                                                                    | Sim nas perguntas `01`, `03` ou `04`                     |
