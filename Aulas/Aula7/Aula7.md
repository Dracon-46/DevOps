# Aula 7 — Testes Automatizados

A Aula 7 desceu um nível em relação às anteriores. Nas Aulas 4, 5 e 6 o assunto
foi a pipeline em si — o que ela é, como montá-la com Actions do Marketplace, em
que gatilho ela dispara. Aqui o foco passou a ser **o que roda dentro dela**: os
testes automatizados que decidem se uma alteração pode ou não avançar.

## Por que automatizar os testes

Testes automatizados são verificações executadas por ferramentas para validar se
a aplicação se comporta como o esperado, sem depender de alguém repetir cada
cenário à mão. A aula listou cinco motivos para automatizá-los:

- **reduzir erros humanos**, tirando a dependência de conferência manual;
- **aumentar a velocidade**, rodando dezenas de verificações em segundos;
- **identificar falhas rapidamente**, logo depois da alteração no código;
- **garantir consistência**, executando sempre os mesmos cenários;
- **aumentar a confiabilidade**, verificando continuamente se o que já
  funcionava continua funcionando.

## Pipeline de testes e pipeline de qualidade

A aula separou duas coisas que costumam ser confundidas:

- **Pipeline de testes** — executa as validações no sistema depois do build. O
  objetivo é garantir que alterações novas não quebrem o que já existia.
- **Pipeline de qualidade** — verifica se o código atende aos padrões definidos
  *antes* de avançar para as próximas etapas. Identifica inconsistências e
  problemas de padronização de forma antecipada.

Os princípios de pipeline repetidos aqui foram os mesmos das aulas anteriores:
**build uma única vez** (o mesmo artefato é promovido entre ambientes), **mesmo
deploy em todos os ambientes** (desenvolvimento → homologação → produção) e
**falhou, para tudo** — nenhuma etapa continua depois de um erro.

Quando um teste falha, a consequência é encadeada: a alteração não avança, a
equipe recebe o retorno sobre o problema, o código é corrigido antes da entrega,
e o risco de levar uma versão defeituosa para outro ambiente cai.

## Os três tipos de teste

| Tipo | O que valida | Exemplo de falha mostrado na aula |
| --- | --- | --- |
| **Unitário** | funções e métodos de forma isolada | mudar a regra de desconto para 15% — o sistema esperava 10% ou 5% |
| **Integração** | a comunicação entre módulos, serviços, APIs e bancos | mudar o texto do botão para "Calcular" — o teste não encontrou "Calcular Desconto" |
| **Performance** | velocidade e estabilidade sob carga | baixar o tempo máximo esperado para 1ms — a aplicação não respondeu dentro do configurado |

O que os três exemplos têm em comum: em cada um, **nada quebrou na aplicação** —
o que mudou foi a expectativa. É o melhor argumento a favor de manter os três
tipos, porque cada um enxerga uma classe de problema que os outros dois não
veem. O unitário não percebe que o botão sumiu; o de integração não percebe que
a conta ficou lenta.

## Qualidade e ESLint

A aula tratou qualidade de software como a capacidade do sistema de atender aos
requisitos, às necessidades do usuário e aos objetivos de negócio com
eficiência — confiabilidade, estabilidade, facilidade de manutenção e
capacidade de evoluir. Em ambientes DevOps, a qualidade deixa de ser
responsabilidade exclusiva dos testes e passa a integrar todo o ciclo de
desenvolvimento, entrega e operação. Como resume a citação usada na aula,
*"qualidade deve fazer parte do processo"* (Humble e Priklandnicki, 2013).

O **ESLint** entra como a ferramenta de análise estática dessa etapa: identifica
problemas de padronização e inconsistências no código JavaScript e, dentro da
pipeline, impede que código fora do padrão seja integrado (Moraes, 2015). O
exemplo da aula foi declarar `const x=1;` sem usar a variável, o que reprova na
regra `no-unused-vars`.

## Atividade — Tarefa 07

> Criem um novo projeto que integre três tipos de testes automatizados:
> unitário, integração e performance. Organizem o projeto para que cada tipo de
> teste possa ser executado e analisado de forma independente.
>
> Em seguida, criem uma pipeline de Integração Contínua (CI) utilizando um
> arquivo `.yml` no GitHub Actions, configurada para executar automaticamente a
> cada push na branch `main`. A pipeline deverá instalar as dependências,
> executar os três tipos de testes e apresentar os resultados.

O projeto está em **[Devops_Aula7](https://github.com/Dracon-46/Devops_Aula7)**,
com a aplicação publicada em
<https://dracon-46.github.io/Devops_Aula7/>.

Partindo do exemplo da disciplina
([deivisontakatu/projeto-pipeline-testes](https://github.com/deivisontakatu/projeto-pipeline-testes)),
o código da aplicação foi mantido. O trabalho foi atender aos dois pontos que o
enunciado acrescenta.

### Independência entre os tipos

Cada tipo de teste ganhou **sua própria configuração do Vitest**, com `include`
apontando só para a sua pasta, e seu próprio script:

| Tipo | Pasta | Config | Ambiente |
| --- | --- | --- | --- |
| Unitário | `src/tests/unit/` | `vitest.unit.config.js` | `node` |
| Integração | `src/tests/integration/` | `vitest.integration.config.js` | `jsdom` |
| Performance | `src/tests/performance/` | `vitest.performance.config.js` | `node`, um worker só |

O ambiente de cada um não é detalhe de configuração: unitário e performance não
tocam no DOM, então subir o `jsdom` só para descartá-lo custa tempo em toda
execução; o de integração renderiza o componente de verdade e precisa dele. E o
de performance roda serializado porque medir tempo com vários workers
disputando CPU no runner gera reprovação intermitente — o teste falha sem que
nada tenha piorado no código.

### A pipeline

Os três tipos rodam em **jobs separados e em paralelo**, depois do ESLint:

```text
push na main → qualidade → [unitário | integração | performance] → resultados
                                                                 → publicar
```

Rodar em jobs separados não é enfeite. Num job só, `npm test` para no primeiro
erro: se o unitário falha, você não fica sabendo se a integração passaria.
Separados, os três resultados aparecem sempre, e dá para reexecutar só o tipo
que falhou.

Para "apresentar os resultados", cada job roda um script que lê o relatório
JUnit e escreve uma tabela em `$GITHUB_STEP_SUMMARY` — o resultado aparece na
própria página da execução, sem abrir o log. No final, um job `resultados`,
com `if: always()`, baixa os três relatórios e monta o quadro consolidado; é
justamente quando algum tipo falha que esse quadro mais serve, e nesse caso ele
ainda lista nominalmente os casos que falharam.

## Referência

FATEC. **Aula 07 — Testes Automatizados**. Prof. Me. Deivison S. Takatu.
Disponível em [`documentos/`](../../documentos/README.md).
