Resumo da aula sobre dependências e CI/CD

Na aula de hoje, aprofundamos nossos conhecimentos sobre dependências e entendemos melhor a importância delas no desenvolvimento de um projeto. Também relembramos os conceitos de CI/CD, principalmente a ideia de automatizar processos para facilitar a integração, os testes e a entrega de código.

Durante a aula, clonamos um repositório do GitHub para analisar, na prática, como um projeto funciona quando é baixado e executado em outro ambiente. A partir disso, percebemos que um projeto não é composto apenas pelo código que escrevemos, mas também depende de diversas bibliotecas, pacotes e ferramentas para funcionar corretamente.

Um dos pontos mais importantes foi entender que versões de dependências podem causar problemas. Uma aplicação pode funcionar normalmente no computador de uma pessoa, mas apresentar erros em outro computador caso as versões das bibliotecas sejam diferentes ou alguma dependência esteja faltando. Por isso, é importante definir e controlar corretamente as dependências utilizadas pelo projeto, garantindo que todos estejam trabalhando com uma configuração compatível.

Também vimos a importância de arquivos de configuração, como o package.json, que registra informações importantes do projeto e suas dependências. Ao clonar o repositório, por exemplo, não precisamos baixar manualmente cada biblioteca utilizada. Podemos utilizar o npm install, que instala as dependências necessárias de acordo com as configurações do projeto.

Depois de instalar as dependências, executamos o projeto com o npm start e verificamos se ele funcionava corretamente. Essa experiência mostrou, na prática, como o código pode ser compartilhado por meio de um repositório e posteriormente configurado e executado por outra pessoa.

Além disso, entendemos melhor por que subir o código para um repositório é tão importante. O objetivo não é apenas guardar o código, mas também permitir que outras pessoas tenham acesso ao projeto, possam cloná-lo, instalar suas dependências e continuar o desenvolvimento. Isso também está diretamente relacionado ao uso de CI/CD, já que, em um fluxo de desenvolvimento, o código enviado para o repositório pode passar por processos automáticos de instalação, testes e validação.

No final da aula, conseguimos compreender melhor a relação entre código, dependências, versões, GitHub e CI/CD, percebendo que manter as dependências organizadas e as versões controladas é fundamental para evitar problemas e garantir que o projeto funcione de maneira consistente em diferentes ambientes.

link do repositorio [Devops_Letreco](https://github.com/Dracon-46/Devops_Aula3) e link do projeto [Site_Letreco](https://devops-aula3.vercel.app/)
