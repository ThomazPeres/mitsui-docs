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
        "code": "businessproperty",
        "modality": null,
        "planModality": null
    },
    {
        "id": "51006",
        "name": "51006-Responsabilidade Civil",
        "code": "civilliability",
        "modality": [
            {
                "label": "RCGeral",
                "value": "1"
            },
            {
                "label": "TranspRCG",
                "value": "2"
            }
        ],
        "planModality": [
            {
                "label": "Residencial",
                "value": "00005"
            }
        ]
    },
    {
        "id": "51007",
        "name": "51007-RC Obras",
        "code": "workscivilliability",
        "modality": [
            {
                "label": "Apólice aberta",
                "value": "3"
            },
            {
                "label": "Apólice fechada",
                "value": "4"
            }
        ],
        "planModality": [
            {
                "label": "Responsabilidade Civil Geral",
                "value": "00005"
            }
        ]
    },
    {
        "id": "67006",
        "name": "67006-MS Construção",
        "code": "constructionworks",
        "modality": null,
        "planModality": null
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

{% hint style="info" %}
Retorna apenas os produtos habilitados para a corretora autenticada.

**modality** e **planModality** são preenchidos somente para **Responsabilidade Civil** e **RC Obras**. Use o `value` de `modality` nas consultas de atividades e coberturas e no campo `modality` do cálculo de cada produto: [Responsabilidade Civil](../responsabilidade-civil/calcular.md) | [RC Obras](../rc-obras/calcular.md).

No **Empresarial** e no **MS Construção** os dois vêm `null`: no MS Construção a modalidade e o plano são únicos e o contrato já é criado com eles.

Os `label` e o `name` vêm do cadastro do produto e podem variar. Use sempre o `value` e o `code`.
{% endhint %}

## Buscar seguradoras

<mark style="color:green;">`GET`</mark>  {**URL**}/insurance/?insurance={}

**Query parameters**

{% code overflow="wrap" %}
```json
insurance = nome da seguradora.

Minímo de 3 caracteres.
```
{% endcode %}

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
        "label": "Seguradora 1",
        "value": "1111"
    }
]
```
{% endtab %}
{% endtabs %}
