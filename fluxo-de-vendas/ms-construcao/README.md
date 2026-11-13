---
description: Seguro MS Construção (riscos de engenharia de obras civis e instalação e montagem)
---

# MS Construção

| Característica   | Valor                                                                                                   |
| ---------------- | ------------------------------------------------------------------------------------------------------- |
| `ProductCode`    | `constructionworks`                                                                                     |
| Id do produto    | `67006`                                                                                                 |
| Segurado         | Somente Pessoa Jurídica (CNPJ)                                                                          |
| Itens            | Item único (`itemId: "1"`), criado automaticamente. Os endereços vão em **locais da obra** (`locationId`). |
| Modalidade       | Única (`5`). Gravada pelo servidor, não precisa ser enviada.                                            |
| Plano            | Único (`00005`). Gravado pelo servidor, não precisa ser enviado.                                        |
| Tipos de cotação | Somente seguro novo. **Renovação congênere, renovação Mitsui e endosso não são suportados.**            |
| Prefixo do contrato | `MC` (ex.: `MC9043703374`)                                                                           |

## Ordem de chamadas

1. [Buscar produtos](../servicos-de-consulta/calculo.md#buscar-produtos): confirma que o produto está habilitado para a corretora.
2. [Buscar segmentos](consultas.md#buscar-segmentos): segmento da obra.
3. [Buscar tipos de obra](consultas.md#buscar-tipos-de-obra): tipos de obra do segmento escolhido.
4. [Buscar coberturas](consultas.md#buscar-coberturas): coberturas, franquias e perguntas de perfil de risco do tipo de obra.
5. [Calcular](calcular.md): salva e calcula o contrato, incluindo os locais da obra.
6. [Buscar métodos de pagamento](../servicos-de-consulta/proposta.md#buscar-metodos-de-pagamentos).
7. [Proposta](proposta.md): dados do segurado, beneficiários e pagamento.
8. [Transmissão](../transmissao.md).

{% hint style="warning" %}
Informe **ao menos um local da obra** no [Calcular](calcular.md#locais-da-obra). O cálculo é feito sem ele, mas a proposta e a transmissão são recusadas.
{% endhint %}

{% hint style="info" %}
O perfil de risco vem **dentro da cobertura básica** no retorno de [Buscar coberturas](consultas.md#buscar-coberturas). O endpoint de perfil de risco do Empresarial (`/profile`) não se aplica e retorna lista vazia.
{% endhint %}
