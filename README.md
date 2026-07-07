<div align="center">

<img src="assets/wordmark.svg" alt="EconsDados" height="60"/>

**Bases de dados públicas organizadas, documentadas e harmonizadas pelo laboratório**

[![Site](https://img.shields.io/badge/Site-econsufjf.github.io-1e4a8a?style=flat-square)](https://econsufjf.github.io/econsdados)
[![Licença](https://img.shields.io/badge/Licença-CC%20BY%204.0-c9a84c?style=flat-square)](https://creativecommons.org/licenses/by/4.0/)

</div>

---

## O que é este repositório

O **EconsDados** reúne bases de dados públicas utilizadas nas pesquisas do ECONS — Laboratório de Estudos Econômicos da UFJF. Para cada base você encontra:

- **Guia de uso** — o que é a base, anos disponíveis e como interpretá-la corretamente
- **Documentação da harmonização** — o que foi feito para compatibilizar os dados ao longo do tempo
- **Rotinas de análise** — scripts em R e/ou Stata para operações comuns

Os dados brutos **não estão neste repositório** — são grandes demais para o GitHub. Os guias indicam onde baixá-los e como reproduzir o processamento.

---

## Organização

```
econsdados/
├── saude/
│   ├── sinasc/          ← Nascidos Vivos (DataSUS)
│   └── sihsus/          ← Internações Hospitalares (DataSUS)
├── mercado_de_trabalho/ ← em preparação
│   ├── rais/
│   └── caged/
├── assets/
│   └── wordmark.svg
└── _template_base.md    ← modelo para documentar novas bases
```

---

## Como usar

Cada pasta de base contém um arquivo `guia_de_uso_da_base.md` com todas as informações necessárias para começar. Leia o guia antes de usar os dados.

Para contribuir com documentação de uma nova base, use o `_template_base.md` como ponto de partida.

---

## Bases disponíveis

| Base | Tema | Anos harmonizados | Status |
|---|---|---|---|
| [SINASC](saude/sinasc/guia_de_uso_da_base.md) | Saúde | 1996–2024 | ✅ Disponível |
| SIHSUS | Saúde | — | 🔄 Em preparação |
| RAIS | Mercado de trabalho | — | 🔄 Em preparação |
| CAGED | Mercado de trabalho | — | 🔄 Em preparação |

---

<div align="center">
<sub>Econs — Laboratório de Estudos Econômicos · UFJF &nbsp;|&nbsp; <a href="https://econsufjf.github.io">econsufjf.github.io</a></sub>
</div>
