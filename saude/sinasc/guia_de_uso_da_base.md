# Guia de uso — SINASC

## O que é

O SINASC (Sistema de Informações sobre Nascidos Vivos) é o registro oficial do Ministério da Saúde de todos os nascidos vivos no Brasil, preenchido a partir da Declaração de Nascido Vivo. Cada linha da base é um nascimento, com informações sobre a mãe (idade, escolaridade, raça/cor), a gestação e o parto (duração, número de consultas de pré-natal, tipo de parto) e o recém-nascido (peso, Apgar, sexo).

## Anos disponíveis

A base cobre de **1994 a 2024**. Os anos de **1996 a 2024** foram harmonizados (explicado abaixo) e estão prontos pra análise em série histórica. **1994 e 1995** ainda não passaram por esse processo — ver observação no final.

## O problema: os dados originais mudam de um ano pro outro

O DataSUS mudou o formato de algumas variáveis ao longo do tempo — sem aviso destacado, e sem manter compatibilidade entre versões. Isso é normal em um sistema de registro que roda há 30 anos, mas cria uma armadilha real pra quem analisa a série histórica: **o mesmo nome de variável pode significar coisas diferentes dependendo do ano**, e códigos de "não informado" (como `9999` no peso) aparecem misturados com valores reais se não forem tratados. Analisar a série sem saber disso gera número errado — silenciosamente, sem erro nenhum aparecer.

## A solução: harmonização

Pra resolver isso, cada ano de 1996 a 2024 foi conferido variável por variável, comparando com a documentação oficial do DataSUS, e as inconsistências foram corrigidas. O resultado é uma segunda versão da base — a **harmonizada** — que pode ser usada diretamente, sem repetir esse trabalho:

- Os arquivo brutos, como o DataSUS distribui, ficam em `Bases/<ano>/sinasc_<ano>.fst` (e `.dta`) — sem nenhuma alteração.
- A versão pronta pra análise fica em `Bases/<ano>/sinasc_<ano>_harm.fst` (e `.dta`) — **é essa que deve ser usada**.

Na versão harmonizada:

- Códigos de "não informado" (ex.: peso `9999`, Apgar `99`) foram convertidos para valor ausente (`NA`), em vez de entrar nas contas como se fossem números reais.
- Foram criadas colunas prontas com os principais indicadores de saúde da criança/mãe, já calculados a partir das definições clínicas padrão: prematuridade, baixo peso ao nascer, Apgar baixo (1º e 5º minuto) e pré-natal insuficiente.
- Todo o resto da base permanece exatamente como o DataSUS disponibiliza.

## Principais variáveis

| Categoria | Variáveis | O que é |
|---|---|---|
| Identificação | `uf`, `ano`, `codmunnasc` | UF, ano e código IBGE do município de ocorrência |
| Mãe | `idademae`, `escmae`, `racacor`, `estcivmae` | idade, escolaridade, raça/cor, estado civil da mãe |
| Gestação e parto | `gestacao`, `semagestac`, `consultas`, `parto`, `gravidez` | duração da gestação (faixa e, a partir de 2010, semanas exatas), nº de consultas de pré-natal, tipo de parto, gestação única/múltipla |
| Recém-nascido | `peso`, `apgar1`, `apgar5`, `sexo`, `dtnasc` | peso ao nascer (gramas), notas Apgar no 1º e 5º minuto, sexo, data de nascimento |
| Indicadores prontos | `prematuro`, `baixo_peso`, `apgar1_baixo`, `apgar5_baixo`, `prenatal_insuficiente` | colunas já calculadas (verdadeiro/falso), descritas acima |

A base tem bem mais colunas que essas (mais de 50, no total) — essa tabela lista só as mais usadas em indicadores de saúde da criança/mãe.

## Observação sobre 1994-1995

Esses dois anos existem na pasta, mas usam um formato de variáveis diferente do resto da série e ainda não passaram pela harmonização. Se for usar esses anos, trate com cuidado — as colunas de indicadores prontos não estão disponíveis neles.
