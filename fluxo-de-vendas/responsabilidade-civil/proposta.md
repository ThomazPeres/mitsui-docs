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
Em Responsabilidade Civil o segurado é sempre <mark style="color:yellow;">**Pessoa Jurídica**</mark>. Não existem campos de Pessoa Física, beneficiários nem inspeção.

O envio é o mesmo para RC Geral e Transporte RCG.

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
            "label": "Serviços de manutenção e reparação de caminhões, ônibus e outros veículos",
            "value": "5020202"
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
        },
        {
            "policyId": "1",
            "itemId": "1",
            "code": "tied-policy-company",
            "value": "PORTO SEGURO CIA DE SEGUROS GERAIS"
        },
        {
            "policyId": "1",
            "itemId": "1",
            "code": "tied-policy-number",
            "value": "2344"
        },
        {
            "policyId": "1",
            "itemId": "1",
            "code": "tied-policy-value",
            "value": "1.000,00"
        },
        {
            "policyId": "1",
            "itemId": "1",
            "code": "tied-policy-start-date",
            "value": "2020-08-23T00:00:00-05:00"
        },
        {
            "policyId": "1",
            "itemId": "1",
            "code": "tied-policy-end-date",
            "value": "2021-08-23T00:00:00-05:00"
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
A proposta só é gerada se o item estiver calculado. Com item único isso é automático após um [Calcular](calcular.md) com sucesso.
{% endhint %}

## Definindo campos de envio e opções.

> **insured-cnae:** Código de cnae selecionado. Pode ser consultado neste [endpoint](../servicos-de-consulta/proposta.md#buscar-atividades-e-cnae).

> **insured-cellphone:** Celular do segurado.

> **insured-email:** Email do segurado.

> **insured-address-zipcode:** CEP do segurado.

> **insured-address-street:** Rua do segurado.

> **insured-address-number:** Número do endereço do segurado.

> **insured-address-complement:** Complemento do segurado (**opcional**).

> **insured-address-complement-type:** Tipo de complemento do segurado (**opcional**).

> **insured-address-neighborhood:** Bairro do segurado.

> **insured-address-city:** Cidade do segurado.

> **insured-address-state:** Estado do segurado.

### Outros seguros (opcional)

> **tied-policy-company:** Seguradora da apólice. As seguradoras podem ser pesquisadas no [**endpoint**](../servicos-de-consulta/calculo.md#buscar-seguradoras)
>
> **itemId:** Sempre `"1"`.
>
> **policyId:** Id de outras apólices.

> **tied-policy-number:** Número da apólice.
>
> **itemId:** Sempre `"1"`.
>
> **policyId:** Id de outras apólices.

> **tied-policy-value:** Valor da apólice.
>
> **itemId:** Sempre `"1"`.
>
> **policyId:** Id de outras apólices.

> **tied-policy-start-date:** Data de início da vigência.
>
> **itemId:** Sempre `"1"`.
>
> **policyId:** Id de outras apólices.

> **tied-policy-end-date:** Data de fim da vigência.
>
> **itemId:** Sempre `"1"`.
>
> **policyId:** Id de outras apólices.

{% hint style="warning" %}
**Campos do Empresarial que não existem em Responsabilidade Civil:** `insured-document-*`, `insured-transmitting-organ`, `insured-emission-date`, `insured-data-birth`, `insured-pep`, `insured-salary-range`, `insured-profession`, `beneficiary-*`, `inspection-*` e `use-first-item-address`.
{% endhint %}

### Métodos de pagamento

Idênticos ao Empresarial. Consulte [Métodos de pagamento](../empresarial/proposta.md#metodos-de-pagamento) e obtenha as opções em [Buscar métodos de pagamentos](../servicos-de-consulta/proposta.md#buscar-metodos-de-pagamentos).

### Co-corretagem (opcional)

Idêntica ao Empresarial. Consulte [Co-corretagem](../empresarial/proposta.md#co-corretagem-opcional).
