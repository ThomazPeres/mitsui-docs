---
description: Realiza o processo de salvamento, cálculo, proposta e transmissão do contrato.
---

# Fluxo de vendas

## Produtos

| Produto                                              | `ProductCode`      | Id      |
| ---------------------------------------------------- | ------------------ | ------- |
| [Empresarial](empresarial/)                          | `businessproperty` | `18001` |
| [Responsabilidade Civil](responsabilidade-civil/)    | `civilliability`   | `51006` |

Cada produto tem suas próprias páginas de **Consultas**, **Calcular** e **Proposta**, pois os campos enviados diferem. Os passos abaixo são comuns.

## Passos

[**Serviços de consulta**](servicos-de-consulta/)**:**

* Serviços compartilhados entre produtos: produtos, seguradoras, corretoras, CNAE, salários, profissões e métodos de pagamento.

**Consultas do produto** ([Empresarial](empresarial/consultas.md) | [Responsabilidade Civil](responsabilidade-civil/consultas.md))**:**

* Atividades, coberturas e perfil de risco, cujo formato depende do produto.

**Calcular** ([Empresarial](empresarial/calcular.md) | [Responsabilidade Civil](responsabilidade-civil/calcular.md))**:**

* Realiza o processo de salvamento e cálculo do contrato.

**Proposta** ([Empresarial](empresarial/proposta.md) | [Responsabilidade Civil](responsabilidade-civil/proposta.md))**:**

* Realiza a geração de proposta.

[**Transmissão**](transmissao.md)**:**

* Realiza a solicitação de transmissão da proposta.

[**Cancelar proposta**](cancelar-proposta.md)**:**

* Cancela uma proposta transmitida.

{% hint style="info" %}
O produto **RC Obras** não está disponível nesta API.
{% endhint %}
