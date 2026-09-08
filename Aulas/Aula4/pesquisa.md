# Pesquisa — Comparação entre Azure DevOps e GitHub em CI/CD

Atividade da Aula 4, baseada no artigo acadêmico "Practical Comparison Between the CI/CD Platforms Azure DevOps and GitHub", de Vladislav Manolov, Daniela Gotseva e Nikolay Hinov, publicado na revista Future Internet, v. 17, n. 4, 2025.

## Objetivo

Identificar as ferramentas citadas pelos autores e realizar uma análise comparativa entre as plataformas e ferramentas relacionadas a CI/CD, considerando características, funcionalidades, vantagens, limitações e situações em que cada solução é mais adequada.

## Ferramentas citadas no artigo

Azure DevOps:

- Azure Pipelines — motor de CI/CD para build, teste e deploy multiplataforma.
- Azure Repos — repositórios Git privados com controle de versão.
- Azure Boards — gestão ágil de trabalho (backlogs, sprints, Kanban).
- Azure Test Plans — planejamento e execução de testes manuais e exploratórios.
- Azure Artifacts — hospedagem de pacotes (NuGet, npm, Maven, etc.).

GitHub:

- GitHub Actions — automação de workflows de CI/CD via arquivos YAML acionados por eventos do repositório.
- GitHub Packages — registro de pacotes integrado ao repositório.
- Recursos complementares do ecossistema Git/GitHub usados para code review, colaboração e segurança (Dependabot, code scanning).

## Comparação por característica

| Aspecto | Azure DevOps | GitHub |
|---|---|---|
| Automação de CI/CD | Suíte completa e estruturada (Pipelines), forte em cenários corporativos e multiplataforma | GitHub Actions, fortemente integrado ao repositório e ao fluxo de trabalho baseado em Git |
| Gerenciamento de código-fonte | Azure Repos, com foco em times corporativos | Nativo ao Git, com forte cultura de colaboração open source |
| Segurança | Controles corporativos amplos, políticas de governança | Dependabot, code scanning e secret scanning integrados nativamente |
| Escalabilidade | Alta, voltada a grandes organizações e projetos complexos | Alta, com runners hospedados ou self-hosted, escalando conforme o repositório |
| Integração com outros serviços | Forte integração com o ecossistema Microsoft (Azure, Office, etc.) | Forte integração com o ecossistema de mercado (containers, cloud providers, marketplace de Actions) |
| Desempenho | Estável, adequado a pipelines longos e complexos | Ágil para pipelines menores e feedback rápido em pull requests |
| Custos | Planos voltados a empresas, com licenciamento por usuário/recursos | Modelo flexível, com uso gratuito generoso para projetos públicos e pequenos times |
| Facilidade de uso | Curva de aprendizado maior, porém suíte mais completa (boards, testes, artefatos) | Curva de aprendizado menor, configuração simples via YAML no próprio repositório |

## Vantagens e limitações

Azure DevOps:

- Vantagens: suíte unificada (código, pipelines, testes, artefatos e gestão ágil em um só lugar); forte governança; bom encaixe em ambientes corporativos e no ecossistema Microsoft.
- Limitações: maior complexidade inicial; menor apelo para times pequenos ou projetos open source; overhead de configuração para cenários simples.

GitHub:

- Vantagens: simplicidade de configuração (workflows YAML versionados junto ao código); grande comunidade e marketplace de Actions prontas; ótima experiência para desenvolvedores e colaboração open source.
- Limitações: funcionalidades de gestão de projeto (boards) mais simples que as do Azure Boards; para organizações muito grandes, pode exigir ferramentas complementares de governança.

## Quando usar cada solução

- Azure DevOps tende a ser mais adequado para organizações que precisam de uma solução completa e estruturada, com forte governança, múltiplas equipes e integração profunda com o ecossistema Microsoft.
- GitHub tende a ser mais adequado para equipes que priorizam workflows baseados em Git, colaboração ágil, automação simples integrada ao repositório e, especialmente, para projetos open source ou times menores.

Como destacado pelos autores, não existe uma ferramenta universalmente melhor — a escolha depende de fatores como estratégia de desenvolvimento, segurança, escalabilidade, infraestrutura disponível e orçamento.

## Referência

MANOLOV, Vladislav; GOTSEVA, Daniela; HINOV, Nikolay. Practical Comparison Between the CI/CD Platforms Azure DevOps and GitHub. Future Internet, v. 17, n. 4, 2025, p. 153. DOI: 10.3390/fi17040153.
