# Proposta

## Buscar Atividades e CNAE

<mark style="color:green;">`GET`</mark>  {**URL**}/lookups/activities

**Headers**

| Name                      | Value               |
| ------------------------- | ------------------- |
| Content-Type              | `application/json`  |
| Authorization             | `Bearer <token>`    |
| ocp-apim-subscription-key | { Chave de Acesso } |
| username                  | { Username }        |

**Response**

{% tabs %}
{% tab title="200" %}
```json
[
    {
        "label": " Cultivo de arroz",
        "value": "0111201"
    }
    ...
]
```
{% endtab %}
{% endtabs %}



## Buscar Sálarios

<mark style="color:green;">`GET`</mark>  {**URL**}/lookups/salaryRanges

**Headers**

| Name                      | Value               |
| ------------------------- | ------------------- |
| Content-Type              | `application/json`  |
| Authorization             | `Bearer <token>`    |
| ocp-apim-subscription-key | { Chave de Acesso } |
| username                  | { Username }        |

**Response**

{% tabs %}
{% tab title="200" %}
```json
[
    {
        "label": "Não desejo informar",
        "value": "00000",
        "order": "AA"
    },
    {
        "label": "1,00 a 2.500,00",
        "value": "00001",
        "order": "AB"
    },
    {
        "label": "2.500,01 a 5.000,00",
        "value": "00002",
        "order": "AC"
    },
    {
        "label": "5.000,01 a 10.000,00",
        "value": "00003",
        "order": "AD"
    },
    {
        "label": "acima de 10.000,01",
        "value": "00004",
        "order": "AE"
    }
]
```
{% endtab %}
{% endtabs %}



## Buscar Profissões

<mark style="color:green;">`GET`</mark>  {**URL**}/lookups/professions

**Headers**

| Name                      | Value               |
| ------------------------- | ------------------- |
| Content-Type              | `application/json`  |
| Authorization             | `Bearer <token>`    |
| ocp-apim-subscription-key | { Chave de Acesso } |
| username                  | { Username }        |

**Response**

{% tabs %}
{% tab title="200" %}
```json
[
    {
        "label": "Não desejo informar",
        "value": "00000",
        "order": "AA"
    },
    {
        "label": "Advogado",
        "value": "00001",
        "order": "AB"
    },
    ....
]
```
{% endtab %}
{% endtabs %}



## Buscar Corretoras

<mark style="color:green;">`GET`</mark>  {**URL**}/brokerage/product/{productName}?brokerage={nome da corretora}

**Headers**

| Name                      | Value               |
| ------------------------- | ------------------- |
| Content-Type              | `application/json`  |
| Authorization             | `Bearer <token>`    |
| ocp-apim-subscription-key | { Chave de Acesso } |
| username                  | { Username }        |

**Response**

{% tabs %}
{% tab title="200" %}
```json
[
    {
        "value": "0101422", - Valor a ser enviado 
        "label": "VITACA CORRETORA DE SEGUROS LTDA - ME" - Label
    }
]
```
{% endtab %}
{% endtabs %}

## Buscar métodos de pagamentos

<mark style="color:green;">`GET`</mark>  {**URL**}/payments/{contractId}

**Headers**

| Name                      | Value               |
| ------------------------- | ------------------- |
| Content-Type              | `application/json`  |
| Authorization             | `Bearer <token>`    |
| ocp-apim-subscription-key | { Chave de Acesso } |
| username                  | { Username }        |

**Response**

{% tabs %}
{% tab title="200" %}
```json
[
    {
        "code": "1",
        "description": "Boleto / Carnê",
        "installments": [
            {
                "taxValue": 427.48,
                "code": "34630",
                "number": 1,
                "description": "1x sem juros de R$ 6.219,83 (Total: R$ 6.219,83)",
                "totalValue": 6219.83,
                "firstInstallmentValue": 6219.83,
                "firstInstallmentExpirationDay": 4,
                "otherInstallmentsExpirationDay": 15,
                "firstInstallmentChargeType": "4",
                "otherInstallmentsChargeType": "3"
            },
            .....
        ],
    }
]
```
{% endtab %}
{% endtabs %}
