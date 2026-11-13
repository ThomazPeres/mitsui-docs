# Consultas

Serviços de consulta exclusivos do produto **MS Construção** (`constructionworks`). Os serviços compartilhados entre produtos estão em [Serviços de consulta](../servicos-de-consulta/).

{% hint style="warning" %}
O segmento e o tipo de obra formam um par: o tipo de obra deve vir da consulta filtrada pelo segmento escolhido. O servidor não confere se o par existe, então um tipo de obra de outro segmento só é percebido no cálculo.
{% endhint %}

## Buscar segmentos

<mark style="color:green;">`GET`</mark> {**URL**}/lookups/occupancy-classes?productCode=constructionworks

**Query parameters**

{% code overflow="wrap" %}
```json
productCode = constructionworks (obrigatório; sem ele o retorno é 204)
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
        "label": "Aeroportos",
        "value": "01"
    }
]
```
{% endtab %}

{% tab title="204" %}
Sem conteúdo. `productCode` não informado.
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Envie o `value` escolhido, exatamente como retornado, no campo `occupation` do cálculo.
{% endhint %}

## Buscar tipos de obra

<mark style="color:green;">`GET`</mark> {**URL**}/lookups/classifications?productCode=constructionworks\&occupancy={}

**Query parameters**

{% code overflow="wrap" %}
```json
productCode = constructionworks (obrigatório; sem ele o retorno é 204)
occupancy   = value do segmento obtido em Buscar segmentos
searchText  = Filtro por nome ou código (opcional, mínimo de 3 caracteres)
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
        "label": "Obras e/ou Instalação de elevadores e/ou escadas rolantes - LADO TERRA",
        "value": "001-03",
        "parent": {
            "label": "Aeroportos",
            "value": "01"
        }
    }
]
```
{% endtab %}

{% tab title="204" %}
Sem conteúdo. `productCode` não informado.
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
Sempre envie `occupancy`. Sem ele a lista mistura os tipos de obra de todos os segmentos, e o `parent` de cada item traz apenas um deles.

Envie o `value` escolhido em `classification-id` no cálculo e em `classificationId` na consulta de coberturas.
{% endhint %}

## Buscar coberturas

<mark style="color:green;">`GET`</mark> {**URL**}/coverages/constructionworks?classificationId={}

**Query parameters**

```json
classificationId = value do tipo de obra (obrigatório na prática; sem ele o retorno é 204)
```

{% hint style="info" %}
Os parâmetros `modality`, `planModality`, `categoryId` e `zipcode` são aceitos nesta rota, mas ignorados no MS Construção.
{% endhint %}

**Headers**

| Name          | Value              |
| ------------- | ------------------ |
| Content-Type  | `application/json` |
| Authorization | `Bearer <token>`   |
| username      | { Username }       |

**Response**

Exemplo reduzido, com valores ilustrativos. As coberturas, os limites de LMI e as franquias variam conforme o tipo de obra.

{% tabs %}
{% tab title="200" %}
```json
[
    {
        "group": "Cobertura",
        "coverages": [
            {
                "code": "67001",
                "label": "Básica: Obras Civis em Construção e Instalação e/ou Montagem (OCC/IM)",
                "basic": true,
                "lmiLimit": {
                    "min": 100000.0,
                    "max": 30000000.0
                },
                "deductibles": [
                    {
                        "label": "10% prej. ind. Min R$ 25.000,00",
                        "value": "1-2-99999-99999-0-30000000.00-99999",
                        "lmiLimit": {
                            "min": 0.0,
                            "max": 30000000.0
                        }
                    }
                ],
                "riskProfile": {
                    "questions": [
                        {
                            "code": "02",
                            "label": "Exerce atividade em mineradora?",
                            "type": "select",
                            "answers": [
                                { "code": "1", "label": "Sim" },
                                { "code": "2", "label": "Não" }
                            ]
                        },
                        {
                            "code": "03",
                            "label": "Exerce atividade em subterrâneo?",
                            "type": "select",
                            "answers": [
                                { "code": "1", "label": "Sim" },
                                { "code": "2", "label": "Não" }
                            ],
                            "dependsOn": {
                                "questionCode": "02",
                                "answerCode": "1"
                            }
                        }
                    ]
                },
                "text": "Texto descritivo da cobertura."
            },
            {
                "code": "67074",
                "label": "Manutenção Ampla",
                "lmiLimit": {
                    "min": 10000.0,
                    "max": 30000000.0
                },
                "deductibles": [
                    {
                        "label": "10% prej. ind. Min R$ 25.000,00",
                        "value": "1-2-99999-99999-0-30000000.00-99999",
                        "lmiLimit": {
                            "min": 0.0,
                            "max": 30000000.0
                        }
                    }
                ],
                "text": "Texto descritivo da cobertura."
            }
        ]
    }
]
```
{% endtab %}

{% tab title="204" %}
Sem conteúdo. `classificationId` não informado ou sem coberturas para o tipo de obra.
{% endtab %}
{% endtabs %}

### Lendo o retorno

> **code:** Código da cobertura. Enviar em `coverage-code`.

> **basic:** Presente e `true` apenas na cobertura básica. A `67001` é a única básica e é obrigatória no cálculo.

> **lmiLimit:** Faixa permitida para `coverage-lmi`.

> **deductibles:** Franquias disponíveis. Enviar `value` e `label` em `coverage-deductible`. O `lmiLimit` da franquia é a faixa de LMI em que ela vale: escolha a franquia cuja faixa contém o LMI informado.

> **riskProfile.questions:** Perguntas obrigatórias da cobertura. Respondidas em `coverage-risk-profile` com o `code` da pergunta e o `code` da resposta em `value`.
>
> **dependsOn:** A pergunta só deve ser respondida quando a pergunta `questionCode` tiver a resposta `answerCode`.

### Perguntas de perfil de risco

Todas pertencem à cobertura básica `67001` e valem para qualquer tipo de obra. Respostas: `1` = Sim, `2` = Não.

| Código | Pergunta                                                   | Observação                                       |
| ------ | ---------------------------------------------------------- | ------------------------------------------------ |
| `01`   | Exerce atividades em áreas de Petroquímicas / Refinarias?  | Sim recusa o risco                               |
| `02`   | Exerce atividade em mineradora?                            | Sim habilita a pergunta `03`                     |
| `03`   | Exerce atividade em subterrâneo?                           | Só quando `02` = Sim. Sim recusa o risco         |
| `04`   | Exerce atividade em área offshore?                         | Sim recusa o risco                               |
| `05`   | Exerce atividade em barragens?                             |                                                  |
| `06`   | Exerce atividade em plantas hídricas?                      |                                                  |
| `07`   | Exerce atividade sob/sobre água?                           |                                                  |

{% hint style="info" %}
Campos com valor nulo ou `false` são omitidos do retorno.

Os textos das perguntas vêm do cadastro do produto. Use sempre o retorno de [Buscar coberturas](consultas.md#buscar-coberturas) como fonte.
{% endhint %}
