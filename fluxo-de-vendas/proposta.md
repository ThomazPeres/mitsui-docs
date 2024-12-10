# Proposta

## Gerar proposta

<mark style="color:green;">`POST`</mark> {**URL**}/calculate

**Headers**

| Name          | Value              |
| ------------- | ------------------ |
| Content-Type  | `application/json` |
| Authorization | `Bearer <token>`   |
| username      | { Username }       |

**Body**

**Aqui, segue uma explicação dos campos.**

{% hint style="warning" %}
**Para proposta, o envio para&#x20;**_<mark style="color:yellow;">**Pessoa Física**</mark>**&#x20;e&#x20;**<mark style="color:yellow;">**Pessoa Jurídica**</mark>_ **são diferentes.**

Abaixo segue apenas um exemplo reduzido da estrutura de envio, e _**Aqui**_ as diferenças e as possiveis respostas.\
\
Na proposta também é enviado os dados do pagamento e na transmissão realizado o pagamento de fato.
{% endhint %}

```postman_json
{
    "contractId": "{{contractId}}",
    "proposalSurvey": [
        {
            "code": "insured-cnae",
            "value": "0111201"
        },
        {
            "code": "insured-cellphone",
            "value": "+5511999999999"
        },'
        {
            "policyId": "1",
            "itemId": "1",
            "code": "tied-policy-company",
            "value": "PORTO SEGURO CIA DE SEGUROS GERAIS"
        },
        {
            "policyId": "1",
            "itemId": "1",
            "code": "tied-policy-number",
            "value": "2344"
        },
        {
            "policyId": "1",
            "itemId": "1",
            "code": "tied-policy-value",
            "value": "1.000,00"
        },
        {
            "policyId": "1",
            "itemId": "1",
            "code": "tied-policy-start-date",
            "value": "2020-08-23T00:00:00-05:00"
        },
        {
            "policyId": "1",
            "itemId": "1",
            "code": "tied-policy-end-date",
            "value": "2021-08-23T00:00:00-05:00"
        },
        {
            "beneficiaryId": "1",
            "code": "beneficiary-name",
            "itemId": "1",
            "value": "Teste beneficiario"
        },
        {
            "beneficiaryId": "1",
            "code": "beneficiary-identity",
            "itemId": "1",
            "value": "63576603379"
        },
        {
            "beneficiaryId": "1",
            "code": "beneficiary-value",
            "itemId": "1",
            "value": "1.000,00"
        },
        {
            "beneficiaryId": "1",
            "code": "beneficiary-description",
            "itemId": "1",
            "value": "Teste descrição item 1"
        },
        {
            "code": "inspection-contact-name",
            "itemId": "1",
            "value": "Teste inspeção nCalculation"
        },
        {
            "code": "inspection-contact-cellphone",
            "itemId": "1",
            "value": "(11)111111111"
        },
        {
            "code": "inspection-contact-cellphone2",
            "itemId": "1",
            "value": "(11)111111111"
        },
        {
            "code": "inspection-contact-name",
            "itemId": "2",
            "value": "Teste inspeção nCalculation"
        },
        {
            "code": "inspection-contact-cellphone",
            "itemId": "2",
            "value": "(11)111111111"
        },
        {
            "code": "inspection-contact-cellphone2",
            "itemId": "2",
            "value": "(11)111111111"
        }
    ],
    "CoBrokerageDistribution": [
        {
            "brokerageId": "0101876",
            "brokerageName": "FIHJVFMUMA ANFGUKGKU A YCAG UW MZCP KHSQ",
            "percentage": 99,
            "writeToLetter": true
        },
        {
            "brokerageId": "0103804",
            "brokerageName": "N UEEKXWV ZMQFTJFJT YA QDUJHFK MN IRCO",
            "percentage": 1,
            "writeToLetter": true
        }
    ],
    "PaymentSurvey": [
        {
            "code": "payment-method-id",
            "value": "9"
        },
        {
            "code": "payment-installment-code",
            "value": "36685"
        },
        // {
        //     "code": "payment-day",
        //     "value": "5"
        // }
        {
            "code": "payment-card-holder-name",
            "value": "TESTE TESTE"
        },
        {
            "code": "payment-card-brand",
            "value": "Master"
        },
        {
            "code": "payment-card-number",
            "value": "5394122280295960"
        },
        {
            "code": "payment-card-expiration-date",
            "value": "02/2028"
        }
    ]
}
```

**Response**

{% tabs %}
{% tab title="200" %}
```json
Retorna todo o contrato e o método de pagamento utilizado.
```
{% endtab %}
{% endtabs %}

## Definindo campos de envio e opções.

> **insured-cnae:** Código de cnae selecionado. Pode ser consultado neste [endpoint](servicos-de-consulta/proposta.md#buscar-atividades-e-cnae).
>
> <mark style="color:yellow;">**Pessoa Juridica.**</mark>

> **insured-cellphone:** Celular do segurado.
>
> **Pessoa Jurídica e Física.**

> **insured-email:** Email do segurado.
>
> **Pessoa Jurídica e Física.**

> **insured-address-zipcode:** CEP do segurado.
>
> **Pessoa Jurídica e Física.**

> **insured-address-street:** Rua do segurado.
>
> **Pessoa Jurídica e Física.**

> **insured-address-number:** Número do endereço do segurado.
>
> **Pessoa Jurídica e Física.**

> **insured-address-complement:** Complemento do segurado (**opcional**).
>
> **Pessoa Jurídica e Física.**

> **insured-address-complement-type:** Tipo de complemento do segurado (**opcional**).
>
> **Pessoa Jurídica e Física.**

> **insured-address-neighborhood:** Bairro do segurado.
>
> **Pessoa Jurídica e Física.**

> **insured-address-city:** Cidade do segurado.
>
> **Pessoa Jurídica e Física**.

> **insured-address-State:** Estado do segurado.
>
> **Pessoa Jurídica e Física.**

> **insured-document-type:** Tipo do documento do segurado.
>
>
>
> **Opções:**
>
> ```json
> value: 1 = RG
> value: 2 = CRNM (RNE)
> ```
>
> <mark style="color:yellow;">**Pessoa Física.**</mark>

> **insured-document-number:** Número do documento do segurado.
>
> <mark style="color:yellow;">**Pessoa Física.**</mark>

> **insured-transmitting-organ:** Orgão transmissor do documento.
>
> <mark style="color:yellow;">**Pessoa Física.**</mark>

> **insured-emission-data:** Data de transmissão do documento.
>
> <mark style="color:yellow;">**Pessoa Física.**</mark>

> **insured-data-birth:** Data de nascimento do segurado.
>
> <mark style="color:yellow;">**Pessoa Física.**</mark>

> **insured-pep:** Segurado é pessoa exposta politicamento.
>
> <mark style="color:yellow;">**Pessoa Física.**</mark>

> **insured-salary-range:** Faixa salarial do segurado. As respostas disponivesi podem ser consultadas neste [endpoint](servicos-de-consulta/proposta.md#buscar-salarios).
>
> <mark style="color:yellow;">**Pessoa Física.**</mark>

> **insured-profession:** Profissão do segurado. As respostas disponivesi podem ser consultadas neste [endpoint](servicos-de-consulta/proposta.md#buscar-profissoes).
>
> <mark style="color:yellow;">**Pessoa Física.**</mark>

> **beneficiary-name:** Nome do beneficiário. Pode haver mais de 1 beneficiário.
>
> **itemId:** Item que deseja adicionar o beneficiário.
>
> **beneficiaryId:** Id do beneficiário.
>
> **Pessoa Jurídica e Física.**

> **beneficiary-identity:** CPF/CNPJ do beneficiário.
>
> **itemId:** Item que deseja adicionar o beneficiário.
>
> **beneficiaryId:** Id do beneficiário.
>
> **Pessoa Jurídica e Física.**

> **beneficiary-value:** Valor do beneficiário.
>
> **itemId:** Item que deseja adicionar o beneficiário.
>
> **beneficiaryId:** Id do beneficiário.
>
> **Pessoa Jurídica e Física.**

> **beneficiary-identity:** Descrição do bem. Máximo de **1024** caracteres.
>
> **itemId:** Item que deseja adicionar o beneficiário.
>
> **beneficiaryId:** Id do beneficiário.
>
> **Pessoa Jurídica e Física.**

> **tied-policy-company:** Seguradora da apólice. As corretoras podem ser pesquisadas no [**endpoint**](servicos-de-consulta/proposta.md#buscar-corretoras)
>
> **itemId:** Item que deseja adicionar outras apólices relacionadas.
>
> **tiedPolicyId:** Id de outras apólices.
>
> **Pessoa Jurídica e Física.**

> **tied-policy-number:** Número da apólices.
>
> **itemId:** Item que deseja adicionar outras apólices relacionadas.
>
> **tiedPolicyId:** Id de outras apólices.
>
> **Pessoa Jurídica e Física.**

> **tied-policy-value:** Valor da apólice.
>
> **itemId:** Item que deseja adicionar outras apólices.
>
> **tiedPolicyId:** Id de outras apólices.
>
> **Pessoa Jurídica e Física.**

> **tied-policy-start-date:** Data de início da vigência.
>
> **itemId:** Item que deseja adicionar outras apólices relacionadas.
>
> **tiedPolicyId:** Id de outras apólices.
>
> **Pessoa Jurídica e Física.**

> **tied-policy-end-date:** Data de fim da vigência.
>
> **itemId:** Item que deseja adicionar outras apólices relacionadas.
>
> **tiedPolicyId:** Id de outras apólices.
>
> **Pessoa Jurídica e Física.**

{% hint style="warning" %}
Abaixo vamos ter as perguntas de inspeção onde é necessário em casos específicos onde pode necessitar de uma avaliação do valor do seguro.\
\
Todas perguntas de inspeção são obrigatórias, exceto para o número de telefone 2, caso o item necessite de inspeção.
{% endhint %}

> **inspection-contact-name:** Nome do contato da inspeção.
>
> **itemId:** Item que deseja precisa de inspeção.
>
> **Pessoa Jurídica e Física.**

> **inspection-contact-cellphone:** Número de contato do inspetor.
>
> **itemId:** Item que deseja precisa de inspeção.
>
> **Pessoa Jurídica e Física.**

> **inspection-contact-cellphone2:** Número de contato do inspetor. (**Opcional)**
>
> **itemId:** Item que deseja precisa de inspeção.
>
> **Pessoa Jurídica e Física.**



### Métodos de pagamento

> **payment-method-id:** Identificador do método de pagamento selecionado.

> **payment-installment-code:** Identificador da parcela selecionada.

> **:** Nome no cartão de crédito.
>
> <mark style="color:yellow;">Para Boleto + débito.</mark>

> **payment-card-holder-name:** Nome no cartão de crédito.
>
> <mark style="color:yellow;">Para cartão de crédito.</mark>

> **payment-card-brand:** Bandeira do cartão.
>
> \
> Opções de bandeiras:
>
> ```
>   {
>     "label": "Diners",
>     "value": "diners",
>     "order": 1
>   },
>   {
>     "label": "Elo",
>     "value": "elo",
>     "order": 2
>   },
>   {
>     "label": "Master",
>     "value": "master",
>     "order": 3
>   },
>   {
>     "label": "Visa",
>     "value": "visa",
>     "order": 4
>   }
> ```
>
> <mark style="color:yellow;">Para cartão de crédito.</mark>

> **payment-card-number:** Número do cartão de crédito.
>
> <mark style="color:yellow;">Para cartão de crédito.</mark>

> **payment-card-expiration-date:** Data de expiração do cartão.
>
> Formato: MM/AAAA
>
> <mark style="color:yellow;">Para cartão de crédito.</mark>

### Co-corretagem (opcional)

{% hint style="info" %}
As corretoras podem ser buscadas neste endpoint: [**Buscar corretora**](servicos-de-consulta/proposta.md#buscar-corretoras)
{% endhint %}

> **brokerageId:** Identificador da corretora selecionada.

> **brokerageName:**  Nome da corretora selecionada.

> **percentage:** Porcentagem da co-corretagem.
