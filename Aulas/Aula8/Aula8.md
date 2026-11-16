# Aula 8 — Apresentação de Ferramentas DevOps

Até a Aula 7, cada aula apresentou um pedaço do ciclo DevOps: integração e
entrega contínua, gerência de configuração, pipelines, Actions do Marketplace e
testes automatizados. A Aula 8 inverteu o papel: em vez de o professor
apresentar, **cada grupo ficou responsável por estudar uma ferramenta do
ecossistema DevOps e ensiná-la para a turma**.

## O que a apresentação precisava responder

A proposta era que a turma saísse da apresentação entendendo a ferramenta de
ponta a ponta, guiada por sete perguntas:

- O que é a ferramenta?
- Qual problema ela resolve?
- Em qual etapa do DevOps ela pode ser utilizada?
- Como funciona?
- Como utilizá-la na prática?
- Quais são suas vantagens e limitações?
- Como ela pode ser integrada a um projeto?

## Roteiro sugerido

| # | Etapa | Conteúdo |
| --- | --- | --- |
| 01 | Introdução | Nome, categoria e contexto da ferramenta |
| 02 | Problema | Qual necessidade ela resolve |
| 03 | Funcionamento | Como a ferramenta funciona por dentro |
| 04 | Aplicação no DevOps | Em qual etapa ou processo ela entra |
| 05 | Demonstração | Exemplo prático de utilização |
| 06 | Integração | Como se relaciona com outras ferramentas |
| 07 | Vantagens e limitações | Pontos positivos, desafios e restrições |
| 08 | Conclusão | Quando utilizar e principais aprendizados |

A **demonstração prática** era o centro da apresentação, seguindo o fluxo
*entrada → processo → resultado*. O ponto destacado na aula foi explicar o que
está acontecendo em cada passo, e não apenas mostrar a tela. A ferramenta também
devia aparecer dentro de um contexto: por exemplo, uma equipe que desenvolve uma
aplicação web e precisa automatizar uma atividade do processo. Cada apresentação
tinha de 15 a 20 minutos.

## Comparação e análise

Para não ficar só na descrição, a ferramenta precisava ser analisada em seis
aspectos:

| Aspecto | Pergunta |
| --- | --- |
| Facilidade de uso | É simples de aprender? |
| Integração | Com quais ferramentas trabalha? |
| Automação | O que pode ser automatizado? |
| Custo | Possui versão gratuita? |
| Escalabilidade | Atende projetos maiores? |
| Limitações | Quais são suas principais restrições? |

## Ferramentas e critérios de avaliação

Cada grupo ficou com uma ferramenta: **Docker**, **Kubernetes**, **Grafana**,
**AWS** e **GitHub Actions**. Juntas, elas cobrem boa parte do ciclo:
contêineres, orquestração, observabilidade, nuvem e automação de pipelines.

| Critério | Peso |
| --- | --- |
| Domínio e compreensão da ferramenta | 2,0 |
| Relação com DevOps | 1,5 |
| Demonstração prática | 2,0 |
| Qualidade e organização da apresentação | 1,5 |
| Análise: vantagens, limitações e aplicações | 1,0 |
| Participação e divisão entre integrantes | 1,0 |
| Clareza, comunicação e gestão do tempo | 1,0 |
| **Total** | **10,0** |

## Nossa ferramenta: Docker

O meu grupo (Grupo A) ficou com o **Docker**, que resolve o problema clássico
do *"na minha máquina funciona"*: empacota a aplicação com tudo o que ela
precisa (runtime, dependências e configuração) em uma **imagem**, que roda da
mesma forma em qualquer lugar como um **contêiner**. Na esteira DevOps, ele
aparece na padronização do ambiente de desenvolvimento, nos testes
reproduzíveis na CI e no empacotamento para o deploy.

O mesmo grupo é o do projeto final, então o Docker não ficou só na apresentação:
o [RateMedia](https://github.com/LuisGlauser/RateMedia) roda em contêiner.

| Conceito | Como aparece no RateMedia |
| --- | --- |
| Dockerfile *multi-stage* | Três estágios (`deps` → `builder` → `runner`): a imagem final leva só o build *standalone* do Next.js |
| Imagem enxuta | Base `node:22-alpine` e `.dockerignore` excluindo dependências, testes e arquivos de ambiente |
| Segurança | O contêiner roda com o usuário `nextjs`, sem privilégios de root |
| Docker Compose | Serviço `app` com portas, variáveis de ambiente e `restart: unless-stopped` |
| Healthcheck | O Compose verifica periodicamente se a aplicação responde na porta 3000 |

## Referência

FATEC. **Aula 08 — Apresentação Ferramentas DevOps**. Prof. Me. Deivison S.
Takatu. Disponível em [`documentos/`](../../documentos/README.md).
