---
description: Seguro de Responsabilidade Civil (RC Geral e Transporte RCG)
---

# Responsabilidade Civil

| Característica   | Valor                                                                                        |
| ---------------- | -------------------------------------------------------------------------------------------- |
| `ProductCode`    | `civilliability`                                                                             |
| Id do produto    | `51006`                                                                                      |
| Segurado         | Somente Pessoa Jurídica (CNPJ)                                                               |
| Itens            | Item único (`itemId: "1"`), criado automaticamente. Sem endereço, sem classe de construção. |
| Modalidades      | `1` = RC Geral, `2` = Transporte RCG (campo `modality`)                                      |
| Plano            | `00005` = Responsabilidade Civil Geral (campo `plan-modality`, único valor)                  |
| Tipos de cotação | Seguro novo e renovação congênere. **Renovação Mitsui não é suportada.**                     |

## Ordem de chamadas

1. [Buscar produtos](../servicos-de-consulta/calculo.md#buscar-produtos): obtém `modality` e `planModality` disponíveis.
2. [Buscar atividades](consultas.md#buscar-atividades): atividades da modalidade escolhida.
3. [Buscar coberturas](consultas.md#buscar-coberturas): coberturas, franquias e perguntas de perfil de risco de cada cobertura.
4. [Calcular](calcular.md): salva e calcula o contrato.
5. [Buscar métodos de pagamento](../servicos-de-consulta/proposta.md#buscar-metodos-de-pagamentos).
6. [Proposta](proposta.md): dados do segurado e pagamento.
7. [Transmissão](../transmissao.md).

{% hint style="warning" %}
A modalidade (`modality`) é definida no primeiro cálculo e **não pode ser alterada** depois. Para trocar de RC Geral para Transporte RCG (ou vice-versa), inicie um novo contrato.
{% endhint %}

{% hint style="info" %}
O produto **RC Obras** não está disponível nesta API.
{% endhint %}
