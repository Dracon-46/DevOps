# Pesquisa — Comparação entre Azure DevOps e GitHub em CI/CD

Atividade da Aula 4, baseada no artigo acadêmico "Practical Comparison Between the CI/CD Platforms Azure DevOps and GitHub", de Vladislav Manolov, Daniela Gotseva e Nikolay Hinov, publicado na revista Future Internet, v. 17, n. 4, artigo 153, 2025. DOI: 10.3390/fi17040153.

## Objetivo

Identificar as ferramentas citadas pelos autores e realizar uma análise comparativa entre as plataformas e ferramentas relacionadas a CI/CD, considerando características, funcionalidades, vantagens, limitações e situações em que cada solução é mais adequada.

## Metodologia do artigo

Os autores adotam uma abordagem multifacetada, analisando recursos técnicos, automação, mecanismos de segurança, escalabilidade, custo-benefício e experiência de uso. A pesquisa combina estudos de caso reais de empresas da Fortune Global 500, análise de participação de mercado, padrões de adoção em setores regulados, métricas de desempenho e confiabilidade, histórico de incidentes de indisponibilidade e comparação de estruturas de custo entre organizações de diferentes portes.

## Ferramentas citadas no artigo

Além de Azure DevOps e GitHub, foco central da comparação, os autores citam outras plataformas de CI/CD como referência de mercado:

- Jenkins — servidor de automação open source, um dos mais tradicionais do mercado.
- GitLab CI/CD — solução integrada ao GitLab, concorrente direto do GitHub Actions.
- Atlassian Bitbucket — repositórios Git com pipelines integrados (Bitbucket Pipelines).
- AWS CodePipeline — serviço de CI/CD nativo da AWS.
- JetBrains TeamCity — servidor de CI/CD da JetBrains, popular em ambientes .NET/Java.
- TravisCI — uma das pioneiras em CI hospedado para projetos open source.
- CircleCI — plataforma de CI/CD baseada em nuvem, focada em velocidade de execução.

Dentro do Azure DevOps, os recursos analisados são: Azure Pipelines, Azure Repos, Azure Boards, Azure Test Plans e Azure Artifacts. O artigo também menciona integrações com Azure Active Directory, Microsoft Defender for DevOps e serviços do ecossistema Azure (AKS, Azure Functions, Azure App Services).

Dentro do GitHub, o destaque é o GitHub Actions, complementado pelo GitHub Advanced Security (code scanning, Dependabot, secret scanning). O artigo também cita integrações multi-nuvem com AWS Lambda e Google Kubernetes Engine (GKE), além de ferramentas comuns ao ecossistema DevOps como Docker, Kubernetes e HashiCorp Terraform/Vault.

## Participação de mercado

Segundo os dados citados no artigo, o GitHub lidera com 33% de participação de mercado entre as plataformas de CI/CD, seguido por Azure DevOps com 24%, Jenkins com 14% e GitLab com 9%. Juntas, GitHub e Azure DevOps respondem por mais da metade do mercado.

## Comparação por característica

| Aspecto | Azure DevOps | GitHub |
|---|---|---|
| Funcionalidade de CI/CD | Pipelines robustos, melhor suporte a repositórios monolíticos e implantações em múltiplos estágios | GitHub Actions, leve e rápido, ideal para ciclos ágeis e times pequenos/médios |
| Controle de versão e repositórios | Azure Repos, com foco corporativo | Nativo ao Git, com forte cultura de colaboração e pull requests |
| Integrações | Forte integração com o ecossistema Microsoft e serviços híbridos/on-premises | Boa integração multi-nuvem (AWS, GCP, Azure) e com o ecossistema de mercado |
| Segurança e conformidade | Azure AD, acesso condicional, acesso privilegiado just-in-time (JIT), Microsoft Defender for DevOps; controles de acesso mais restritivos por padrão; atende normas como ISO 27001, SOC 2, GDPR, HIPAA e FedRAMP | GitHub Advanced Security (code scanning, Dependabot, secret scanning), alertas de segurança diretamente nos pull requests, abordagem "developer-first" |
| Escalabilidade e desempenho | SLA de disponibilidade de 99,9%, com redundância global; melhor para projetos corporativos complexos e de grande escala | SLA de disponibilidade de 99,95%; mais leve para times pequenos/médios, porém mais sujeito a instabilidades em picos de uso |
| Custos | Modelo pago por usuário/serviço, com 1.800 minutos gratuitos de pipeline por mês (repositórios públicos); permite otimização via agentes self-hosted | Estrutura de assinatura em camadas (Free, Team, Enterprise), com 2.000 minutos gratuitos de CI/CD no plano Free; pacotes de funcionalidades podem forçar upgrades; runners macOS bem mais caros que os baseados em Linux |
| Experiência de uso | Curva de aprendizado maior, porém suíte completa (código, pipelines, testes, artefatos e gestão ágil integrados) | Curva de aprendizado menor, configuração simples via YAML versionado junto ao código |
| Testes e qualidade | Azure Test Plans para testes manuais e exploratórios, além de suporte a testes automatizados nas pipelines | Suporte a testes automatizados integrados às Actions, com relatórios de teste no próprio fluxo de PR |

## Vantagens e limitações

Azure DevOps:

- Vantagens: suíte unificada (código, pipelines, testes, artefatos e gestão ágil em um só lugar); segurança de nível corporativo (Azure AD, acesso JIT, Defender for DevOps); forte adequação a setores regulados (financeiro, saúde, defesa, governo); SLA de disponibilidade robusto com redundância global.
- Limitações: maior complexidade inicial; menor apelo para times pequenos ou projetos open source; overhead de configuração para cenários simples; custo por usuário/serviço pode crescer conforme a organização escala.

GitHub:

- Vantagens: simplicidade de configuração (workflows YAML versionados junto ao código); grande comunidade e ecossistema de Actions prontas; forte flexibilidade multi-nuvem; segurança integrada diretamente ao fluxo de desenvolvimento (alertas em pull requests); minutos gratuitos generosos no plano Free.
- Limitações: SLA de disponibilidade ligeiramente inferior em cenários de pico; runners macOS com custo elevado; pacotes de funcionalidades por assinatura podem obrigar upgrades desnecessários; controles de acesso e governança menos rígidos por padrão que os do Azure DevOps.

## Quando usar cada solução

Azure DevOps é preferido por empresas da Fortune 500, agências governamentais, setores regulados (financeiro, saúde, defesa) e organizações fortemente integradas ao ecossistema Microsoft, especialmente quando há necessidade de governança corporativa estruturada, conformidade regulatória, integração híbrida/on-premises e gerenciamento de arquiteturas complexas e de grande escala.

GitHub é preferido por comunidades open source, instituições de pesquisa, startups e times pequenos, organizações cloud-native e voltadas a GitOps, e projetos multi-nuvem (AWS, GCP, Azure). É a escolha mais indicada quando o foco está em agilidade de desenvolvimento, automação baseada em Git, custo-benefício para equipes menores e colaboração orientada à comunidade.

## Conclusão

Os autores concluem que não existe uma plataforma universalmente superior — a escolha depende das prioridades organizacionais. Azure DevOps se destaca quando governança de DevOps corporativo, conformidade e integração híbrida são prioridades; GitHub se destaca quando agilidade do desenvolvedor, automação nativa em Git e flexibilidade multi-nuvem são mais importantes. Compreender os pontos fortes e as limitações de cada plataforma é essencial para otimizar fluxos de trabalho e atingir metas de escalabilidade a longo prazo, já que a escolha impacta diretamente a eficiência da equipe, a postura de segurança e a escalabilidade operacional.

## Referência

MANOLOV, Vladislav; GOTSEVA, Daniela; HINOV, Nikolay. Practical Comparison Between the CI/CD Platforms Azure DevOps and GitHub. Future Internet, v. 17, n. 4, artigo 153, 2025. DOI: 10.3390/fi17040153.
