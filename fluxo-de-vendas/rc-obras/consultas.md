# Consultas

Serviços de consulta exclusivos do produto **RC Obras** (`workscivilliability`). Os serviços compartilhados entre produtos estão em [Serviços de consulta](../servicos-de-consulta/).

{% hint style="warning" %}
O segmento e o tipo de obra formam um par: o tipo de obra deve vir da consulta filtrada pelo segmento escolhido. O servidor não confere se o par existe.
{% endhint %}

## Buscar segmentos

<mark style="color:green;">`GET`</mark> {**URL**}/lookups/occupancy-classes?productCode=workscivilliability

**Query parameters**

{% code overflow="wrap" %}
```json
productCode = workscivilliability (obrigatório; sem ele o retorno é 204)
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
        "label": "Construção civil",
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
A lista de segmentos é a mesma nas duas modalidades. Envie o `value` escolhido, exatamente como retornado, no campo `occupation` do cálculo.
{% endhint %}

## Buscar tipos de obra

<mark style="color:green;">`GET`</mark> {**URL**}/lookups/classifications?productCode=workscivilliability\&occupancy={}\&modality={}

**Query parameters**

{% code overflow="wrap" %}
```json
productCode = workscivilliability (obrigatório; sem ele o retorno é 204)
occupancy   = value do segmento obtido em Buscar segmentos
modality    = Código da modalidade (3 = Apólice Aberta, 4 = Apólice Fechada)
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
        "label": "Edificações",
        "value": "001-01",
        "parent": {
            "label": "Construção civil",
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
A lista muda conforme o segmento e a modalidade: sempre envie `occupancy` e `modality`. Sem `occupancy` a lista mistura os tipos de obra de todos os segmentos.

Envie o `value` escolhido em `classification-id` no cálculo e em `classificationId` na consulta de coberturas.
{% endhint %}

## Buscar coberturas

<mark style="color:green;">`GET`</mark> {**URL**}/coverages/workscivilliability?classificationId={}\&modality={}

**Query parameters**

```json
classificationId = value do tipo de obra (obrigatório)
modality         = Código da modalidade (obrigatório)
planModality     = Código do plano (opcional; padrão 00005)
```

**Headers**

| Name          | Value              |
| ------------- | ------------------ |
| Content-Type  | `application/json` |
| Authorization | `Bearer <token>`   |
| username      | { Username }       |

**Response**

Exemplo reduzido da Apólice Aberta, com valores ilustrativos. As coberturas, os limites de LMI e as franquias vêm do cadastro do produto e mudam por modalidade.

{% tabs %}
{% tab title="200" %}
```json
[
    {
        "group": "Cobertura",
        "coverages": [
            {
                "code": "51024",
                "label": "RC Obras Civis",
                "basic": true,
                "lmiLimit": {
                    "min": 100000.0,
                    "max": 5000000.0,
                    "matrixMax": 15000000.0
                },
                "deductibles": [
                    {
                        "label": "10% prej. ind. Min R$ 2.500,00 por evento",
                        "value": "1-2-99999-99999-0-999999999.00-99999",
                        "lmiLimit": {
                            "min": 0.0,
                            "max": 999999999.0
                        }
                    }
                ],
                "riskProfile": {
                    "questions": [
                        {
                            "code": "19",
                            "label": "Possui conhecimento de sinistro ou reclamação?",
                            "type": "select",
                            "answers": [
                                { "code": "1", "label": "Sim" },
                                { "code": "2", "label": "Não" }
                            ]
                        },
                        {
                            "code": "30",
                            "label": "Custo de defesa (%)",
                            "type": "input",
                            "mask": "percentage",
                            "placeholder": "Informe o valor"
                        },
                        {
                            "code": "31",
                            "label": "Indenização (%)",
                            "type": "input",
                            "mask": "percentage",
                            "placeholder": "Informe o valor"
                        }
                    ]
                },
                "text": "Texto descritivo da cobertura."
            },
            {
                "code": "00393",
                "label": "Prestação de Serviços em Locais de Terceiros",
                "lmiLimit": {
                    "min": 10000.0,
                    "max": 5000000.0
                },
                "deductibles": [
                    {
                        "label": "10% prej. ind. Min R$ 2.500,00 por evento",
                        "value": "1-2-99999-99999-0-999999999.00-99999",
                        "lmiLimit": {
                            "min": 0.0,
                            "max": 999999999.0
                        }
                    }
                ],
                "riskProfile": {
                    "questions": [
                        {
                            "code": "10",
                            "label": "Exerce atividade em aeroportos?",
                            "type": "select",
                            "answers": [
                                { "code": "1", "label": "Sim" },
                                { "code": "2", "label": "Não" }
                            ]
                        },
                        {
                            "code": "32",
                            "label": "Em qual lado do aeroporto?",
                            "type": "select",
                            "answers": [
                                { "code": "1", "label": "Lado ar" },
                                { "code": "2", "label": "Lado terra" }
                            ],
                            "dependsOn": {
                                "questionCode": "10",
                                "answerCode": "1"
                            }
                        },
                        {
                            "code": "13",
                            "label": "Quantidade de funcionários que prestam serviços em locais de terceiros:",
                            "type": "input",
                            "mask": "number",
                            "placeholder": "Informe o valor"
                        }
                    ]
                },
                "text": "Texto descritivo da cobertura."
            }
        ]
    }
]
```
{% endtab %}

{% tab title="204" %}
Sem conteúdo. `classificationId` ou `modality` não informados, ou nenhuma cobertura para os parâmetros.
{% endtab %}
{% endtabs %}

### Lendo o retorno

> **code:** Código da cobertura. Enviar em `coverage-code`.

> **basic:** Presente e `true` apenas na cobertura básica. A básica muda por modalidade: `51024` na Apólice Aberta e `51023` na Apólice Fechada. Ela é obrigatória; as adicionais são opcionais.

> **lmiLimit:** Faixa permitida para `coverage-lmi`.
>
> **matrixMax:** Quando presente, LMI entre `max` e `matrixMax` é aceito no salvamento, mas o cálculo retorna restrição de aceitação automática. Para cotar por esta API, use LMI até `max`.

> **deductibles:** Franquias disponíveis. Enviar `value` e `label` em `coverage-deductible`. O `lmiLimit` da franquia é a faixa de LMI em que ela vale.

> **riskProfile.questions:** Perguntas obrigatórias daquela cobertura. Cada uma deve ser respondida em `coverage-risk-profile` com o `code` da pergunta e, para tipo `select`, o `code` da resposta em `value`.
>
> **dependsOn:** Quando presente, a pergunta só deve ser respondida se a condição for atendida.
>
> **mask:** `number` (inteiro) ou `percentage` (inteiro de 10 a 90, sem o símbolo `%`).

{% hint style="info" %}
Campos com valor nulo ou `false` são omitidos do retorno.
{% endhint %}

### Perguntas de perfil de risco

As perguntas e os textos vêm do cadastro do produto. Use sempre o retorno de [Buscar coberturas](consultas.md#buscar-coberturas) como fonte. As mais comuns:

| Código | Cobertura                           | Pergunta                                                   | Regra                                                   |
| ------ | ----------------------------------- | ---------------------------------------------------------- | ------------------------------------------------------- |
| `19`   | Básica (`51023` / `51024`)          | Possui conhecimento de sinistro ou reclamação?             | `1` = Sim, `2` = Não                                    |
| `30`   | Básica                              | Custo de defesa (%)                                        | Inteiro de 10 a 90. Somado à `31`, deve dar 100         |
| `31`   | Básica                              | Indenização (%)                                            | Inteiro de 10 a 90. Somado à `30`, deve dar 100         |
| `10`   | `00393`                             | Exerce atividade em aeroportos?                            | `1` = Sim habilita a pergunta `32`                      |
| `32`   | `00393`                             | Lado do aeroporto                                          | Só quando `10` = Sim. `1` = Lado ar recusa o risco      |
| `13`   | `00393`                             | Quantidade de funcionários que prestam serviços em locais de terceiros | Inteiro                                   |
| `29`   | `51015`                             | Quantidade de veículos                                     | Inteiro                                                 |

{% hint style="warning" %}
**Não envie** os códigos `15`, `16`, `17`, `26`, `34` a `39`, `43` e `45` (agregados), nem `41`, `42` e `46` a `50` (derivados dos dados da obra). Eles são preenchidos pelo servidor e o que for enviado é descartado.
{% endhint %}
