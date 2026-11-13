# Calcular

Campos do produto **RC Obras** (`workscivilliability`).

{% hint style="info" %}
Endpoint, headers, envelope do body, criação e recálculo do contrato, formato da resposta e erros estão em [Calcular](../calcular.md).
{% endhint %}

## Calcular

<mark style="color:green;">`POST`</mark> {**URL**}/calculate

**Body**

[**Aqui**](calcular.md#definindo-campos-de-envio)**, segue uma explicação dos campos**

{% tabs %}
{% tab title="Apólice Aberta (modality 3)" %}
```postman_json
{
    "ProductCode": "workscivilliability",
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
            "code": "modality",
            "label": "Apólice aberta",
            "value": "3"
        },
        {
            "code": "quotation-type",
            "value": "new"
        },
        {
            "code": "plan-modality",
            "value": "00005"
        },
        {
            "code": "vigency-start-date",
            "value": "2026-12-01T00:00:00-03:00"
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
            "code": "risk-value",
            "value": "1500000.00"
        },
        {
            "code": "occupation",
            "label": "Construção civil",
            "value": "01"
        },
        {
            "code": "classification-id",
            "label": "Edificações",
            "value": "001-01"
        },
        {
            "code": "works-description",
            "value": "Instalações elétricas em edifícios comerciais"
        }
    ],
    "coverages": [
        {
            "itemId": "1",
            "coverages": [
                {
                    "coverage-code": "51024",
                    "coverage-lmi": "R$1.000.000,00",
                    "coverage-deductible": {
                        "label": "10% prej. ind. Min R$ 2.500,00 por evento",
                        "value": "1-2-99999-99999-0-999999999.00-99999"
                    },
                    "coverage-risk-profile": [
                        {
                            "code": "19",
                            "label": "Não",
                            "value": "2"
                        },
                        {
                            "code": "30",
                            "value": "50"
                        },
                        {
                            "code": "31",
                            "value": "50"
                        }
                    ]
                },
                {
                    "coverage-code": "00393",
                    "coverage-lmi": "R$500.000,00",
                    "coverage-deductible": {
                        "label": "10% prej. ind. Min R$ 2.500,00 por evento",
                        "value": "1-2-99999-99999-0-999999999.00-99999"
                    },
                    "coverage-risk-profile": [
                        {
                            "code": "10",
                            "label": "Não",
                            "value": "2"
                        },
                        {
                            "code": "13",
                            "value": "5"
                        }
                    ]
                }
            ]
        }
    ]
}
```
{% endtab %}

{% tab title="Apólice Fechada (modality 4)" %}
```postman_json
{
    "ProductCode": "workscivilliability",
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
            "code": "modality",
            "label": "Apólice fechada",
            "value": "4"
        },
        {
            "code": "quotation-type",
            "value": "new"
        },
        {
            "code": "plan-modality",
            "value": "00005"
        },
        {
            "code": "insured-identity",
            "value": "12345678000199"
        },
        {
            "code": "insured-name",
            "value": "CONSTRUTORA EXEMPLO LTDA"
        },
        {
            "code": "iof-exempt",
            "value": "false"
        },
        {
            "code": "works-start-date",
            "value": "2026-12-01T00:00:00-03:00"
        },
        {
            "code": "works-end-date",
            "value": "2027-05-31T00:00:00-03:00"
        },
        {
            "code": "vigency-start-date",
            "value": "2026-12-01T00:00:00-03:00"
        },
        {
            "code": "risk-value",
            "value": "2000000.00"
        },
        {
            "code": "occupation",
            "label": "Construção civil",
            "value": "01"
        },
        {
            "code": "classification-id",
            "label": "Edificações",
            "value": "001-01"
        },
        {
            "code": "works-description",
            "value": "Construção de galpão industrial"
        },
        {
            "locationId": "1",
            "code": "risk-location-zipcode",
            "value": "90240-601"
        },
        {
            "locationId": "1",
            "code": "risk-location-street",
            "value": "Av. Paraná"
        },
        {
            "locationId": "1",
            "code": "risk-location-number",
            "value": "1761"
        },
        {
            "locationId": "1",
            "code": "risk-location-neighborhood",
            "value": "São Geraldo"
        },
        {
            "locationId": "1",
            "code": "risk-location-city",
            "label": "Porto Alegre",
            "value": "Porto Alegre"
        },
        {
            "locationId": "1",
            "code": "risk-location-state",
            "label": "RS",
            "value": "RS"
        }
    ],
    "coverages": [
        {
            "itemId": "1",
            "coverages": [
                {
                    "coverage-code": "51023",
                    "coverage-lmi": "R$1.000.000,00",
                    "coverage-deductible": {
                        "label": "10% prej. ind. Min R$ 2.500,00 por evento",
                        "value": "1-2-99999-99999-0-999999999.00-99999"
                    },
                    "coverage-risk-profile": [
                        {
                            "code": "19",
                            "label": "Não",
                            "value": "2"
                        },
                        {
                            "code": "30",
                            "value": "50"
                        },
                        {
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

{% hint style="info" %}
Segmento, tipo de obra, coberturas adicionais, LMI e franquia dos exemplos são ilustrativos. Use os valores retornados pelas [consultas do produto](consultas.md).
{% endhint %}

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
    "contractId": "RC9539994702",
    "response": {
        "prize": {
            "planId": "1",
            "items": [
                {
                    "itemId": "1",
                    "calculationId": "300041210",
                    "coverages": [
                        {
                            "id": "51024",
                            "totalValue": 1850.40
                        },
                        {
                            "id": "00393",
                            "totalValue": 620.15
                        }
                    ],
                    "totalValue": 2470.55,
                    "netValue": 2300.76,
                    "taxValue": 169.79,
                    "success": true
                }
            ],
            "totalValue": 2470.55,
            "netValue": 2300.76,
            "taxValue": 169.79,
            "success": true
        }
    }
}
```
{% endtab %}

{% tab title="400" %}
```json
{
    "warnings": [],
    "restrictions": [
        {
            "message": "Data de fim da obra deve ser informada.",
            "itemId": "1"
        }
    ]
}
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Retorno completo e catálogo de erros em [Resposta](../calcular.md#resposta) e [Erros](../calcular.md#erros).
{% endhint %}

## Definindo campos de envio.

> **Product Code:** `workscivilliability`.
>
> \
> **Produtos disponiveis neste endpoint:** [Buscar Produto.](../servicos-de-consulta/calculo.md#buscar-produtos)

> **CalculationSettings:** Comissão, desconto e agravo. Ver [CalculationSettings](../calcular.md#calculationsettings).

{% hint style="info" %}
As regras de preenchimento de `fields` (obrigatoriedade, `label`, `itemId`, `clear` e o que acontece ao reenviar o cálculo) estão em [Regras de fields](../calcular.md#regras-de-fields).
{% endhint %}

{% hint style="warning" %}
**A ordem dos campos dentro de `fields` importa:**

* Envie `quotation-type` **antes** dos campos de renovação congênere. Gravar o tipo de cotação limpa a apólice anterior já gravada.
* Envie `occupation` **antes** de `classification-id`. Trocar o segmento limpa o tipo de obra já gravado.
* Em cada local da obra, envie `risk-location-has-no-zipcode` (quando usado) **antes** dos demais campos do local. Mudar essa opção limpa o endereço do local.
{% endhint %}

### Contrato

> **modality:** Modalidade. Valores obtidos em [Buscar produtos](../servicos-de-consulta/calculo.md#buscar-produtos).
>
> \
> Opções:
>
> ```
> {
>   "label": "Apólice aberta",
>   "value": "3"
> },
> {
>   "label": "Apólice fechada",
>   "value": "4"
> }
> ```
>
> ❗**Obrigatório**, sem valor padrão. ❗**Imutável após o primeiro cálculo**: um valor diferente enviado depois é ignorado. Para trocar a modalidade, inicie um novo contrato.

> **quotation-type:** Novo seguro ou renovação congênere.
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
> ❗**Renovação congênere só existe na Apólice Aberta.** Na Apólice Fechada envie sempre `new`.
>
> ❗**Renovação Mitsui (`renewal`) não é suportada no RC Obras.**

> **plan-modality:** Plano. Único valor aceito: `00005`. Opcional, assumido por padrão.

> **vigency-start-date:** Início de vigência, em ISO 8601 (ex.: `2026-12-01T00:00:00-03:00`). Opcional: o padrão é a data de criação do contrato. Precisa estar dentro da janela permitida para a corretora.

> **insured-identity:** CNPJ do segurado, com ou sem máscara. ❗Somente Pessoa Jurídica. Na proposta o CNPJ precisa constar como ativo.

> **insured-name:** Razão social do segurado. Caracteres especiais são removidos: `&` vira `E`, hífen e apóstrofo viram espaço e vírgulas são retiradas.

> **iof-exempt:** Isenção de IOF. Exatamente `"true"` ou `"false"`. Padrão `"false"`.

> **risk-value:** Valor em risco. ❗Obrigatório. Aceita `"1500000.00"` ou `"1.500.000,00"`.
>
> ❗Não use ponto como separador de milhar sem casas decimais: `"150.000"` é lido como 150.

> **occupation:** Segmento (as opções podem ser consultadas neste [endpoint](consultas.md#buscar-segmentos)). ❗Obrigatório.
>
> **label:** Descrição do segmento.

> **classification-id:** Tipo de obra (as opções podem ser consultadas neste [endpoint](consultas.md#buscar-tipos-de-obra), filtrando pelo segmento e pela modalidade). ❗Obrigatório.
>
> **label:** Descrição do tipo de obra.

> **works-description:** Descrição da obra ou da atividade (**opcional**).

> **item-name:** Nome do item (**opcional**). O item `1` é criado automaticamente como "Plano 1".
>
> **itemId:** Sempre `"1"`. O RC Obras possui item único.

***

### Campos da Apólice Fechada

<details>

<summary>Datas da obra</summary>

Enviar somente na Apólice Fechada (`modality` = `4`).

> **works-start-date:** Data de início da obra, em ISO 8601. A data é considerada como escrita, sem conversão de fuso.

> **works-end-date:** Data de fim da obra, em ISO 8601. ❗Obrigatório. Deve ser posterior ao início de vigência. Define o fim da vigência da apólice.

{% hint style="warning" %}
**Regras da Apólice Fechada:**

* A vigência vai do `vigency-start-date` até o `works-end-date`.
* O início de vigência não pode ser anterior ao início da obra.
* Vigência inferior a **5 dias** ou superior a **1.826 dias** gera restrição e não pode ser cotada por esta API.
* O percentual de execução da obra é calculado pelo servidor a partir das datas. Acima de **50%** o risco é recusado.
* O tipo de cálculo é definido pelo servidor a partir do prazo: prazo curto (menos de 1 ano), anual ou plurianual.
{% endhint %}

</details>

***

### Campos adicionais para Renovação congênere.

<details>

<summary>Campos adicionais</summary>

Somente na Apólice Aberta. Estes campos são de **nível de contrato** (não levam `itemId`) e devem vir **depois** de `quotation-type`.

> **insurance-company:** Seguradora da apólice anterior, as seguradoras podem ser pesquisas neste [endpoint](../servicos-de-consulta/calculo.md#buscar-seguradoras). ❗Obrigatório.

> **policy-number:** Número da apólice anterior. ❗Obrigatório.

> **has-claim:** Possui sinistro (❗propriedade texto com true ou false). ❗Obrigatório.

> **claim-percentage:** Sinistralidade em porcentagem (%).\
> ❗Envio obrigátorio caso tenha sinistralidade.

> **experience:** Experiência. (Ambos para sem ou com sinistro). ❗Obrigatório.\
> \
> Opções:
>
> {% code overflow="wrap" fullWidth="false" %}
> ```json
> {
>   "label": "1 ano",
>   "value": "1"
> },
> {
>   "label": "2 anos",
>   "value": "2"
> },
> {
>   "label": "3 anos",
>   "value": "3"
> },
> {
>   "label": "4 anos",
>   "value": "4"
> },
> {
>   "label": "5 anos ou mais",
>   "value": "5"
> }
> ```
> {% endcode %}

</details>

***

### Campos preenchidos pelo servidor

Não envie estes campos. Se enviados, são ignorados.

| Campo                              | Como é preenchido                                                                  |
| ---------------------------------- | ---------------------------------------------------------------------------------- |
| `vigency-end-date`                 | Apólice Aberta: 1 ano após o início de vigência. Apólice Fechada: igual ao `works-end-date` |
| `calculation-type`                 | Apólice Aberta: anual. Apólice Fechada: prazo curto, anual ou plurianual           |
| `works-duration`, `works-progress` | Calculados a partir das datas da obra                                              |
| `insurance-type`                   | Derivado do tipo de cotação e do histórico de sinistro                             |

{% hint style="warning" %}
**Campos de outros produtos que não existem no RC Obras** e são ignorados se enviados: `item-address-*`, `category-id`, `classification-description`, `occupation-description`, `item-type`, `lost-profits`, `coverage-clause`, `beneficiary-*`, `tied-policy-*`, `co-insured-*` e todos os campos de Pessoa Física.
{% endhint %}

### Locais da obra (Apólice Fechada)

Na Apólice Fechada os endereços da obra são enviados em `fields`, com o `locationId` em cada campo. Cada `locationId` diferente cria um local. Envie ao menos um. Na Apólice Aberta esses campos são ignorados.

| Campo                             | Obrigatório                 | Descrição                                                                 |
| --------------------------------- | --------------------------- | ------------------------------------------------------------------------- |
| `risk-location-has-no-zipcode`    | Não                         | `"true"` quando o local não tem CEP. Padrão `"false"`                     |
| `risk-location-zipcode`           | Sim, com CEP                | CEP, com ou sem máscara                                                   |
| `risk-location-street`            | Sim, com CEP                | Logradouro                                                                |
| `risk-location-number`            | Sim, com CEP                | Número                                                                    |
| `risk-location-complement`        | Não                         | Complemento                                                               |
| `risk-location-complement-type`   | Não                         | Tipo de complemento (ex.: Sala, Bloco, Lote)                              |
| `risk-location-neighborhood`      | Sim, com CEP                | Bairro                                                                    |
| `risk-location-city`              | Sim                         | Cidade, por extenso                                                       |
| `risk-location-state`             | Sim                         | UF (ex.: `RS`)                                                            |
| `risk-location-latitude`          | Sim, sem CEP                | Latitude com ponto decimal (ex.: `"-30.0346"`). Precisa estar no Brasil   |
| `risk-location-longitude`         | Sim, sem CEP                | Longitude com ponto decimal (ex.: `"-51.2177"`). Precisa estar no Brasil  |

> **locationId:** Identificador do local, definido por você. Qualquer texto serve. Os locais são numerados na ordem em que foram criados ("Local 1", "Local 2"), e essa numeração aparece nas mensagens de restrição.

> Para remover um local, envie um campo com o `locationId`, sem `code` e com `clear: true`.

{% hint style="warning" %}
Os locais da obra são exigidos ao gerar a proposta: sem local, ou com endereço incompleto, a proposta é recusada. Eles só podem ser enviados no Calcular.
{% endhint %}

### Coverages (Coberturas)

Coberturas selecionadas, as coberturas disponiveis para contratação seguem disponiveis nesse endpoint: [Buscar Coberturas](consultas.md#buscar-coberturas)

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

> **itemId:** Sempre `"1"`.

> **coverage-lmi:** Obrigatório. Deve estar dentro do `lmiLimit` da cobertura. Aceita `"1000000.00"`, `"1.000.000,00"` ou `"R$1.000.000,00"`.

> **coverage-deductible:** ❗Obrigatório em todas as coberturas. O `value` deve ser uma das franquias retornadas para a cobertura, e o LMI deve estar dentro da faixa (`lmiLimit`) da franquia escolhida. Diferente de Responsabilidade Civil, não há franquia padrão.

> **coverage-risk-profile:** Respostas das perguntas de perfil de risco **daquela cobertura**.

{% hint style="warning" %}
**Regras de validação das coberturas:**

* A cobertura básica da modalidade é obrigatória: `51024` na Apólice Aberta e `51023` na Apólice Fechada. As adicionais são opcionais.
* Cobertura de outra modalidade é descartada sem erro.
* O LMI de uma adicional não pode ser maior que o LMI da básica.
* LMI acima de `lmiLimit.max` gera restrição de aceitação automática e não pode ser cotado por esta API.
* **Todas** as perguntas retornadas em `riskProfile.questions` da cobertura devem ser respondidas, exceto as com `dependsOn` não atendido.
* Responder pergunta que **não pertence** à cobertura, ou com `dependsOn` não atendido, gera erro.
* Perguntas `30` (Custo de defesa) e `31` (Indenização): inteiros sem `%`, cada um entre 10 e 90, e a soma deve ser 100.
* Pergunta `32` = `1` (Lado ar) recusa o risco.
{% endhint %}

### Restrições comuns

| Mensagem                                                                                   | Causa                                                    |
| ------------------------------------------------------------------------------------------ | -------------------------------------------------------- |
| `Modalidade não informado.`                                                                | `modality` ausente                                       |
| `Modalidade {código} não disponível para o produto.`                                       | `modality` diferente de `3` e `4`                        |
| `Segmento deve ser informado.`                                                             | `occupation` ausente                                     |
| `Tipo de obra / contrato deve ser informado.`                                              | `classification-id` ausente (Apólice Fechada)            |
| `Tipo de instalação ou obra deve ser informado.`                                           | `classification-id` ausente (Apólice Aberta)             |
| `Valor do risco deve ser informado.`                                                       | `risk-value` ausente                                     |
| `Valor em risco não deve ser superior a {valor}.`                                          | Valor em risco acima do teto da corretora                |
| `Seguradora da apólice anterior deve ser informada.`                                       | Renovação congênere sem `insurance-company`              |
| `Número da apólice anterior deve ser informado.`                                           | Renovação congênere sem `policy-number`                  |
| `Experiência deve ser informada.`                                                          | Renovação congênere sem `experience`                     |
| `Data de fim da obra deve ser informada.`                                                  | Apólice Fechada sem `works-end-date`                     |
| `A data de fim da obra deve ser posterior ao início de vigência.`                          | Fim da obra igual ou anterior ao início de vigência      |
| `O início de vigência não pode ser anterior ao início da obra.`                            | `vigency-start-date` anterior a `works-start-date`       |
| `Vigência inferior a 5 dias, fora do limite de aceitação automática. (...)`                 | Apólice Fechada com vigência menor que 5 dias            |
| `A vigência da apólice fechada deve ter no máximo 1826 dias. (...)`                        | Apólice Fechada com vigência maior que 1.826 dias        |
| `Risco recusado: o percentual de execução da obra está acima de 50%.`                      | Obra com mais de 50% executada no início de vigência     |
| `É necessário contratar a cobertura básica.`                                               | Básica da modalidade ausente                             |
| `LMI da cobertura '{cobertura}' deve estar dentro do limite de: {mínimo} e {máximo}.`     | LMI fora do `lmiLimit`                                   |
| `LMI da cobertura '{cobertura}' acima do limite de aceitação automático de {valor}. (...)` | LMI entre `max` e `matrixMax`                            |
| `O LMI da cobertura '{cobertura}' não pode ser superior ao maior LMI das coberturas básicas ({valor}).` | Adicional com LMI maior que a básica          |
| `Franquia da cobertura '{cobertura}' não está dentro da faixa de LMI permitida de {mínimo} à {máximo}.` | Franquia incompatível com o LMI               |
| `Pergunta {pergunta} não respondida. (...)`                                                | Pergunta de perfil de risco sem resposta                 |
| `Risco recusado. Lado ar fora da política de aceitação.`                                   | Pergunta `32` = Lado ar                                  |
