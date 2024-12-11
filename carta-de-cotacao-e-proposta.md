# Carta de cotação e proposta

## Carta de cotação&#x20;

<mark style="color:green;">`GET`</mark>  {**URL**}/contract/{contractId}/quotation-letter

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



## Carta de proposta

<mark style="color:green;">`GET`</mark>  {**URL**}/contract/{contractId}/proposal-letter

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
