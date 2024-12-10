---
description: Ambientes e autenticação/autorização
---

# Configurações

{% hint style="warning" %}
A URL de cada recurso vai conter o parametro **\{{url\_ambiente\}}** como prefixo, que deve ser substituido de acordo com o ambiente para o qual serão feitas as requisições.



Exemplo de chamada:

&#x20;`https://apimgtmssdhomolog.azure-api.net/nCalculation/auth`
{% endhint %}

## Ambiente de testes

```markdown
https://apimgtmssdhomolog.azure-api.net/nCalculation
```



## Autenticação e autorização



{% hint style="warning" %}
Para começar a utilizar nossos recursos, você deve possuir uma _<mark style="color:red;">**Chave de Acesso e Username**</mark>_, previamente fornecida.



A API possui um ambiente de testes para realização de testes e um ambiente de produção, cada um com sua respectiva _<mark style="color:red;">**Chave de Acesso e Username**</mark>_.
{% endhint %}

Para obter autorização no consumo dos recursos, você deve enviar a **Chave de Acesso** e o **Username** no Header da requisição toda vez que fizer alguma chamada.

Propriedades no header:

```
ocp-apim-subscription-key: { Chave de Acesso }
username : { Username }
```





<mark style="color:green;">`POST`</mark> {**URL**}/auth

Return bearer token &#x20;

**Headers**

| Name                      | Value               |
| ------------------------- | ------------------- |
| ocp-apim-subscription-key | { Chave de Acesso } |

**Body**

| Name       | Type   | Description       |
| ---------- | ------ | ----------------- |
| username   | string | Código do usuário |
| password   | string | Senha do usuário  |
| clientKey  | string | Chave do cliente  |
| clientCode | string | Código do cliente |

**Response**

{% tabs %}
{% tab title="200" %}
{% code overflow="wrap" fullWidth="false" %}
```json
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
}
```
{% endcode %}
{% endtab %}

{% tab title="401" %}
```json
{
    "error": "213Combinação de Chave e Código do Cliente inválida."
}
```
{% endtab %}
{% endtabs %}



