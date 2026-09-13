# Aula 5 — GitHub Actions na prática: Actions do Marketplace

A Aula 5 deu continuidade ao conteúdo de pipelines visto na Aula 4, passando da
teoria de CI/CD para o uso prático do **GitHub Marketplace**. Enquanto na aula
anterior o foco foi entender o que é uma pipeline, como os arquivos `.yml`
definem as etapas e por que os testes automatizados funcionam como barreira de
qualidade, aqui o objetivo passou a ser montar uma pipeline real reaproveitando
Actions já prontas, publicadas por terceiros.

Uma Action do Marketplace é um bloco de automação reutilizável: em vez de
escrever à mão os comandos de cada etapa, o workflow declara `uses:` apontando
para a Action e passa parâmetros por `with:` ou variáveis de ambiente. Isso
muda bastante a forma de montar a pipeline, porque tarefas que exigiriam vários
comandos de instalação e configuração passam a caber em poucas linhas.

## Atividade — Tarefa 05

A atividade proposta foi escolher **três Actions disponíveis no GitHub
Marketplace** e desenvolver um projeto que as utilizasse em uma pipeline
automatizada, aplicando cada Action em uma etapa adequada do processo. Além de
configurar o workflow, era necessário executar a pipeline, verificar o
funcionamento de cada etapa e documentar no projeto quais Actions foram
utilizadas, suas respectivas funções e como contribuíram para a automação.

O projeto desenvolvido foi um **painel de métricas DORA**: uma aplicação web que
calcula as quatro métricas usadas pelo relatório DORA para medir a maturidade de
um processo de entrega — frequência de deploy, lead time para mudanças, taxa de
falha em mudanças e tempo médio de restauração (MTTR). O tema conversa
diretamente com a disciplina, já que essas são as métricas normalmente usadas
para avaliar o resultado de uma adoção de DevOps.

## As três Actions escolhidas

As três foram distribuídas em etapas distintas, formando a sequência
**qualidade → teste → entrega**. As etapas são encadeadas com `needs:`, de modo
que uma só começa se a anterior terminar com sucesso — o mesmo encadeamento
discutido na Aula 4.

| Etapa | Action | Função na pipeline |
| --- | --- | --- |
| 1. Qualidade | [`super-linter/super-linter`](https://github.com/marketplace/actions/super-linter) | Análise estática do código (ESLint e validação de JSON) antes de qualquer teste |
| 2. Testes | [`dorny/test-reporter`](https://github.com/marketplace/actions/test-reporter) | Lê o relatório JUnit gerado pelo Vitest e publica o resultado dos testes como check run na interface do GitHub |
| 3. Deploy | [`peaceiris/actions-gh-pages`](https://github.com/marketplace/actions/github-pages-action) | Publica a pasta `dist/` gerada pelo build no GitHub Pages, apenas quando o push é na `main` |

A escolha da ordem foi proposital: a análise estática é a verificação mais
barata da pipeline, então falhar nela primeiro evita gastar tempo de runner
instalando dependências e executando testes de um código que já se sabe
irregular. O deploy, por depender das duas etapas anteriores, só acontece com o
código validado e testado.

## Projeto

O código, o workflow completo e a documentação detalhada de cada Action estão no
repositório do projeto:

- Repositório: [Devops_Aula5](https://github.com/Dracon-46/Devops_Aula5)
- Site publicado pela pipeline: <https://dracon-46.github.io/Devops_Aula5/>
- Execuções da pipeline: [aba Actions](https://github.com/Dracon-46/Devops_Aula5/actions)
