# Consultas

## Buscar contrato

<mark style="color:green;">`GET`</mark> {**URL**}/contract/{contractId}

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
Retorna todo o contrato.
```
{% endtab %}
{% endtabs %}



## Listar contratos

<mark style="color:green;">`GET`</mark> {**URL**}/contracts?page={}\&size={}

**Query parameters**

{% code overflow="wrap" %}
```json
page = Pagina.

size = Número de contratos por página
```
{% endcode %}

**Body**

```json
{
    "status": [], 
    "product": "18001", // Código do Produto
    "searchText": "" // Pesquisar por nome, CPF/CNPJ, número do contrato
}
```

{% hint style="info" %}
```json
Status disponiveis para consulta 


Draft = Iniciada,
Quoted = Cotada,
Proposal = Proposta iniciada,
PendingTransmission = Proposta gerada,
Transmitted = Proposta transmitida,
Denied = Proposta recusada,
Emitted = Apólice emitida,
Canceled = Apólice cancelada,
Expired = Cotação expirada,
ToRenew = A Renovar,
```
{% endhint %}

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
"data": [
{
    "step": "Transmissão",
    "status": {
        "label": "Proposta gerada",
        "code": "PendingTransmission"
    },
    "insuredName": "John Doe",
    "insuredId": "04642129000154",
    "productName": "18001-MS Empresa - Massificados",
    "id": "18001",
    "productPath": "businessproperty",
    "contractId": "EM9825079064",
    "totalValue": 2965.13,
    "quotationValidity": "2025-01-02T02:59:59Z",
    "updatedAt": "2024-12-02T11:31:54.418762Z",
    "brokerageName": "CORRETORA DE SEGUROS LTDA"
},
{
    "step": "Transmissão",
    "status": {
        "label": "Proposta gerada",
        "code": "PendingTransmission"
    },
    "insuredName": "John Doe",
    "insuredId": "84535244000169",
    "productName": "18001-MS Empresa - Massificados",
    "id": "18001",
    "productPath": "businessproperty",
    "contractId": "EM2465657678",
    "totalValue": 3384.17,
    "quotationValidity": "2024-12-30T02:59:59Z",
    "updatedAt": "2024-11-29T12:55:33.4226983Z",
    "brokerageName": "CORRETORA DE SEGUROS LTDA"
},
```
{% endtab %}
{% endtabs %}
