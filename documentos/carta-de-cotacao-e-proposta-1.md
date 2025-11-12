# Boleto e pix

## PDF do pix

<mark style="color:green;">`GET`</mark> {**URL**}/contract/{contractId}/pix

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
Retorna um base64 para gerar o PDF
{% endtab %}
{% endtabs %}

## PDF de boleto

<mark style="color:green;">`GET`</mark> {**URL**}/contract/{contractId}/ticket

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
Retorna um base64 para gerar o PDF
{% endtab %}
{% endtabs %}
