# Aula 4 – DevOps: Pipelines, CI/CD e Testes Automatizados

Na Aula 4 de DevOps, estudamos o conceito de pipelines e sua importância dentro dos processos de Integração Contínua (CI) e Entrega ou Implantação Contínua (CD). O conteúdo mostrou como é possível automatizar diversas etapas do desenvolvimento de software, desde a alteração do código e execução de testes até a geração de artefatos e, dependendo da configuração, a implantação da aplicação.

Um dos principais conceitos apresentados foi o de pipeline. Uma pipeline pode ser entendida como uma sequência automatizada de etapas que são executadas para validar, construir, testar e, posteriormente, disponibilizar uma aplicação. Dessa forma, tarefas que poderiam ser realizadas manualmente passam a ser executadas automaticamente sempre que determinadas condições são atendidas, como um novo commit ou um pull request.

Também aprendemos sobre os arquivos de configuração no formato .yml ou .yaml. Esses arquivos são utilizados para definir as etapas que serão executadas pela pipeline. Neles podem ser configurados eventos que iniciam a execução, ambientes, comandos, dependências entre etapas, ferramentas utilizadas, testes, builds e outras ações necessárias para automatizar o processo de desenvolvimento e entrega.

Durante a aula, utilizamos o GitHub Actions como exemplo prático. Foi possível observar diretamente no GitHub a execução de uma pipeline, acompanhando cada etapa e verificando os resultados apresentados pela plataforma. Essa demonstração ajudou a compreender melhor a relação entre o código armazenado no repositório, o arquivo .yml e a execução automatizada das tarefas.

Outro ponto importante estudado foi o encadeamento de pipelines e etapas. Uma pipeline pode possuir várias etapas que precisam ser executadas em uma determinada ordem. Por exemplo, primeiro pode ser realizada a instalação das dependências, depois a compilação da aplicação, em seguida os testes e, somente se essas etapas forem concluídas com sucesso, a implantação. Esse processo permite criar uma sequência de validações antes que uma versão do software seja disponibilizada.

Também foi discutida a possibilidade de possuir mais de um arquivo .yml dentro de um mesmo projeto. Isso é possível e pode ser útil quando existem diferentes processos que precisam ser automatizados. Por exemplo, um arquivo pode ser responsável pelos testes, outro pelo processo de build e outro pelo deploy. Dessa forma, o projeto pode possuir diferentes workflows, cada um com uma finalidade específica.

Outra dúvida levantada durante a aula foi sobre a execução simultânea de pipelines. Também é possível executar diferentes workflows ou etapas de forma paralela, desde que não exista uma dependência que exija que uma determinada etapa espere a conclusão de outra. A execução paralela pode reduzir o tempo total de processamento, principalmente quando existem vários testes independentes que podem ser realizados ao mesmo tempo.

Além das pipelines, estudamos a importância dos testes automatizados dentro do processo de CI/CD. A utilização de testes permite identificar problemas automaticamente antes que uma alteração seja integrada ou disponibilizada para os usuários. Dessa forma, a pipeline funciona também como uma barreira de qualidade, impedindo que alterações com problemas avancem para as próximas etapas.

Entre os principais tipos de testes abordados, destacam-se os testes unitários, os testes de integração e os testes de performance.

Os testes unitários têm como objetivo verificar pequenas partes isoladas da aplicação. Um exemplo seria testar individualmente uma função responsável por realizar um cálculo ou validar determinado dado. Como são testes menores e mais específicos, normalmente possuem execução rápida e podem ser executados frequentemente durante o desenvolvimento.

Os testes de integração verificam o funcionamento conjunto entre diferentes componentes do sistema. Um exemplo seria verificar se uma aplicação consegue se comunicar corretamente com um banco de dados ou se um serviço consegue consumir corretamente uma API. Esse tipo de teste é importante porque uma aplicação pode possuir componentes que funcionam individualmente, mas apresentam problemas quando são utilizados em conjunto.

Já os testes de performance têm como objetivo analisar o comportamento da aplicação em relação ao desempenho. Podem ser utilizados para avaliar tempo de resposta, quantidade de requisições suportadas, consumo de recursos e comportamento do sistema quando submetido a diferentes níveis de carga.

A utilização desses testes dentro de uma pipeline permite que problemas sejam identificados de maneira antecipada. Em vez de descobrir um erro somente depois que a aplicação foi disponibilizada, o processo de CI/CD pode executar automaticamente as verificações e interromper o fluxo quando uma etapa importante falhar.

A aula também serviu para compreender que CI/CD não significa apenas realizar o deploy automaticamente. O conceito envolve a criação de um processo confiável e repetível para validar e entregar software. A pipeline pode envolver diversas etapas, como análise do código, instalação de dependências, compilação, execução de testes, geração de artefatos, verificações de segurança e implantação.

Como atividade da Aula 4, foi proposta uma pesquisa baseada no artigo acadêmico "Practical Comparison Between the CI/CD Platforms Azure DevOps and GitHub", de Vladislav Manolov, Daniela Gotseva e Nikolay Hinov, publicado na revista Future Internet, volume 17, número 4, em 2025. O artigo apresenta uma comparação prática entre Azure DevOps e GitHub, analisando suas características e utilização em processos de CI/CD.

A atividade tem como objetivo identificar as ferramentas citadas pelos autores e realizar uma análise comparativa entre as plataformas e ferramentas relacionadas a CI/CD. A pesquisa deve considerar características, funcionalidades, vantagens, limitações e situações em que cada solução pode ser mais adequada.

O artigo apresenta uma comparação principalmente entre o Azure DevOps e o GitHub. Dentro do Azure DevOps, são abordados recursos como Azure Pipelines, Azure Repos, Azure Boards, Azure Test Plans e Azure Artifacts. Já no ecossistema GitHub, um dos principais recursos analisados é o GitHub Actions, utilizado para automação de workflows e processos de CI/CD.

A comparação realizada pelos autores considera diferentes aspectos, como automação de CI/CD, gerenciamento de código-fonte, segurança, escalabilidade, integração com outros serviços, desempenho, custos e facilidade de utilização. O Azure DevOps apresenta uma abordagem mais estruturada e voltada para ambientes corporativos, oferecendo uma suíte mais ampla de ferramentas para gerenciamento do ciclo de desenvolvimento. O GitHub, por sua vez, possui uma abordagem mais centrada no Git, nos repositórios e na experiência do desenvolvedor, utilizando o GitHub Actions para automatizar workflows diretamente dentro dos projetos.

Um dos pontos importantes da pesquisa será compreender que não existe necessariamente uma única ferramenta que seja melhor para todos os projetos. A escolha depende das necessidades da organização, do tamanho da equipe, da infraestrutura utilizada, dos requisitos de segurança, do nível de controle necessário, dos custos e da estratégia de desenvolvimento adotada.

O Azure DevOps pode ser especialmente interessante para organizações que necessitam de uma solução mais completa e estruturada, principalmente em ambientes corporativos e no ecossistema Microsoft. O GitHub pode ser mais adequado para equipes que priorizam workflows baseados em Git, colaboração, desenvolvimento ágil e automação diretamente integrada aos repositórios. Os autores destacam justamente que a escolha entre as plataformas deve considerar fatores como estratégia de desenvolvimento, segurança, escalabilidade, infraestrutura e orçamento.

Dessa maneira, a Aula 4 relacionou a parte teórica de DevOps com uma aplicação prática. Primeiro, foram apresentados os conceitos de pipelines, arquivos .yml, execução de etapas, testes automatizados e encadeamento de processos. Depois, esses conceitos puderam ser observados na prática utilizando o GitHub Actions. Por fim, a atividade proposta amplia o conteúdo da aula ao exigir uma análise acadêmica das principais plataformas utilizadas para implementar processos de CI/CD, permitindo compreender que existem diferentes soluções e que cada uma possui características, vantagens e limitações próprias.

Referência da atividade:

MANOLOV, Vladislav; GOTSEVA, Daniela; HINOV, Nikolay. Practical Comparison Between the CI/CD Platforms Azure DevOps and GitHub. Future Internet, v. 17, n. 4, 2025, p. 153. DOI: 10.3390/fi17040153.
