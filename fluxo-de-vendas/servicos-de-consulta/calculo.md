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
                "label": "Responsabilidade Civil Geral",
                "value": "00005"
            }
        ]
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

**modality** e **planModality** são preenchidos somente para **Responsabilidade Civil**. Use o `value` de `modality` nas consultas de [atividades](../responsabilidade-civil/consultas.md#buscar-atividades) e [coberturas](../responsabilidade-civil/consultas.md#buscar-coberturas) e no campo `modality` do [cálculo](../responsabilidade-civil/calcular.md).
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
