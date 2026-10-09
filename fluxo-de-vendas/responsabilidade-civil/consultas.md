# Consultas

Serviços de consulta exclusivos do produto **Responsabilidade Civil** (`civilliability`). Os serviços compartilhados entre produtos estão em [Serviços de consulta](../servicos-de-consulta/).

{% hint style="warning" %}
Em Responsabilidade Civil **não existe** consulta de classe de construção nem de perfil de risco por item. As perguntas de perfil de risco vêm **dentro de cada cobertura** no retorno de [Buscar coberturas](consultas.md#buscar-coberturas) e são respondidas em `coverage-risk-profile` no [Calcular](calcular.md#coverages-coberturas).
{% endhint %}

## Buscar atividades

<mark style="color:green;">`GET`</mark> {**URL**}/lookups/classifications?productCode=civilliability\&modality={}

**Query parameters**

{% code overflow="wrap" %}
```json
productCode = civilliability (obrigatório; sem ele o retorno é 204)
modality    = Código da modalidade obtido em Buscar produtos (1 = RC Geral, 2 = Transporte RCG)
```
{% endcode %}

**Headers**

| Name          | Value              |
| ------------- | ------------------ |
| Content-Type  | `application/json` |
| Authorization | `Bearer <token>`   |
| username      | { Username }       |

**Response**

{% tabs %}
{% tab title="200" %}
```json
[
    {
        "label": "INSTITUIÇÕES FINANCEIRAS",
        "value": "400-00"
    },
    {
        "label": "PRESTAÇÃO DE SERVIÇOS",
        "value": "410-00"
    }
]
```
{% endtab %}

{% tab title="204" %}
Sem conteúdo. `productCode` não informado.
{% endtab %}
{% endtabs %}

{% hint style="info" %}
A lista de atividades muda conforme a modalidade. Envie o `value` escolhido em `classification-id` no cálculo.
{% endhint %}

## Buscar coberturas

<mark style="color:green;">`GET`</mark> {**URL**}/coverages/civilliability?classificationId={}\&modality={}

**Query parameters**

```json
classificationId = Código da atividade selecionado (obrigatório)
modality         = Código da modalidade (obrigatório)
```

**Headers**

| Name          | Value              |
| ------------- | ------------------ |
| Content-Type  | `application/json` |
| Authorization | `Bearer <token>`   |
| username      | { Username }       |

**Response**

Exemplo reduzido. Cada cobertura traz suas franquias (`deductibles`) e suas perguntas de perfil de risco (`riskProfile.questions`).

{% tabs %}
{% tab title="200" %}
```json
[
    {
        "group": "Cobertura",
        "coverages": [
            {
                "code": "00145",
                "label": "Estabelecimentos Comerciais e/ou Industriais",
                "basic": true,
                "lmiLimit": {
                    "min": 10000.0,
                    "max": 5000000.0
                },
                "deductibles": [
                    {
                        "code": "1",
                        "label": "10% prej. ind. Min R$ 2.500,00 por evento",
                        "value": "1-2-99999-99999-0-999999999.00-99999",
                        "lmiLimit": {
                            "min": 0.0,
                            "max": 999999999.0
                        },
                        "description": null,
                        "matrix": false
                    }
                ],
                "riskProfile": {
                    "questions": [
                        {
                            "code": "12",
                            "label": "Faturamento bruto anual",
                            "type": "input",
                            "mask": "currency",
                            "placeholder": "R$ 0,00",
                            "answers": null,
                            "defaultValue": null,
                            "dependsOn": null,
                            "tooltip": null,
                            "hintText": null,
                            "limits": null,
                            "readOnly": false
                        },
                        {
                            "code": "19",
                            "label": "Possui sinistro nesta cobertura?",
                            "type": "select",
                            "mask": null,
                            "placeholder": "Escolha uma opção",
                            "answers": [
                                {
                                    "code": "1",
                                    "label": "Sim"
                                },
                                {
                                    "code": "2",
                                    "label": "Não"
                                }
                            ],
                            "defaultValue": null,
                            "dependsOn": null,
                            "tooltip": null,
                            "hintText": null,
                            "limits": null,
                            "readOnly": false
                        }
                    ]
                },
                "text": "Texto descritivo da cobertura.",
                "specialCondition": false
            }
        ],
        "assistGroup": false
    }
]
```
{% endtab %}

{% tab title="400" %}
```json
[
    {
        "message": "Atividade"
    }
]
```

Retornado quando `classificationId` ou `modality` não foram informados.
{% endtab %}
{% endtabs %}

### Lendo o retorno

> **code:** Código da cobertura. Enviar em `coverage-code`.

> **basic:** Cobertura básica. O cálculo exige **no mínimo 2 coberturas**: 1 básica e 1 adicional.

> **lmiLimit:** Faixa permitida para `coverage-lmi`.

> **deductibles:** Franquias disponíveis. Enviar `value` e `label` em `coverage-deductible`.

> **riskProfile.questions:** Perguntas obrigatórias daquela cobertura. Cada uma deve ser respondida em `coverage-risk-profile` com o `code` da pergunta e, para tipo `select`, o `code` da resposta em `value`.
>
> **dependsOn:** Quando presente, a pergunta só precisa ser respondida se a condição for atendida.
>
> **mask:** `currency` (valor monetário), `number` (inteiro) ou `percentage` (10 a 90).

> **specialCondition:** `true` indica cobertura com condição especial (ex.: RC Facultativa de Veículos, `90956`).

{% hint style="info" %}
O parâmetro `planModality` é aceito nesta rota, mas ignorado: para Responsabilidade Civil o plano é sempre `00005`.
{% endhint %}
