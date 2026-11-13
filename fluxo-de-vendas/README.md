---
description: Realiza o processo de salvamento, cálculo, proposta e transmissão do contrato.
---

# Fluxo de vendas

## Produtos

| Produto                                              | `ProductCode`         | Id      |
| ---------------------------------------------------- | --------------------- | ------- |
| [Empresarial](empresarial/)                          | `businessproperty`    | `18001` |
| [Responsabilidade Civil](responsabilidade-civil/)    | `civilliability`      | `51006` |
| [RC Obras](rc-obras/)                                | `workscivilliability` | `51007` |
| [MS Construção](ms-construcao/)                      | `constructionworks`   | `67006` |

Cada produto tem suas próprias páginas de **Consultas**, **Calcular** e **Proposta**, pois os campos enviados diferem. Os passos abaixo são comuns.

{% hint style="info" %}
[Buscar produtos](servicos-de-consulta/calculo.md#buscar-produtos) retorna apenas os produtos habilitados para a corretora autenticada.
{% endhint %}

## Passos

[**Serviços de consulta**](servicos-de-consulta/)**:**

* Serviços compartilhados entre produtos: produtos, seguradoras, corretoras, CNAE, salários, profissões e métodos de pagamento.

**Consultas do produto** ([Empresarial](empresarial/consultas.md) | [Responsabilidade Civil](responsabilidade-civil/consultas.md) | [RC Obras](rc-obras/consultas.md) | [MS Construção](ms-construcao/consultas.md))**:**

* Atividades, coberturas e perfil de risco, cujo formato depende do produto.

[**Calcular**](calcular.md)**:**

* Realiza o processo de salvamento e cálculo do contrato. Campos por produto: [Empresarial](empresarial/calcular.md) | [Responsabilidade Civil](responsabilidade-civil/calcular.md) | [RC Obras](rc-obras/calcular.md) | [MS Construção](ms-construcao/calcular.md).

**Proposta** ([Empresarial](empresarial/proposta.md) | [Responsabilidade Civil](responsabilidade-civil/proposta.md) | [RC Obras](rc-obras/proposta.md) | [MS Construção](ms-construcao/proposta.md))**:**

* Realiza a geração de proposta.

[**Transmissão**](transmissao.md)**:**

* Realiza a solicitação de transmissão da proposta.

[**Cancelar proposta**](cancelar-proposta.md)**:**

* Cancela uma proposta transmitida.
