# Aula 9 — Documentação de Software

A Aula 9 começou com uma pergunta simples, que serve de teste para qualquer
repositório:

> *Se eu entrar hoje no GitHub do seu projeto, consigo entender e executar o
> projeto sem perguntar nada para vocês?*

A ideia central é que a documentação deve **reduzir a dependência de
explicações informais** e permitir que outra pessoa compreenda o projeto
sozinha.

## O que acontece sem documentação

- o projeto passa a depender de desenvolvedores específicos;
- novos integrantes têm dificuldade para entrar;
- configurações são esquecidas ou executadas de forma diferente por cada um;
- manutenção e resolução de problemas demoram mais;
- o conhecimento se perde quando alguém sai da equipe;
- as mesmas perguntas sobre instalação, execução e deploy se repetem.

## O que é documentação de software

É o conjunto de informações que ajuda pessoas a **compreender, utilizar,
desenvolver, testar e manter** um sistema. Uma boa documentação responde: o que
é o projeto, para que serve, como instalar e configurar, como executar e testar,
e como contribuir.

Ela atende quatro necessidades:

| Necessidade | Papel da documentação |
| --- | --- |
| Comunicação | Compartilhar conhecimento entre pessoas |
| Manutenção | Facilitar correções e evolução |
| Colaboração | Permitir trabalho em conjunto |
| Continuidade | Reduzir a dependência de indivíduos |

A frase que resume a aula: **documentar não é apenas registrar, é tornar o
conhecimento reutilizável.** Como exemplos de projetos bem documentados, a aula
citou React, Node.js, a documentação do Docker, Bitcoin e o repositório
github/brasil.

## Documentação e DevOps

DevOps integra pessoas, processos e tecnologia para entregar software de forma
contínua. A documentação entra registrando **como o código é desenvolvido, como
as mudanças são validadas, como a pipeline funciona e como o sistema é
implantado**. Cada perfil usa a documentação de um jeito:

| Quem | Para quê |
| --- | --- |
| Dev | Começar a trabalhar com menos dependência da equipe |
| Tester | Saber como executar e validar os testes |
| DevOps | Configurar pipeline, ambientes e deploy |
| Gestor | Acompanhar processos e decisões |
| Usuário | Aprender a usar o produto |

A documentação também combina várias áreas: Engenharia de Software (requisitos,
arquitetura, código e testes), Gestão de Projetos (escopo, cronograma, riscos),
DevOps (CI/CD, infraestrutura, deploy e monitoramento), Segurança (políticas,
acessos e incidentes), Qualidade (critérios de aceitação e evidências) e
Produto/UX (jornadas, regras de negócio e usabilidade).

## Tipos de documentação

- **Técnica:** arquitetura, APIs, banco de dados, componentes e configurações.
- **De projeto:** objetivos, requisitos, decisões e organização.
- **De processo:** branches, commits, Pull Requests, testes, pipeline e deploy.

## O README

O README é normalmente o primeiro documento consultado em um repositório e deve
permitir entender rapidamente o propósito, as tecnologias, os pré-requisitos, a
instalação e execução, os testes, a contribuição e os links importantes.

| Seção | O que deve ter |
| --- | --- |
| Tecnologias e pré-requisitos | Linguagem, framework, banco, gerenciador de pacotes, Docker e Git, com versões quando fizer diferença |
| Instalação e execução | Uma sequência reproduzível: clonar → acessar a pasta → instalar → configurar variáveis → executar → acessar → testar |
| Configuração e variáveis | Quais variáveis existem, para que servem e quais são obrigatórias, com valores de exemplo e sem expor segredos |
| Execução e testes | Comandos para iniciar a aplicação e rodar testes unitários, de integração e de performance |
| Estrutura do projeto | As pastas principais (`src/`, `tests/`, `docs/`, `.github/workflows/`) e a responsabilidade de cada uma, sem descrever arquivo por arquivo |

## Documentação do processo DevOps

| Etapa | O que documentar |
| --- | --- |
| Desenvolvimento | Implementação de funcionalidades e correções |
| Git | Controle de versão e histórico das alterações |
| Pull Request | Revisão e integração das mudanças |
| Build | Preparação do software para execução |
| Testes | Validação do funcionamento e identificação de falhas |
| Pipeline CI/CD | Automação da integração, validação e entrega |
| Deploy | Publicação da aplicação em um ambiente de execução |

## O que NÃO colocar na documentação

- senhas e credenciais de usuários, administradores ou bancos de dados;
- chaves de API e tokens que deem acesso a serviços ou recursos privados;
- dados sensíveis: informações pessoais, dados de clientes e informações
  internas restritas;
- arquivos `.env` ou configurações que contenham segredos;
- detalhes de infraestrutura que facilitem acessos indevidos.

## Atividade

> Escolha um projeto de software e elabore sua documentação, apresentando o
> objetivo, o problema que pretende resolver, o escopo e os principais
> requisitos funcionais e não funcionais. Descreva as tecnologias utilizadas, a
> arquitetura da aplicação e a organização dos principais componentes do
> sistema.
>
> Crie ou atualize o arquivo `README.md` do repositório no GitHub, incluindo os
> pré-requisitos, as instruções de instalação, configuração e execução do
> projeto. Quando aplicável, documente também as APIs, o banco de dados, as
> variáveis de ambiente e os procedimentos de testes e deploy.

O projeto escolhido foi o projeto final da disciplina,
**[RateMedia](https://github.com/LuisGlauser/RateMedia)**. A documentação foi
separada em três camadas, cada uma com um público diferente:

| Camada | Onde | Conteúdo |
| --- | --- | --- |
| README | [Repositório](https://github.com/LuisGlauser/RateMedia#readme) | Visão geral, funcionalidades, stack, arquitetura, pipeline, links e contribuidores |
| Wiki | [Wiki do projeto](https://github.com/LuisGlauser/RateMedia/wiki) | Instalação, variáveis de ambiente, testes, deploy, guias de usuário e de administrador, FAQ |
| Central de documentação | [ratemedia.vercel.app/docs](https://ratemedia.vercel.app/docs) | 11 capítulos em Markdown, 14 diagramas, além de Word e PDF |

Os 11 capítulos cobrem tudo o que a atividade pede: visão geral (objetivo,
problema e escopo), requisitos funcionais e não funcionais, regras de negócio,
casos de uso, histórias de usuário, arquitetura, modelo de dados (DER e
dicionário), diagramas de classes e de sequência, integrações com APIs,
DevOps (CI/CD, Docker e deploy) e testes.

Também foram aplicadas as regras da seção *o que não colocar*: o repositório tem
apenas um `.env.example` com valores fictícios, e as chaves reais ficam nas
variáveis de ambiente da Vercel.

## Referência

FATEC. **Aula 09 — Documentação de Software**. Prof. Me. Deivison S. Takatu.
Disponível em [`documentos/`](../../documentos/README.md). Exemplo da disciplina:
[deivisontakatu/aula-documentacao-software](https://github.com/deivisontakatu/aula-documentacao-software).
