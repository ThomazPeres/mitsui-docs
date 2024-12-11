# Cancelar proposta

## Cancelar Proposta&#x20;

Pode ser realizado após a transmissão e&#x20;

<mark style="color:yellow;">`POST`</mark>  {**URL**}/contract/{contractId}/proposal/{proposalId}/cancel

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