<div align="center">

<img src="../../assets/wordmark.svg" alt="EconsDados" height="60"/>

# SINASC

**Microdados do Sistema de Informações sobre Nascidos Vivos — registro oficial de nascimentos no Brasil (1996–2024)**

![Econs UFJF](https://img.shields.io/badge/Econs-UFJF-1e4a8a?style=flat-square)
![Fonte](https://img.shields.io/badge/Fonte-DataSUS-5a6070?style=flat-square)
![Anos](https://img.shields.io/badge/Anos-1996–2024-c9a84c?style=flat-square)
![Status](https://img.shields.io/badge/Status-Harmonizada-2e7d32?style=flat-square)

</div>

---

## O que é

O SINASC é o registro oficial do Ministério da Saúde de todos os nascidos vivos no Brasil, preenchido a partir da Declaração de Nascido Vivo. Cada linha da base é um **nascimento**, com informações sobre a mãe (idade, escolaridade, raça/cor), a gestação e o parto (duração, número de consultas de pré-natal, tipo de parto) e o recém-nascido (peso, Apgar, sexo).

---

## Cobertura

| | |
|---|---|
| **Anos disponíveis** | 1994–2024 |
| **Anos harmonizados** | 1996–2024 |
| **Periodicidade** | Anual |
| **Nível geográfico** | Nascimento / Município / UF / Brasil |
| **Fonte** | [DataSUS — SINASC](https://datasus.saude.gov.br/transferencia-de-arquivos/) |

---

## O problema: inconsistências ao longo do tempo

O DataSUS mudou o formato de algumas variáveis ao longo do tempo — sem aviso destacado e sem manter compatibilidade entre versões.

> [!WARNING]
> O mesmo nome de variável pode significar coisas diferentes dependendo do ano. Códigos de "não informado" (como `9999` no peso) aparecem misturados com valores reais se não forem tratados. Analisar a série histórica sem esse cuidado gera números errados silenciosamente.

---

## A solução: harmonização

Cada ano de 1996 a 2024 foi conferido variável por variável, comparando com a documentação oficial do DataSUS, e as inconsistências foram corrigidas.

**Estrutura dos arquivos:**

```
Bases/
├── <ano>/
│   ├── sinasc_<ano>.fst         ← bruto (exatamente como o DataSUS distribui)
│   └── sinasc_<ano>_harm.fst    ← harmonizado (use este)
```

> [!TIP]
> Use sempre a versão `_harm` para análises em série histórica. O arquivo bruto fica disponível para conferência, mas não deve ser usado diretamente.

Na versão harmonizada:
- Códigos de "não informado" (ex.: peso `9999`, Apgar `99`) foram convertidos para `NA`
- Foram criadas colunas de indicadores prontos, já calculados a partir das definições clínicas padrão

---

## Principais variáveis

| Categoria | Variável | Descrição |
|---|---|---|
| Identificação | `uf` | Unidade da Federação |
| Identificação | `ano` | Ano de referência |
| Identificação | `codmunnasc` | Código IBGE do município de ocorrência |
| Mãe | `idademae` | Idade da mãe |
| Mãe | `escmae` | Escolaridade da mãe |
| Mãe | `racacor` | Raça/cor da mãe |
| Mãe | `estcivmae` | Estado civil da mãe |
| Gestação e parto | `gestacao` | Duração da gestação (faixa) |
| Gestação e parto | `semagestac` | Semanas de gestação (a partir de 2010) |
| Gestação e parto | `consultas` | Número de consultas de pré-natal |
| Gestação e parto | `parto` | Tipo de parto |
| Recém-nascido | `peso` | Peso ao nascer (gramas) |
| Recém-nascido | `apgar1` | Apgar no 1º minuto |
| Recém-nascido | `apgar5` | Apgar no 5º minuto |
| Recém-nascido | `sexo` | Sexo |
| Indicadores prontos | `prematuro` | Nascimento prematuro (verdadeiro/falso) |
| Indicadores prontos | `baixo_peso` | Baixo peso ao nascer (verdadeiro/falso) |
| Indicadores prontos | `apgar1_baixo` | Apgar baixo no 1º minuto (verdadeiro/falso) |
| Indicadores prontos | `apgar5_baixo` | Apgar baixo no 5º minuto (verdadeiro/falso) |
| Indicadores prontos | `prenatal_insuficiente` | Pré-natal insuficiente (verdadeiro/falso) |

<details>
<summary>Sobre as demais variáveis</summary>

A base tem mais de 50 colunas no total. A tabela acima lista apenas as mais usadas em indicadores de saúde da criança e da mãe. Para a lista completa, consulte o dicionário oficial do DataSUS.

</details>

---

## Observações e limitações

> [!NOTE]
> - **1994 e 1995** existem na pasta, mas usam um formato diferente do restante da série e ainda não foram harmonizados. As colunas de indicadores prontos não estão disponíveis nesses anos.
> - `semagestac` (semanas exatas de gestação) disponível apenas a partir de 2010; anos anteriores registram apenas a faixa (`gestacao`).

---

## Referências

- 📄 [Dicionário de variáveis — DataSUS](https://datasus.saude.gov.br/transferencia-de-arquivos/)
- 🌐 [Portal de transferência de arquivos — DataSUS](https://datasus.saude.gov.br/transferencia-de-arquivos/)

---

<div align="center">
<sub>Econs — Laboratório de Estudos Econômicos · UFJF &nbsp;|&nbsp; <a href="https://econsufjf.github.io">econsufjf.github.io</a></sub>
</div>
