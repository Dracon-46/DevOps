# Aula 6 — Pipeline no push da main e análise de pipelines reais

A Aula 6 fechou o ciclo das aulas anteriores. Na Aula 4 o foco foi entender o
que é uma pipeline; na Aula 5, montar uma reaproveitando Actions do Marketplace;
aqui o objetivo foi integrar a pipeline ao gatilho que mais importa no dia a dia
— **todo push na branch principal** — e depois olhar para fora, estudando como
projetos reais e maduros organizam suas pipelines.

## Atividade — Tarefa 06

A tarefa tinha duas partes:

1. Integrar uma pipeline ao projeto usando o GitHub Actions, configurada para
   executar sempre que houver um novo push na branch `main`.
2. Buscar repositórios no GitHub que tenham pipeline integrada e analisar pelo
   menos três, destacando características, funcionalidades, gatilhos e histórico.

As duas partes foram resolvidas com o mesmo projeto: um **analisador estático de
workflows do GitHub Actions**. Ele lê um arquivo `.yml`, monta um modelo do
workflow (gatilhos, jobs, encadeamento, matriz, ações usadas) e aplica dez regras
de qualidade e segurança. Ou seja, a ferramenta construída na Parte 1 é a mesma
que produziu a análise da Parte 2.

## A pipeline

O gatilho exigido pela tarefa:

```yaml
on:
  push:
    branches: [main]
  pull_request:
    branches: [main]
  workflow_dispatch:
```

São três jobs encadeados com `needs`, então um só começa se o anterior passar:

| Etapa | O que faz |
| --- | --- |
| `qualidade` | ESLint sobre `src/` e `tests/` |
| `testes` | Matriz com Node 20 e 22, 80 testes no Vitest, relatório JUnit salvo como artefato |
| `auto-analise` | A ferramenta analisa o **próprio** `pipeline.yml` que a está executando |

O terceiro job é o detalhe mais interessante do projeto: a pipeline roda o
analisador sobre si mesma com `--falhar-em=alta`. Se alguém introduzir no
workflow uma ação sem versão fixada, uma permissão ampla demais ou uma
interpolação insegura em `run:`, o próprio job reprova. O relatório em Markdown
ainda é publicado em `$GITHUB_STEP_SUMMARY`, aparecendo direto no resumo da
execução.

## Os três repositórios analisados

A análise não foi feita no olho: cada repositório foi clonado com histórico
completo, os workflows passaram pelo analisador, e o histórico saiu de
`git log` e `git rev-list` sobre `.github/workflows`.

| | axios | fastapi | caddy |
| --- | --- | --- | --- |
| Linguagem | JavaScript | Python | Go |
| Workflows | 8 | 20 | 9 |
| Jobs no CI principal | 7 | 6 | 3 |
| Ações fixadas por SHA | 7/7 | 8/8 | 5/5 |
| Primeiro workflow | 18/06/2020 | 27/11/2019 | 20/03/2020 |
| Commits em workflows | 145 | 343 | 126 |

Alguns achados que valeram a pena:

- **Os três fixam 100% das ações por hash de commit**, não por tag. Tag é móvel,
  hash não é — e para compensar o congelamento, usam Dependabot agrupado para
  atualizar.
- **Dois deles rodam análise de segurança da própria pipeline** (`zizmor`), e o
  terceiro usa o `OpenSSF Scorecard` — o que mostra que a pipeline virou um
  artefato que merece revisão automática, exatamente a premissa do projeto.
- **A primeira automação dos projetos mais antigos não foi teste, e sim gestão de
  issues** — tanto no axios quanto no FastAPI.
- O Caddy compila para **dez sistemas operacionais** em matriz, com
  `fail-fast: false` para uma falha não derrubar os outros alvos.
- O FastAPI usa `workflow_run` para encadear pipelines: o deploy da documentação
  não é disparado por push, e sim pela conclusão do workflow de build.

A análise completa, com gatilhos por workflow e a saída do analisador para cada
repositório, está no documento do projeto.

## Projeto

- Repositório: [Devops_Aula6](https://github.com/Dracon-46/Devops_Aula6)
- Análise dos três repositórios: [`docs/analise-repositorios.md`](https://github.com/Dracon-46/Devops_Aula6/blob/main/docs/analise-repositorios.md)
- Execuções da pipeline: [aba Actions](https://github.com/Dracon-46/Devops_Aula6/actions)
