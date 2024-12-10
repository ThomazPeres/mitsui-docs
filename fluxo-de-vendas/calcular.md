# Calcular

## Calcular

<mark style="color:green;">`POST`</mark> {**URL**}/calculate

**Headers**

| Name                      | Value               |
| ------------------------- | ------------------- |
| ocp-apim-subscription-key | { Chave de acesso } |
| Authorization             | `Bearer <token>`    |
| username                  | { Username }        |

**Body**

[**Aqui**](calcular.md#definindo-campos-de-envio)**, segue uma explicação dos campos**

```postman_json
{
    "ProductCode": "businessproperty",
    "CalculationSettings": {
        "calculation-settings": {
            "vp-contract": {
                "label": "",
                "value": ""
            },
            "commission-percentage": "25.0",
            "discount-percentage": "0.0",
            "increase-percentage": "0.0"
        },
        "co-brokerage": []
    },
    "fields": [
        {
            "CODE": "insured-identity",
            "VALUE": "47196777700"
        },
        {
            "code": "insured-name",
            "value": "John Doe"
        },
        {
            "code": "iof-exempt",
            "value": "false"
        },
        {
            "itemId": "1",
            "code": "item-name",
            "value": "ITEM 1"
        },
        {
            "itemId": "1",
            "code": "item-address-zipcode",
            "value": "90480-200"
        },
        {
            "itemId": "1",
            "code": "item-address-street",
            "value": "Av. Paraná"
        },
        {
            "itemId": "1",
            "code": "item-address-number",
            "value": "1761"
        },
        {
            "itemId": "1",
            "code": "item-address-complement",
            "value": "3º"
        },
        {
            "itemId": "1",
            "code": "item-address-complement-type",
            "label": "Andar",
            "value": "Andar"
        },
        {
            "itemId": "1",
            "code": "item-address-neighborhood",
            "value": "São Geraldo"
        },
        {
            "itemId": "1",
            "code": "item-address-city",
            "value": "São Paulo"
        },
        {
            "itemId": "1",
            "code": "item-address-state",
            "value": "SP"
        },
        {
            "itemId": "1",
            "code": "classification-description",
            "label": "CAFÉ - Cafeteria, permitindo vendas de artigos para fumantes e doces (bombonieri)",
            "value": "103-80"
        },
        {
            "itemId": "1",
            "code": "classification-id",
            "value": "103-80"
        },
        {
            "itemId": "1",
            "code": "occupation",
            "value": "02"
        },
        {
            "itemId": "1",
            "code": "occupation-description",
            "value": "Indústria"
        },
        {
            "itemId": "1",
            "code": "category-id",
            "label": "Sólida",
            "value": "2"
        },
        {
            "itemId": "1",
            "code": "item-type",
            "label": "LMI Prédio e Conteúdo",
            "value": "3"
        },
        {
            "itemId": "1",
            "code": "lost-profits",
            "value": "R$1000"
        },
        {
            "itemId": "1",
            "code": "risk-value",
            "value": "R$ 1000000.00"
        },
        {
            "itemId": "1",
            "code": "01",
            "label": "Andar Superior",
            "value": "2"
        },
        {
            "itemId": "1",
            "code": "02",
            "label": "Sim",
            "value": "1"
        },
        {
            "itemId": "1",
            "code": "14",
            "label": "Sim",
            "value": "1"
        },
        {
            "itemId": "1",
            "code": "18",
            "label": "Sim",
            "value": "1"
        },
        {
            "itemId": "1",
            "code": "19",
            "label": "Sim",
            "value": "1"
        },
        {
            "itemId": "1",
            "code": "20",
            "label": "Sim",
            "value": "1"
        },
        {
            "itemId": "1",
            "code": "21",
            "label": "Sim",
            "value": "1"
        },
        {
            "itemId": "2",
            "code": "item-name",
            "value": "ITEM 2"
        },
        {
            "itemId": "2",
            "code": "item-address-zipcode",
            "value": "90420-000"
        },
        {
            "itemId": "2",
            "code": "item-address-street",
            "value": "R. Xavier Ferreira"
        },
        {
            "itemId": "2",
            "code": "item-address-number",
            "value": "137"
        },
        {
            "itemId": "2",
            "code": "item-address-complement-type",
            "label": "Andar",
            "value": "Andar"
        },
        {
            "itemId": "2",
            "code": "item-address-neighborhood",
            "value": "Auxiliadora"
        },
        {
            "itemId": "2",
            "code": "item-address-city",
            "value": "Porto Alegre"
        },
        {
            "itemId": "2",
            "code": "item-address-state",
            "value": "RS"
        },
        {
            "itemId": "2",
            "code": "classification-description",
            "label": "ESCRITORIO - Térreo/Sobrado",
            "value": "197-10"
        },
        {
            "itemId": "2",
            "code": "classification-id",
            "value": "197-10"
        },
        {
            "itemId": "2",
            "code": "occupation",
            "value": "03"
        },
        {
            "itemId": "2",
            "code": "occupation-description",
            "value": "Serviços"
        },
        {
            "itemId": "2",
            "code": "category-id",
            "label": "Mista",
            "value": "1"
        },
        {
            "itemId": "2",
            "code": "item-type",
            "label": "LMI Conteúdo",
            "value": "1"
        },
        {
            "itemId": "2",
            "code": "lost-profits",
            "value": "1000"
        },
        {
            "itemId": "2",
            "code": "risk-value",
            "value": "R$ 1000000.00"
        },
        {
            "itemId": "2",
            "code": "01",
            "label": "Andar Superior",
            "value": "2"
        },
        {
            "itemId": "2",
            "code": "02",
            "label": "Sim",
            "value": "1"
        },
        {
            "itemId": "2",
            "code": "14",
            "label": "Sim",
            "value": "1"
        },
        {
            "itemId": "2",
            "code": "18",
            "label": "Sim",
            "value": "1"
        },
        {
            "itemId": "2",
            "code": "19",
            "label": "Sim",
            "value": "1"
        },
        {
            "itemId": "2",
            "code": "20",
            "label": "Sim",
            "value": "1"
        },
        {
            "itemId": "2",
            "code": "21",
            "label": "Sim",
            "value": "1"
        },
    ],
    "coverages": [
        {
            "itemId": "1",
            "coverages": [
                {
                    "coverage-code": "00028",
                    "coverage-lmi": "R$ 1000000.00",
                    "coverage-clause": {
                        "label": "Sem aplicação - Indenização a Valor de Novo",
                        "value": "971"
                    },
                    "coverage-deductible": {
                        "label": "10 % prej. ind. Min 2000",
                        "value": "2-2-99999-99999-5000000.00-9999999.00-01B-10"
                    }
                },
                {
                    "coverage-code": "00030",
                    "coverage-lmi": "R$3000000.00",
                    "coverage-clause": {
                        "label": "Contratada - Indenização a Valor de Novo para a Cobertura Danos Elétricos",
                        "value": "973"
                    },
                    "coverage-deductible": {
                        "label": "10 % prej. ind. Min 2000",
                        "value": "2-2-99999-99999-100000.00-999999999.00-99999"
                    }
                }
            ]
        },
        {
            "itemId": "2",
            "coverages": [
                {
                    "coverage-code": "00028",
                    "coverage-lmi": "R$ 1000000.00",
                    "coverage-clause": {
                        "value": "971"
                    },
                    "coverage-deductible": {
                        "value": "2-2-99999-99999-5000000.00-9999999.00-01B-10"
                    }
                },
                {
                    "coverage-code": "00030",
                    "coverage-lmi": "R$30000000.00",
                    "coverage-clause": {
                        "value": "973"
                    },
                    "coverage-deductible": {
                        "value": "2-2-99999-99999-100000.00-999999999.00-99999"
                    }
                }
            ]
        }
    ]
}
```

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
    "contractId": "EM9539994702",
    "response": {
        "prize": {
            "planId": "1",
            "date": "2024-12-09T15:42:39.3460408Z",
            "items": [
                {
                    "itemId": "1",
                    "calculationId": "300035586",
                    "coverages": [
                        {
                            "id": "00028",
                            "totalValue": 187.84,
                            "netValue": 140.88,
                            "mocked": false
                        },
                        {
                            "id": "00030",
                            "totalValue": 2758.21,
                            "netValue": 2068.66,
                            "mocked": false
                        },
                        {
                            "id": "01217",
                            "isEmptyPrize": true,
                            "totalValue": 0.0,
                            "netValue": 0.00,
                            "mocked": false
                        }
                    ],
                    "totalValue": 3163.47,
                    "netValue": 2946.05,
                    "taxValue": 217.42,
                    "mocked": false,
                    "cached": false,
                    "success": true
                },
                {
                    "itemId": "2",
                    "calculationId": "300035587",
                    "coverages": [
                        {
                            "id": "00028",
                            "totalValue": 94.52,
                            "netValue": 70.89,
                            "mocked": false
                        },
                        {
                            "id": "00030",
                            "totalValue": 2751.78,
                            "netValue": 2063.84,
                            "mocked": false
                        },
                        {
                            "id": "01217",
                            "isEmptyPrize": true,
                            "totalValue": 0.0,
                            "netValue": 0.00,
                            "mocked": false
                        }
                    ],
                    "totalValue": 3056.36,
                    "netValue": 2846.30,
                    "taxValue": 210.06,
                    "mocked": false,
                    "cached": false,
                    "success": true
                }
            ],
            "totalValue": 6219.83,
            "netValue": 5792.35,
            "taxValue": 427.48,
            "mocked": false,
            "success": true
        }
    }
}
```
{% endtab %}

{% tab title="401" %}
```json
{
  "error": "Invalid request"
}
```
{% endtab %}
{% endtabs %}



## Definindo campos de envio



> **Product Code:** Código do produto
>
> \
> **Produtos disponiveis neste endpoint:** [Buscar Produto.](servicos-de-consulta/calculo.md#buscar-produtos)

> **CalculationSettings:** Configurações básicas para cálculo



{% hint style="info" %}
Fields é um array de objetos.



Os objetos podem conter **Code, Value, ItemId** e **Label.**



Sendo **Code** e **Value** sempre obrigátorios.\
\
**Value** sempre será tipo **String**
{% endhint %}



> **insured-identity:** CPF/CNPJ do segurado.

> **insured-name:** Nome do segurado.

> **iof-exempt:** Isenção de IOF.

> **item-name:** Nome do item (pode cotar 1 ou mais itens).

> **item-address-zipcode:** CEP do item.
>
> **itemId:** Item que deseja adicionar a resposta.

> **item-address-street:** Rua do item.
>
> **itemId:** Item que deseja adicionar a resposta.

> **item-address-number:** Número do endereço do item.
>
> **itemId:** Item que deseja adicionar a resposta.

> **item-address-complement:** Complemento do item (**opcional**).
>
> **itemId:** Item que deseja adicionar a resposta.

> **item-address-complement-type:** Tipo de complemento do item (**opcional**).
>
> **itemId:** Item que deseja adicionar a resposta.

> **item-address-neighborhood:** Bairro do item.
>
> **itemId:** Item que deseja adicionar a resposta.

> **item-address-city:** Cidade do item.
>
> **itemId:** Item que deseja adicionar a resposta.

> **item-address-State:** Estado do item.
>
> **itemId:** Item que deseja adicionar a resposta.

> **classification-id:** Código da atividade do item (as atividades podem ser consultadas neste [endpoint](servicos-de-consulta/calculo.md#buscar-atividades)).
>
> **itemId:** Item que deseja adicionar a resposta.

> **classification-description:** Código da atividade do item.
>
> **itemId:** Item que deseja adicionar a resposta.
>
> **label:** Descrição da atividade referenciada (é retornado na mesma consulta de atividades).

> **occupation:** Ocupação da atividade selecionada.
>
> **itemId:** Item que deseja adicionar a resposta.

> **occupation-description:** Descrição da ocupação (é retornado na mesma consulta de atividades).
>
> **itemId:** Item que deseja adicionar a resposta.

> **category-id:** Classe de construção do item (pode ser consultado neste [endpoint](servicos-de-consulta/calculo.md#buscar-classe-de-construcao)).
>
> **itemId:** Item que deseja adicionar a resposta.
>
> **label:** Descrição da classe de construção selecionada.

> **item-type:** Tipo do bem do item.
>
> **itemId:** Item que deseja adicionar a resposta.\
> \
> Opções:\
>
>
> ```json
> {
>     "order": 1,
>     "label": "LMI Conteúdo",
>     "value": "1"
> },
> {
>     "order": 2,
>     "label": "LMI Prédio",
>     "value": "2"
> },
> {
>     "order": 3,
>     "label": "LMI Prédio e Conteúdo",
>     "value": "3"
> }
> ```
>
> \
>
>
> **label:** Descrição do tipo do bem selecionado.

> **lost-profits:** Valor de lucros cessantes (**opcional**).
>
> **itemId:** Item que deseja adicionar a resposta.

> **risk-value:** Valor em risco do item.
>
> **itemId:** Item que deseja adicionar a resposta.

### Coverages (Coberturas)

Coberturas selecionadas por item, as coberturas disponiveis para contratação seguem disponiveis nesse endpoint: [Listas Coberturas](servicos-de-consulta/calculo.md#buscar-coberturas)

**Coverages:** Array de objetos para adicionar coberturas aos itens.

O que enviar no objeto de coverages:

{% code overflow="wrap" %}
```json
{
    "itemId": Id do item para adicionar as coberturas,
    "coverages": [
        {
            "coverage-code": Código da cobertura,
            "coverage-lmi": Valor da cobertura,
            "coverage-clause": {
                "label": Descrição da cláusula selecionada,
                "value": Código da cláusula selecionada
            },
            "coverage-deductible": {
                "label": Descrição da franquia selecionada,
                "value": Código da franquia selecionada
            }
        }
    ]
},
```
{% endcode %}



{% hint style="warning" %}
**As perguntas com códigos númericos, dependem da atividade selecionada anteriormente sendo necessário uma consulta neste endpoint:**[ **Perfil de Risco**](servicos-de-consulta/calculo.md#buscar-perfil-de-risco)**.**\
\
**Elas sempre devem ser respondidas no modelo:**\


```json
{
    "itemId": Item que deseja adicionar a resposta,
    "code": Código que vem do endpoint,
    "label": Descrição do que vem do endpoint,
    "value": Resposta selecionada do endpoint
},
```
{% endhint %}
