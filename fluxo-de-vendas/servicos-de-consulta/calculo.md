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

