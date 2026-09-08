# Calcular

Campos do produto **Responsabilidade Civil** (`civilliability`).

{% hint style="info" %}
Endpoint, headers, envelope do body, criação e recálculo do contrato, formato da resposta e erros estão em [Calcular](../calcular.md).
{% endhint %}

## Calcular

<mark style="color:green;">`POST`</mark> {**URL**}/calculate

**Body**

[**Aqui**](calcular.md#definindo-campos-de-envio)**, segue uma explicação dos campos**

{% tabs %}
{% tab title="RC Geral (modality 1)" %}
```postman_json
{
    "ProductCode": "civilliability",
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
            "code": "quotation-type",
            "value": "new"
        },
        {
            "code": "plan-modality",
            "label": "Responsabilidade Civil Geral",
            "value": "00005"
        },
        {
            "code": "modality",
            "label": "RCGeral",
            "value": "1"
        },
        {
            "code": "insured-identity",
            "value": "12345678000199"
        },
        {
            "code": "insured-name",
            "value": "EMPRESA EXEMPLO LTDA"
        },
        {
            "code": "iof-exempt",
            "value": "false"
        },
        {
            "code": "classification-id",
            "label": "INSTITUIÇÕES FINANCEIRAS",
            "value": "400-00"
        },
        {
            "itemId": "1",
            "code": "item-name",
            "value": "ITEM 1"
        }
    ],
    "coverages": [
        {
            "itemId": "1",
            "coverages": [
                {
                    "coverage-code": "00145",
                    "coverage-lmi": "R$100.000,00",
                    "coverage-deductible": {
                        "label": "10% prej. ind. Min R$ 6.250,00 POS 10% dos prejuízos indenizáveis com mínimo de R$ 2.500,00 por evento",
                        "value": "1-2-99999-99999-0-999999999.00-99999"
                    },
                    "coverage-risk-profile": [
                        {
                            "itemId": "1",
                            "code": "01",
                            "label": "Não",
                            "value": "2"
                        },
                        {
                            "itemId": "1",
                            "code": "02",
                            "label": "Não",
                            "value": "2"
                        },
                        {
                            "itemId": "1",
                            "code": "03",
                            "label": "Não",
                            "value": "2"
                        },
                        {
                            "itemId": "1",
                            "code": "04",
                            "label": "Não",
                            "value": "2"
                        },
                        {
                            "itemId": "1",
                            "code": "05",
                            "label": "Não",
                            "value": "2"
                        },
                        {
                            "itemId": "1",
                            "code": "06",
                            "label": "Não",
                            "value": "2"
                        },
                        {
                            "itemId": "1",
                            "code": "12",
                            "value": "1000000"
                        }
                    ]
                },
                {
                    "coverage-code": "00393",
                    "coverage-lmi": "R$100.000,00",
                    "coverage-deductible": {
                        "label": "10% prej. ind. Min R$ 12.500,00",
                        "value": "1-2-99999-99999-0-999999999.00-400-00"
                    },
                    "coverage-risk-profile": [
                        {
                            "itemId": "1",
                            "code": "07",
                            "label": "Não",
                            "value": "2"
                        },
                        {
                            "itemId": "1",
                            "code": "08",
                            "label": "Não",
                            "value": "2"
                        },
                        {
                            "itemId": "1",
                            "code": "09",
                            "label": "Não",
                            "value": "2"
                        },
                        {
                            "itemId": "1",
                            "code": "10",
                            "label": "Não",
                            "value": "2"
                        },
                        {
                            "itemId": "1",
                            "code": "11",
                            "label": "Não",
                            "value": "2"
                        },
                        {
                            "itemId": "1",
                            "code": "13",
                            "value": "2"
                        }
                    ]
                },
                {
                    "coverage-code": "00071",
                    "coverage-lmi": "R$10.000,00",
                    "coverage-deductible": {
                        "label": "10% prej. ind. Min R$ 6.250,00 POS 10% dos prejuízos indenizáveis com mínimo de R$ 2.500,00 por terceiro reclamante",
                        "value": "1-2-99999-99999-0-999999999.00-400-00"
                    },
                    "coverage-risk-profile": []
                }
            ]
        }
    ]
}
```
{% endtab %}

{% tab title="Transporte RCG (modality 2)" %}
```postman_json
{
    "ProductCode": "civilliability",
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
            "code": "quotation-type",
            "value": "new"
        },
        {
            "code": "plan-modality",
            "label": "Responsabilidade Civil Geral",
            "value": "00005"
        },
        {
            "code": "modality",
            "label": "TranspRCG",
            "value": "2"
        },
        {
            "code": "insured-identity",
            "value": "12345678000199"
        },
        {
            "code": "insured-name",
            "value": "EMPRESA EXEMPLO LTDA"
        },
        {
            "code": "iof-exempt",
            "value": "false"
        },
        {
            "code": "classification-id",
            "label": "TRANSPORTADORAS",
            "value": "900-00"
        },
        {
            "itemId": "1",
            "code": "item-name",
            "value": "ITEM 1"
        }
    ],
    "coverages": [
        {
            "itemId": "1",
            "coverages": [
                {
                    "coverage-code": "51015",
                    "coverage-lmi": "R$ 50.000,00",
                    "coverage-deductible": {
                        "label": "15% prej. ind. Min R$ 10.000,00 por evento fixa. Ver quadro da descrição da Franquia",
                        "value": "1-2-99999-99999-0-999999999.00-900-01"
                    },
                    "coverage-risk-profile": [
                        {
                            "itemId": "1",
                            "code": "29",
                            "value": "2"
                        }
                    ]
                },
                {
                    "coverage-code": "90956",
                    "coverage-lmi": "R$ 5.000.000,00",
                    "coverage-deductible": {
                        "label": "Em excesso à apólice primária DM R$ e DC R$. Se inexist no sinistro, aplica-se como franquia",
                        "value": "2-2-99999-99999-0-999999999.00-900-00"
                    },
                    "coverage-risk-profile": [
                        {
                            "itemId": "1",
                            "code": "19",
                            "label": "Não",
                            "value": "2"
                        },
                        {
                            "itemId": "1",
                            "code": "20",
                            "label": "Não",
                            "value": "2"
                        },
                        {
                            "itemId": "1",
                            "code": "21",
                            "value": "160000.00"
                        },
                        {
                            "itemId": "1",
                            "code": "22",
                            "value": "160000.00"
                        },
                        {
                            "itemId": "1",
                            "code": "23",
                            "value": "1"
                        },
                        {
                            "itemId": "1",
                            "code": "24",
                            "value": "1"
                        },
                        {
                            "itemId": "1",
                            "code": "28",
                            "value": "5"
                        }
                    ]
                },
                {
                    "coverage-code": "00145",
                    "coverage-lmi": "R$ 1.000.000,00",
                    "coverage-deductible": {
                        "label": "10% prej. ind. Min R$ 2.500,00 por evento",
                        "value": "1-2-99999-99999-0-999999999.00-99999"
                    },
                    "coverage-risk-profile": [
                        {
                            "itemId": "1",
                            "code": "12",
                            "value": "R$ 20.000,00"
                        },
                        {
                            "itemId": "1",
                            "code": "19",
                            "label": "Não",
                            "value": "2"
                        },
                        {
                            "itemId": "1",
                            "code": "30",
                            "value": "50"
                        },
                        {
                            "itemId": "1",
                            "code": "31",
                            "value": "50"
                        }
                    ]
                }
            ]
        }
    ]
}
```
{% endtab %}
{% endtabs %}

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
    "contractId": "RC9539994702",
    "response": {
        "prize": {
            "planId": "1",
            "date": "2025-07-21T13:42:39.3460408Z",
            "items": [
                {
                    "itemId": "1",
                    "calculationId": "300041210",
                    "coverages": [
                        {
                            "id": "00145",
                            "totalValue": 1250.40
                        },
                        {
                            "id": "00393",
                            "totalValue": 980.12
                        },
                        {
                            "id": "00071",
                            "totalValue": 210.55
                        }
                    ],
                    "totalValue": 2441.07,
                    "netValue": 2270.76,
                    "taxValue": 170.31,
                    "mocked": false,
                    "cached": false,
                    "success": true
                }
            ],
            "totalValue": 2441.07,
            "netValue": 2270.76,
            "taxValue": 170.31,
            "mocked": false,
            "success": true
        }
    }
}
```
{% endtab %}

{% tab title="400" %}
```json
[
    {
        "code": "3f2a1c9e-7b21-4f0e-9a55-2f8f5a0d1c44",
        "type": "Error",
        "message": "Pergunta não respondida para a cobertura 00145: 12"
    }
]
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Retorno completo e catálogo de erros em [Resposta](../calcular.md#resposta) e [Erros](../calcular.md#erros).
{% endhint %}

## Definindo campos de envio.

> **Product Code:** `civilliability`.
>
> \
> **Produtos disponiveis neste endpoint:** [Buscar Produto.](../servicos-de-consulta/calculo.md#buscar-produtos)

> **CalculationSettings:** Comissão, desconto e agravo. Ver [CalculationSettings](../calcular.md#calculationsettings).

> **quotation-type:** Novo seguro ou renovação congenere.
>
> \
> Opções:
>
> ```
> {
>   "label": "Seguro novo",
>   "value": "new"
> },
> {
>   "label": "Renovação congênere",
>   "value": "congener-renewal"
> }
> ```
>
> ❗**Renovação Mitsui (`renewal`) não é suportada em Responsabilidade Civil.**

> **plan-modality:** Plano. Único valor aceito: `00005` (Responsabilidade Civil Geral). Opcional, assumido por padrão.

> **modality:** Modalidade. Valores obtidos em [Buscar produtos](../servicos-de-consulta/calculo.md#buscar-produtos).
>
> \
> Opções:
>
> ```
> {
>   "label": "RCGeral",
>   "value": "1"
> },
> {
>   "label": "TranspRCG",
>   "value": "2"
> }
> ```
>
> Padrão `1`. ❗**Imutável após o primeiro cálculo**: um valor diferente enviado depois é ignorado. Para trocar a modalidade, inicie um novo contrato.

{% hint style="info" %}
As regras de preenchimento de `fields` (obrigatoriedade, `label`, `itemId`, `clear` e o que acontece ao reenviar o cálculo) estão em [Regras de fields](../calcular.md#regras-de-fields).
{% endhint %}

***

### Campos adicionais para Renovação congênere.

<details>

<summary>Campos adicionais</summary>

Em Responsabilidade Civil estes campos são de **nível de contrato** (não levam `itemId`).

> **insurance-company:** Seguradora da apólice anterior, as seguradoras podem ser pesquisas neste [endpoint](../servicos-de-consulta/calculo.md#buscar-seguradoras).

> **policy-number:** Número da apólice anterior.

> **has-claim:** Possui sinistro (❗propriedade texto com true ou false)

> **claim-percentage:** Sinistralidade em porcentagem (%).\
> ❗Envio obrigátorio caso tenha sinistralidade.

> **experience:** Experiência. (Ambos para sem ou com sinistro).\
> \
> Opções:
>
> {% code overflow="wrap" fullWidth="false" %}
> ```json
> {
>   "label": "1 ano",
>   "order": 1,
>   "value": "1"
> },
> {
>   "label": "2 anos",
>   "order": 2,
>   "value": "2"
> },
> {
>   "label": "3 anos",
>   "order": 3,
>   "value": "3"
> },
> {
>   "label": "4 anos",
>   "order": 4,
>   "value": "4"
> },
> {
>   "label": "5 anos ou mais",
>   "order": 5,
>   "value": "5"
> }
> ```
> {% endcode %}

</details>

***

> **insured-identity:** CNPJ do segurado. ❗Somente Pessoa Jurídica.

> **insured-name:** Razão social do segurado.

> **iof-exempt:** Isenção de IOF.

> **classification-id:** Código da atividade (as atividades podem ser consultadas neste [endpoint](consultas.md#buscar-atividades)). ❗Obrigatório e de **nível de contrato**, sem `itemId`.
>
> **label:** Descrição da atividade referenciada.

> **item-name:** Nome do item (**opcional**). O item `1` é criado automaticamente como "Plano 1".
>
> **itemId:** Sempre `"1"`. Responsabilidade Civil possui item único.

{% hint style="warning" %}
**Campos do Empresarial que não existem em Responsabilidade Civil** e são ignorados se enviados: `item-address-*`, `classification-description`, `occupation`, `occupation-description`, `category-id`, `item-type`, `risk-value`, `lost-profits`, `coverage-clause` e todos os campos de Pessoa Física.
{% endhint %}

### Coverages (Coberturas)

Coberturas selecionadas, as coberturas disponiveis para contratação seguem disponiveis nesse endpoint: [Listar Coberturas](consultas.md#buscar-coberturas)

**Coverages:** Array de objetos para adicionar coberturas ao item.

O que enviar no objeto de coverages:

{% code overflow="wrap" %}
```json
{
    "itemId": "1",
    "coverages": [
        {
            "coverage-code": Código da cobertura,
            "coverage-lmi": Valor da cobertura (dentro de lmiLimit),
            "coverage-deductible": {
                "label": Descrição da franquia selecionada,
                "value": Código da franquia selecionada
            },
            "coverage-risk-profile": [
                {
                    "itemId": "1",
                    "code": Código da pergunta (riskProfile.questions[].code),
                    "label": Descrição da resposta (opcional),
                    "value": Resposta (code da answer, ou valor digitado)
                }
            ]
        }
    ]
},
```
{% endcode %}

> **itemId:** Obrigatório no objeto de coverages. Sem ele a cobertura não é salva.

> **coverage-lmi:** Obrigatório. Deve estar dentro do `lmiLimit` da cobertura.

> **coverage-deductible:** Franquia. Pode ser enviado com `value` vazio; nesse caso a franquia padrão da faixa de LMI é aplicada.

> **coverage-risk-profile:** Respostas das perguntas de perfil de risco **daquela cobertura**. Substitui o endpoint de perfil de risco do Empresarial.

{% hint style="warning" %}
**Regras de validação das coberturas:**

* Mínimo de **2 coberturas**: 1 básica (`basic: true`) e 1 adicional.
* **Todas** as perguntas retornadas em `riskProfile.questions` da cobertura devem ser respondidas, exceto as com `dependsOn` não atendido.
* Responder pergunta que **não pertence** à cobertura gera erro.
* Perguntas `30` (Custo de defesa) e `31` (Indenização): cada uma entre 10 e 90, e a soma deve ser 100.
* **Não envie** os códigos `14`, `15`, `16`, `17`, `18`, `25` e `26` (agregados). Eles são preenchidos pelo servidor.
{% endhint %}
