# Aula 10 — Projeto DevOps

A Aula 10 apresentou o **projeto final da disciplina**: desenvolver em grupo uma
aplicação web e aplicar nela, de forma integrada, tudo o que foi visto ao longo
do semestre (controle de versão, testes automatizados, integração e entrega
contínua, contêineres, configuração segura e monitoramento). O foco é a
automação do desenvolvimento, dos testes e da implantação, com colaboração,
qualidade e melhoria contínua.

## Objetivos

- aplicar os conceitos de DevOps na prática;
- desenvolver uma aplicação web funcional e integrada;
- automatizar testes, integração e deploy;
- padronizar os ambientes de desenvolvimento e execução;
- monitorar o funcionamento da aplicação.

O tema é livre, definido pelo grupo, desde que resolva um problema ou uma
necessidade identificável e atenda aos requisitos técnicos da disciplina.

## Requisitos técnicos

| Área | O que é cobrado |
| --- | --- |
| Arquitetura | Front-end, back-end (regras de negócio e endpoints), banco de dados e, quando aplicável, middleware de integração, autenticação ou validação |
| Git e GitHub | Código e documentação no repositório, branches por funcionalidade, commits descritivos, Pull Requests, revisão de código e ligação entre tarefas e alterações |
| Testes | Unitários, de integração, E2E (fluxos do usuário) e de performance (latência, volume e erros) |
| Integração contínua | GitHub Actions instalando dependências, validando a estrutura, rodando os testes, fazendo o build e verificando a qualidade |
| Docker | Dockerfile, portas e variáveis de ambiente, organização dos serviços, instruções de execução e demonstração containerizada |
| Entrega contínua | Construção automatizada, implantação automatizada, verificação pós-deploy, processo documentado e identificação da versão publicada |
| Observabilidade | Registro de eventos e erros, verificação de disponibilidade, métricas operacionais e monitoramento do ambiente |
| Configuração e segurança | Código separado da configuração, variáveis de ambiente, `.env.example` sem credenciais reais, proteção de segredos, permissões mínimas na pipeline e verificação de vulnerabilidades |

**Entregáveis:** repositório com histórico, branches e Pull Requests; testes com
evidências de execução; pipeline de CI/CD; Dockerfiles; README e instruções
técnicas; aplicação implantada (endereço público ou implantação reproduzível); e
uma apresentação técnica demonstrando os requisitos.

## Nosso projeto: RateMedia

O grupo desenvolveu o **[RateMedia](https://github.com/LuisGlauser/RateMedia)**, uma plataforma no estilo do
Letterboxd para acompanhar, avaliar e resenhar animes, mangás, séries e filmes,
com um módulo de campanhas de RPG criadas e avaliadas pela comunidade.

- **Aplicação no ar:** <https://ratemedia.vercel.app>
- **Documentação:** <https://ratemedia.vercel.app/docs> e [Wiki](https://github.com/LuisGlauser/RateMedia/wiki)
- **Stack:** Next.js 15 e React 19, Supabase (PostgreSQL com RLS e Auth),
  APIs AniList, Jikan e TMDB, Vitest, Playwright, GitHub Actions, Docker e Vercel

## Como cada requisito foi atendido

| Requisito | Evidência no RateMedia |
| --- | --- |
| **Arquitetura** | Front-end em React (Server e Client Components); back-end com Server Actions do Next.js; PostgreSQL no Supabase; middleware que renova a sessão e protege rotas privadas |
| **Git e GitHub** | Branches por tipo (`docs/`, `chore/`), Conventional Commits, Pull Requests com template, `main` protegida, templates de issue, `CONTRIBUTING.md` e tags de versão |
| **Testes unitários** | 90 testes no Vitest: busca, formatação, permissões, clientes das APIs externas e central de documentação |
| **Testes de integração** | 95 testes: Server Actions, middleware e camada de dados com um dublê do Supabase |
| **Testes E2E** | 16 testes no Playwright: home, busca, filtros, paginação, login, cadastro, campanhas e 404 |
| **Testes de performance** | Script de carga com perfis *smoke*, *load* e *stress*, medindo latência p95, vazão e taxa de erros, com limites que reprovam a pipeline |
| **Integração contínua** | Workflow em três jobs: (1) lint, typecheck, unitários, integração, build e `npm audit`; (2) E2E; (3) performance, os dois últimos em paralelo, com relatórios publicados como *artifacts* |
| **Docker** | Dockerfile *multi-stage* com usuário sem privilégios, `docker-compose.yml` com portas, variáveis e *healthcheck*, e `.dockerignore` |
| **Entrega contínua** | Deploy de produção na Vercel em <https://ratemedia.vercel.app> |
| **Versão publicada** | Versionamento semântico com tags `v0.1.0` e `v0.2.0`, `CHANGELOG.md` e versão exibida no rodapé do site |
| **Observabilidade** | *Healthcheck* do contêiner, registro de falhas das APIs externas no log do servidor, logs da Vercel e métricas de latência e erros geradas pelo teste de performance |
| **Configuração e segurança** | `.env.example` sem credenciais, segredos só em variáveis de ambiente, *Row Level Security* em todas as tabelas, `permissions: contents: read` na pipeline, `npm audit` e Dependabot |
| **Documentação** | README, `CONTRIBUTING.md`, `SECURITY.md`, Wiki e central `/docs` (requisitos, casos de uso, histórias de usuário, UML, DER, Word e PDF) |

### Pontos a evoluir

- **Deploy automático:** o deploy na Vercel ainda é disparado manualmente, porque
  o repositório não está ligado à Vercel pela integração com o GitHub. Com a
  integração, cada Pull Request ganharia um *preview* e cada merge na `main`
  publicaria em produção sozinho.
- **Monitoramento em produção:** faltam alertas e um painel de métricas
  contínuas (por exemplo, com Grafana ou com o monitoramento da Vercel).
- **Testes de RLS:** as políticas de acesso do banco são validadas manualmente;
  o próximo passo é testá-las contra um Supabase local.

## Apresentação técnica

O roteiro pedido para a apresentação final:

1. objetivo e funcionalidades da aplicação;
2. arquitetura e comunicação entre os componentes;
3. organização do GitHub e fluxo de Pull Requests;
4. execução dos testes;
5. construção e execução dos contêineres;
6. processo de deploy.

## Materiais de apoio da disciplina

- [Atividade do projeto final](https://github.com/deivisontakatu/aula-devops/tree/main/Atividade)
- [Projeto DevOps](https://github.com/deivisontakatu/projeto-devops)
- [Projeto Docker](https://github.com/deivisontakatu/projeto-docker)
- [Projeto Kubernetes](https://github.com/deivisontakatu/projeto-kubernetes)
- [DevOps com GitHub Actions e testes](https://github.com/deivisontakatu/projeto-devops-testes)
- [Variáveis de ambiente](https://github.com/deivisontakatu/projeto-variavel-ambiente)

## Referências

FATEC. **Aula 10 — Projeto DevOps**. Prof. Me. Deivison S. Takatu. Disponível em
[`documentos/`](../../documentos/README.md).

HUMBLE, J.; PRIKLANDNICKI, R. **Entrega Contínua: como entregar software de
forma rápida e confiável**. São Paulo: Bookman, 2013.

KIM, G.; HUMBLE, J.; DEBOIS, P.; WILLIS, J. **Manual de DevOps: como obter
agilidade, confiabilidade e segurança em organizações tecnológicas**. São Paulo:
Starlin Alta Editora, 2018.
