# Cálculo

## Buscar produtos

<mark style="color:green;">`GET`</mark>  {**URL**}/products

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
        "id": "18001",
        "name": "18001-MS Empresa - Massificados",
        "code": "businessproperty"
    }
]
```
{% endtab %}

{% tab title="401" %}
```json
"Provided token is unvalid."
```
{% endtab %}
{% endtabs %}



## Buscar atividades

<mark style="color:green;">`GET`</mark> {**URL**}/lookups/classifications?productCode={}\&searchText={}

**Query parameters**

{% code overflow="wrap" %}
```json
ProductCode = Código do produto
SearchText  = Atividade a ser pesquisada (pode ser pesquisada por código ou nome da atividade)
```
{% endcode %}

**Headers**

| Name          | Value              |
| ------------- | ------------------ |
| Content-Type  | `application/json` |
| Authorization | `Bearer <token>`   |
| username      | { Username }       |

**Response**

{% tabs %}
{% tab title="200" %}
```json
[
    {
        "label": "BUFFET/SALÕES DE FESTAS",
        "value": "061-00A",
        "parent": {
            "label": "Comércio",
            "value": "01"
        }
    },
    {
        "label": "RESTAURANTE / BAR",
        "value": "061-00",
        "parent": {
            "label": "Comércio",
            "value": "01"
        }
    }
]
```
{% endtab %}

{% tab title="400" %}
```json
{
  "error": "Invalid request"
}
```
{% endtab %}
{% endtabs %}



## Buscar classe de construção

<mark style="color:green;">`GET`</mark> {**URL**}/lookups/categories?productCode={}

**Query parameters**

{% code overflow="wrap" %}
```json
ProductCode = Código do produto
```
{% endcode %}

**Headers**

| Name          | Value              |
| ------------- | ------------------ |
| Content-Type  | `application/json` |
| Authorization | `Bearer <token>`   |
| username      | { Username }       |

**Response**

{% tabs %}
{% tab title="200" %}
```json
[
    {
        "label": "SUPERIOR",
        "value": "1"
    },
    {
        "label": "SÓLIDA",
        "value": "2"
    }
]
```
{% endtab %}

{% tab title="400" %}
```json
{
  "error": "Invalid request"
}
```
{% endtab %}
{% endtabs %}



## Buscar coberturas

<mark style="color:green;">`GET`</mark> {**URL**}/coverages/{productCode}?classificationId={}\&CategoryId={}\&zipcode={}

**Query parameters**

```json
ClassificationId = Código de atividade selecionado
CategoryId       = Classe de construção selecionada
Zipcode          = CEP selecionado
```

**Headers**

| Name          | Value              |
| ------------- | ------------------ |
| Content-Type  | `application/json` |
| Authorization | `Bearer <token>`   |
| username      | { Username }       |

**Response**

{% tabs %}
{% tab title="200" %}
```json
[
    {
        "group": "Cobertura",
        "coverages": [
            {
                "code": "00028",
                "label": "Incêndio (Inclusive em Decorrência de Tumultos, Greves e Lockout), Queda de Raio, Explosão de Qualquer Natureza e Queda de Aeronaves",
                "basic": true,
                "lmiLimit": {
                    "min": 1000.0,
                    "max": 20000000.0
                },
                "fields": [
                    {
                        "code": "coverage-lmi",
                        "label": "LMI",
                        "placeholder": "Defina um limite",
                        "type": "input",
                        "item": true,
                        "order": 1,
                        "configuration": {
                            "validationRules": [
                                {
                                    "type": "required",
                                    "errorMessage": "O campo é obrigatório."
                                }
                            ]
                        }
                    },
                    {
                        "code": "coverage-clause",
                        "label": "Cláusula",
                        "placeholder": "Escolha uma opção",
                        "type": "select",
                        "item": true,
                        "order": 2,
                        "configuration": {
                            "options": [
                                {
                                    "label": "Contratada - Indenização a Valor de Novo para a Cobertura Básica",
                                    "value": "972"
                                },
                                {
                                    "label": "Sem aplicação - Indenização a Valor de Novo",
                                    "value": "971"
                                }
                            ]
                        }
                    },
                    {
                        "code": "coverage-deductible",
                        "label": "Franquia",
                        "placeholder": "Escolha uma opção",
                        "type": "select",
                        "item": true,
                        "order": 3,
                        "configuration": {
                            "options": [
                                {
                                    "label": "10% prej. ind. Min R$ 1.000,00 Aplicável exclusivamente para queda de raio.",
                                    "value": "1-2-99999-99999-0-999999999.00-99999",
                                    "limit": {
                                        "field": "coverage-lmi",
                                        "max": 999999999.0
                                    }
                                },
                                {
                                    "label": "10% prej. ind. Min R$ 2.000,00 Aplicável para todos os eventos.",
                                    "value": "14-2-99999-99999-0-999999999.00-99999",
                                    "limit": {
                                        "field": "coverage-lmi",
                                        "max": 999999999.0
                                    }
                                }
                            ]
                        }
                    }
                ],
                "relatedCoverages": {
                    "dependencyOr": [
                        "00953",
                        "01217"
                    ]
                }
            },
        ]
    }
]           

```
{% endtab %}

{% tab title="400" %}
```json
{
  "error": "Invalid request"
}
```
{% endtab %}
{% endtabs %}





## Buscar perfil de risco

<mark style="color:green;">`GET`</mark> {**URL**}/profile/contract/{contractId}/item/{itemId}

**Headers**

| Name          | Value              |
| ------------- | ------------------ |
| Content-Type  | `application/json` |
| Authorization | `Bearer <token>`   |
| Username      | { Username }       |

**Response**

{% tabs %}
{% tab title="200" %}
```json
[
    {
        "group": "Perfil de risco",
        "fields": [
            {
                "code": "19",
                "label": "Hidrantes?",
                "placeholder": "Escolha uma opção",
                "type": "select",
                "item": true,
                "order": 1,
                "configuration": {
                    "validationRules": [
                        {
                            "type": "required",
                            "errorMessage": "O campo é obrigatório."
                        }
                    ],
                    "options": [
                        {
                            "order": 1,
                            "label": "Sim",
                            "value": "1"
                        },
                        {
                            "order": 2,
                            "label": "Não",
                            "value": "2"
                        }
                    ]
                },
                "integration": {
                    "clauses": [
                        "187"
                    ],
                    "skipTransmission": true
                }
            },
            ....
        ]
    }
]
....
```
{% endtab %}

{% tab title="204" %}
```json
{
    "Message" : "Contrato ou item não encontrado, contrato: {contractId}"
}
```
{% endtab %}

{% tab title="204" %}
```json
{
    "Message" : "Item não encontrado, contrato: {contractId} item: {itemId}"
}
```
{% endtab %}

{% tab title="400" %}
```json
{
    "Message" : "Classe de construção não informada"
}
```
{% endtab %}
{% endtabs %}



