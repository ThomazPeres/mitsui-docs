---
description: Seguro RC Obras (Responsabilidade Civil de obras, instalações e montagens)
---

# RC Obras

| Característica   | Valor                                                                                                         |
| ---------------- | ------------------------------------------------------------------------------------------------------------- |
| `ProductCode`    | `workscivilliability`                                                                                         |
| Id do produto    | `51007`                                                                                                       |
| Segurado         | Somente Pessoa Jurídica (CNPJ)                                                                                |
| Itens            | Item único (`itemId: "1"`), criado automaticamente. Na Apólice Fechada os endereços vão em **locais da obra** (`locationId`). |
| Modalidades      | `3` = Apólice Aberta, `4` = Apólice Fechada (campo `modality`, obrigatório)                                   |
| Plano            | `00005` (campo `plan-modality`, único valor)                                                                  |
| Tipos de cotação | Seguro novo nas duas modalidades. Renovação congênere **só na Apólice Aberta**. **Renovação Mitsui e endosso não são suportados.** |

## Modalidades

| Modalidade      | `modality` | Uso                                                       | Vigência                                       |
| --------------- | ---------- | --------------------------------------------------------- | ---------------------------------------------- |
| Apólice Aberta  | `3`        | Atividade recorrente de obras ou instalações do segurado  | Anual, a partir do início de vigência          |
| Apólice Fechada | `4`        | Uma obra específica, com datas e locais definidos         | Do início de vigência até o fim da obra        |

## Ordem de chamadas

1. [Buscar produtos](../servicos-de-consulta/calculo.md#buscar-produtos): obtém `modality` e `planModality` disponíveis.
2. [Buscar segmentos](consultas.md#buscar-segmentos): segmento da obra.
3. [Buscar tipos de obra](consultas.md#buscar-tipos-de-obra): tipos de obra do segmento e da modalidade escolhidos.
4. [Buscar coberturas](consultas.md#buscar-coberturas): coberturas, franquias e perguntas de perfil de risco de cada cobertura.
5. [Calcular](calcular.md): salva e calcula o contrato. Na Apólice Fechada, inclui os locais da obra.
6. [Buscar métodos de pagamento](../servicos-de-consulta/proposta.md#buscar-metodos-de-pagamentos).
7. [Proposta](proposta.md): dados do segurado e pagamento.
8. [Transmissão](../transmissao.md).

{% hint style="warning" %}
A modalidade (`modality`) é obrigatória, definida no primeiro cálculo e **não pode ser alterada** depois. Para trocar de Apólice Aberta para Apólice Fechada (ou vice-versa), inicie um novo contrato.
{% endhint %}

{% hint style="warning" %}
Na **Apólice Fechada**, informe ao menos um local da obra no [Calcular](calcular.md#locais-da-obra-apolice-fechada). O cálculo é feito sem ele, mas a proposta e a transmissão são recusadas.
{% endhint %}

{% hint style="info" %}
O perfil de risco vem **dentro de cada cobertura** no retorno de [Buscar coberturas](consultas.md#buscar-coberturas). O endpoint de perfil de risco do Empresarial (`/profile`) não se aplica ao RC Obras.
{% endhint %}
