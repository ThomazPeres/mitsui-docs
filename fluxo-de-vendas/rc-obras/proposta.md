# Proposta

## Gerar proposta

<mark style="color:green;">`POST`</mark> {**URL**}/proposal

**Headers**

| Name          | Value              |
| ------------- | ------------------ |
| Content-Type  | `application/json` |
| Authorization | `Bearer <token>`   |
| username      | { Username }       |

**Body**

**Aqui, segue uma explicação dos campos.**

{% hint style="warning" %}
No RC Obras o segurado é sempre <mark style="color:yellow;">**Pessoa Jurídica**</mark>. Não existem campos de Pessoa Física, beneficiários, outros seguros nem inspeção.

O envio é o mesmo para Apólice Aberta e Apólice Fechada. Os **locais da obra** da Apólice Fechada são enviados no [Calcular](calcular.md#locais-da-obra-apolice-fechada), não na proposta.

Na proposta também é enviado os dados do pagamento e na transmissão realizado o pagamento de fato.
{% endhint %}

```postman_json
{
    "contractId": "{{contractId}}",
    "proposalSurvey": [
        {
            "code": "insured-cellphone",
            "value": "11999999999"
        },
        {
            "code": "insured-email",
            "value": "contato@empresaexemplo.com.br"
        },
        {
            "code": "insured-cnae",
            "label": "Construção de edifícios",
            "value": "4120400"
        },
        {
            "code": "insured-address-zipcode",
            "value": "90240-601"
        },
        {
            "code": "insured-address-street",
            "value": "Av. Paraná"
        },
        {
            "code": "insured-address-number",
            "value": "1761"
        },
        {
            "code": "insured-address-neighborhood",
            "value": "São Geraldo"
        },
        {
            "code": "insured-address-city",
            "value": "Porto Alegre"
        },
        {
            "code": "insured-address-state",
            "value": "RS"
        }
    ],
    "CoBrokerageDistribution": [],
    "PaymentSurvey": [
        {
            "code": "payment-method-id",
            "value": "3"
        },
        {
            "code": "payment-installment-code",
            "value": "40514"
        },
        {
            "code": "payment-day",
            "value": "15"
        }
    ]
}
```

**Response**

{% tabs %}
{% tab title="200" %}
```json
Retorna todo o contrato e o método de pagamento utilizado.
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
A proposta só é gerada se o contrato estiver calculado e o cálculo ainda estiver válido. Se expirou, faça um novo [Calcular](calcular.md) no mesmo contrato.
{% endhint %}

## Definindo campos de envio e opções.

> **insured-cnae:** Código de cnae selecionado. Pode ser consultado neste [endpoint](../servicos-de-consulta/proposta.md#buscar-atividades-e-cnae). ❗Obrigatório.

> **insured-cellphone:** Celular do segurado. ❗Obrigatório.

> **insured-email:** Email do segurado. ❗Obrigatório.

> **insured-address-zipcode:** CEP do segurado.

> **insured-address-street:** Rua do segurado.

> **insured-address-number:** Número do endereço do segurado.

> **insured-address-complement:** Complemento do segurado (**opcional**).

> **insured-address-complement-type:** Tipo de complemento do segurado (**opcional**).

> **insured-address-neighborhood:** Bairro do segurado.

> **insured-address-city:** Cidade do segurado.

> **insured-address-state:** Estado do segurado.

{% hint style="info" %}
Na **Apólice Aberta** o endereço do segurado também é usado como local de risco na emissão.
{% endhint %}

{% hint style="warning" %}
**Validações ao gerar a proposta:**

* CNPJ do segurado ativo na Receita Federal.
* Celular, email, CNAE e endereço do segurado preenchidos.
* **Apólice Fechada:** ao menos um local da obra, com endereço completo: CEP, logradouro, número, bairro, cidade e UF, ou latitude, longitude, cidade e UF para local sem CEP.

Mensagens de exemplo: `Pelo menos um local da obra deve ser informado.`, `Endereço do local da obra deve ser completado. Local 1`, `CEP do local da obra deve ser informado. Local 1`.
{% endhint %}

{% hint style="warning" %}
**Campos de outros produtos que não existem no RC Obras:** `insured-document-*`, `insured-transmitting-organ`, `insured-emission-date`, `insured-data-birth`, `insured-pep`, `insured-salary-range`, `insured-profession`, `beneficiary-*`, `tied-policy-*`, `inspection-*` e `use-first-item-address`. Cossegurados e cosseguro não estão disponíveis nesta API.
{% endhint %}

### Métodos de pagamento

Idênticos ao Empresarial. Consulte [Métodos de pagamento](../empresarial/proposta.md#metodos-de-pagamento) e obtenha as opções em [Buscar métodos de pagamentos](../servicos-de-consulta/proposta.md#buscar-metodos-de-pagamentos).

### Co-corretagem

`CoBrokerageDistribution` é aceito, mas não é aplicado. A co-corretagem cadastrada para a corretora é aplicada automaticamente na criação do contrato.
