<div align="center">

<img src="../assets/wordmark.svg" alt="EconsDados" height="60"/>

# [Nome da Base]

**[Descrição em uma linha — o que é e o que registra]**

![Econs UFJF](https://img.shields.io/badge/Econs-UFJF-1e4a8a?style=flat-square)
![Fonte](https://img.shields.io/badge/Fonte-[Órgão]-5a6070?style=flat-square)
![Anos](https://img.shields.io/badge/Anos-[início]–[fim]-c9a84c?style=flat-square)
![Status](https://img.shields.io/badge/Status-Harmonizada-2e7d32?style=flat-square)

</div>

---

## O que é

[Descrição clara e direta da base — o que ela registra, quem preenche, qual é a unidade de observação (cada linha é um quê?).]

---

## Cobertura

| | |
|---|---|
| **Anos disponíveis** | [ex: 1996–2024] |
| **Anos harmonizados** | [ex: 1996–2024 · ver observação abaixo] |
| **Periodicidade** | [Anual / Mensal] |
| **Nível geográfico** | [Município / UF / Brasil] |
| **Fonte** | [Portal / Órgão e link] |

---

## O problema: inconsistências ao longo do tempo

[Descrever se houve mudanças de formato, nomes de variáveis, códigos, etc. entre os anos. Se a base é estável, indicar isso. Esse bloco explica ao usuário os riscos de usar a série histórica sem tratamento.]

> [!WARNING]
> [Aviso principal — ex: "O mesmo nome de variável pode significar coisas diferentes dependendo do ano."]

---

## A solução: harmonização

[Descrever o que foi feito para resolver as inconsistências. Se não foi necessário harmonizar, apagar este bloco.]

**Estrutura dos arquivos:**

```
Bases/
├── <ano>/
│   ├── nome_<ano>.fst         ← bruto (exatamente como a fonte distribui)
│   └── nome_<ano>_harm.fst    ← harmonizado (use este)
```

> [!TIP]
> Use sempre a versão `_harm` para análises em série histórica.

---

## Principais variáveis

| Categoria | Variável | Descrição |
|---|---|---|
| Identificação | `uf` | Unidade da Federação |
| Identificação | `ano` | Ano de referência |
| Identificação | `codmun` | Código IBGE do município (6 dígitos) |
| [Categoria] | `var1` | [descrição] |
| [Categoria] | `var2` | [descrição] |
| Indicadores prontos | `ind1` | [coluna calculada — descrever] |

<details>
<summary>Ver lista completa de variáveis</summary>

[Tabela expandida ou link para o dicionário completo]

</details>

---

## Observações e limitações

> [!NOTE]
> [Avisos importantes — anos incompletos, variáveis com alta proporção de missing, mudanças metodológicas da fonte, etc.]

---

## Referências

- 📄 [Dicionário de variáveis oficial]()
- 🌐 [Portal de download dos dados]()
- 📑 [Outros documentos usados na harmonização]()

---

<div align="center">
<sub>Econs — Laboratório de Estudos Econômicos · UFJF &nbsp;|&nbsp; <a href="https://econsufjf.github.io">econsufjf.github.io</a></sub>
</div>
