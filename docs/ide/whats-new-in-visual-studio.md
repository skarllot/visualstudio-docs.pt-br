---
title: Novidades no Visual Studio 2017 | Microsoft Docs
ms.custom: 
ms.date: 04/06/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: edc126208bb401c8dba9a6be722cbd0dbda21caf
ms.openlocfilehash: 720048b861bfb208489a62340efca28ae88d1951
ms.contentlocale: pt-br
ms.lasthandoff: 04/22/2017

---
# <a name="what39s-new-in-visual-studio-2017"></a>Novidades no Visual Studio 2017
Produtividade inigualável para qualquer desenvolvimento, aplicativo e plataforma. Use o Visual Studio 2017 para desenvolver aplicativos para Android, iOS, Windows, Linux, Web e nuvem. Codifique rapidamente, depure e diagnostique com facilidade, teste com frequência e faça lançamentos com confiança. Também é possível estender e personalizar o Visual Studio criando suas próprias extensões. Use o controle de versão, seja ágil e colabore de maneira eficiente com esse novo lançamento!

> [!NOTE]
> Para obter uma lista completa dos novos recursos e das novas funcionalidades do Visual Studio 2017, consulte as [Notas de versão](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes).

Aqui está um resumo de alto nível das alterações que fizemos:

* **Desempenho e produtividade**. Nós nos concentramos não apenas nas novas e modernas funcionalidades de desenvolvimento móvel, da nuvem e de área de trabalho, mas também melhoramos as experiências gerais de aquisição, desempenho e produtividade geral do desenvolvedor. O Visual Studio é iniciado mais rapidamente, é mais dinâmico e usa menos memória do que antes.
* **Princípios básicos redefinidos**. Uma nova experiência de instalação significa que é possível instalar mais rapidamente e instalar o que você deseja quando necessário. O Visual Studio é iniciado mais rapidamente, quando você deseja carregar projetos e soluções grandes ou trabalhar em pastas de código ou até mesmo em um único arquivo de código. Além disso, o Visual Studio ajuda você a manter o foco no contexto geral, especialmente para equipes que adotam o DevOps.
* **Desenvolvimento de aplicativo na nuvem com o Azure**. Um pacote interno de ferramentas do Azure que permite criar com facilidade aplicativos imediatos em nuvem da plataforma Microsoft Azure. O Visual Studio facilita a configuração, o build, a depuração, o empacotamento e a implantação de aplicativos e serviços no Azure.
* **Desenvolvimento de aplicativos móveis**. No Visual Studio 2017, é possível inovar e obter resultados rápidos com o Xamarin, que unifica seus requisitos móveis multiplataforma usando uma base de código principal e um conjunto de habilidades. Entre na era móvel com suas equipes, investimentos em tecnologia e código C# existentes para fornecer experiências para o consumidor à frente do cronograma e abaixo do orçamento. Acelere cada etapa do ciclo de vida móvel para fornecer experiências de última geração para o consumidor ou um portfólio de aplicativos de produtividade para capacitar sua força de trabalho.

Aqui estão mais detalhes sobre algumas de nossas alterações mais importantes.

## <a name="performance-improvements"></a>Melhorias de desempenho

### <a name="a-new-setup-experience"></a>Uma nova experiência de instalação  
[Baixar o Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) ou [Verificar os requisitos do sistema do Visual Studio](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)

 O Visual Studio facilita e agiliza a instalação de recursos específicos de que você precisa, quando necessário. Além disso, ele também se desinstala completamente.

 A alteração mais importante que você verá ao instalar o Visual Studio é a nova experiência de instalação. Na guia **Cargas de Trabalho**, você verá opções de instalação que estão agrupadas para representar estruturas comuns, linguagens e plataformas. Ela abrange tudo, desde o desenvolvimento de área de trabalho do .NET até o desenvolvimento de aplicativos do C++ no Windows, Linux e iOS.   

 ![Caixa de diálogo de instalação do Visual Studio 2017](../install/media/vs2017-workloads.PNG "Tela de instalação do Visual Studio 2017")

Escolha as cargas de trabalho de que você precisa e altere-as quando necessário.

Deseja escolher seus próprios componentes em vez de usar cargas de trabalho? Basta selecionar a guia **Componentes individuais** no instalador. Deseja instalar Pacotes de Idiomas sem precisar alterar também a opção de idioma do Windows? Escolha a guia **Pacotes de idiomas** do instalador.  

Para saber mais sobre a nova experiência de instalação, incluindo instruções passo a passo que explicam a instalação, consulte nossa página [Instalar o Visual Studio](../install/install-visual-studio.md).

### <a name="start-visual-studio-faster"></a>Iniciar o Visual Studio mais rápido
O novo Centro de Desempenho do Visual Studio pode ajudá-lo a otimizar o tempo de inicialização do IDE. O Centro de Desempenho lista todas as extensões e janelas de ferramentas que podem causar lentidão na inicialização do IDE. Você pode usá-lo para melhorar o desempenho de inicialização, determinando quando iniciar as extensões ou se as janelas de ferramentas serão abertas na inicialização.

### <a name="decrease-solution-load-time"></a>Diminuir o tempo de carregamento da solução
Trabalhar em soluções que contêm grandes quantidades de projetos não significa que você precisa trabalhar com todos os arquivos ou projetos de uma só vez. Agora você pode editar e depurar sem ter que aguardar o Visual Studio carregar todos os projetos. Para experimentar com projetos gerenciados, ative **Carregar Solução Leve** em Ferramentas-> Opções-> Projetos e Soluções.

  ![Caixa de diálogo Opções no Visual Studio 2017](../ide/media/vs2017ide-LightweightSolutionLoad.PNG "Visual Studio 2017 – caixa de diálogo Opções – Carga de Solução Leve")

### <a name="faster-on-demand-loading-of-extensions"></a>Carregamento sob demanda de extensões mais rápido
O Visual Studio está movendo suas extensões (e trabalhando com extensões de terceiros também) para que elas sejam carregadas sob demanda, em vez de na inicialização do IDE. Curioso para saber quais extensões afetam a inicialização, carga de solução e desempenho de digitação? Você pode ver essas informações em Ajuda -> Gerenciar desempenho do Visual Studio.

  ![Caixa de diálogo Opções no Visual Studio 2017](../ide/media/vs2017ide-manage-vs-perf.png "Caixa de diálogo Ajuda do Visual Studio – Gerenciamento de Desempenho")

## <a name="productivity-improvements"></a>Aprimoramentos de produtividade

### <a name="sign-in-across-multiple-accounts"></a>Entrar através de várias contas  
Introduzimos um novo serviço de identidade no Visual Studio que permite compartilhar contas de usuário entre o Team Explorer, as Ferramentas do Azure, a publicação da Windows Store e muito mais.

É possível permanecer conectado por mais tempo também. O Visual Studio não solicitará um novo logon a cada 12 horas. Para obter mais informações, consulte a postagem de blog [Menos solicitações de Entrada no Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2016/08/15/fewer-visual-studio-sign-in-prompts/).

### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Gerenciar suas extensões com o Roaming Extension Manager
Agora ficou ainda mais fácil configurar cada ambiente de desenvolvimento com suas extensões favoritas ao entrar no Visual Studio. O novo Roaming Extension Manager acompanha todas as suas extensões favoritas criando uma lista sincronizada na nuvem.  

Para ver uma lista de suas extensões no Visual Studio, clique em Ferramentas > Extensões e Atualizações e, em seguida, clique em Roaming Extension Manager.

![Visual Studio 2017 – Caixa de diálogo Extensões e Atualizações](../ide/media/vs2017ide-extensions-and-updates.png "Visual Studio 2017 – Ferramentas > Caixa de diálogo Extensões e Atualizações")

O Roaming Extension Manager rastreia todas as extensões instaladas, mas você pode escolher quais você deseja adicionar à lista de Roaming.

![Visual Studio 2017 – Caixa de diálogo Extensões e Atualizações](../ide/media/vs2017ide-RoamingExtensionManager.png "Visual Studio 2017 – Roaming Extension Manager")

Ao usar o Roaming Extension Manager, você perceberá 3 tipos de ícones em sua lista:
* ![Ícone de Roaming](../ide/media/vs2017ide-roamedicon.png "Ícone de Roaming") ***Roaming***: uma extensão que faz parte dessa Lista de Roaming, mas que não está instalada no computador.
  (Você pode instalá-las usando o botão **Download**).
* ![Ícone de Roaming e Instalado](../ide/media/vs2017ide-roamedinstalledicon.png "Ícone de Roaming e Instalado") ***Roaming e Instalado***: todas as extensões que fazem parte dessa Lista de Roaming e que estão instaladas no ambiente de desenvolvimento.
  (Se você decidir que não deseja usar perfil móvel, poderá remover essas extensões usando o botão **Parar Roaming**).
* ![Ícone de Instalado](../ide/media/vs2017ide-installedicon.png "Ícone de Instalado") ***Instalado***: todas as extensões que estão instaladas nesse ambiente, mas que não fazem parte da Lista de Roaming.
  (Você pode adicionar extensões à Lista de Roaming usando o botão **Iniciar Roaming**).

Qualquer extensão que você baixar enquanto estiver conectado será adicionada à lista como **Roaming e Instalado** e fará parte da Lista de Roaming, que fornece acesso a ela em qualquer computador.

### <a name="experience-live-architecture-dependency-validation-and-live-unit-testing"></a>Experimente validação de dependência de arquitetura em tempo real e teste de unidade em tempo real

Agora, o Visual Studio pode notificá-lo em tempo real de violações de regra de dependência de arquitetura conforme você digita o código no Editor de Código, usando diagramas de validação de dependência (também conhecidos como Diagramas de camada).

Os erros são exibidos na Lista de Erros e os rabiscos serão exibidos no editor de texto que mostra o local exato da violação. Agora há menor probabilidade de introduzir dependências indesejáveis.

![Validação da arquitetura em tempo real](../ide/media/vs2017ide-LiveArchitectureDepedendencyValidation.png "Validação de dependência de arquitetura em tempo real")

#### <a name="live-unit-testing"></a>Live Unit Testing:

No Visual Studio Enterprise 2017, o Live Unit Testing fornece resultados de teste de unidade dinâmicos e a cobertura de código no editor durante a codificação. Ele funciona com projetos do C# e Visual Basic para o .NET Framework e dá suporte a três estruturas de teste do MSTest, xUnit e NUnit.

![Live Unit Testing](../ide/media/lut-codewindow.png "Um exemplo de nosso novo recurso Live Unit Testing na edição Enterprise do Visual Studio")

Para obter mais informações, consulte a postagem de blog [Live Unit Testing no Visual Studio 2017 Enterprise](https://blogs.msdn.microsoft.com/visualstudio/2017/03/09/live-unit-testing-in-visual-studio-2017-enterprise/).

### <a name="devops"></a>DevOps
#### <a name="redgate-data-tools"></a>Redgate Data Tools:
Para estender os recursos de DevOps para o desenvolvimento do banco de dados do SQL Server, as Redgate Data Tools agora estão disponíveis nas seguintes edições do Visual Studio 2017.

Incluído no Visual Studio 2017 Enterprise:
- O [Redgate ReadyRoll Core](http://www.red-gate.com/products/sql-development/readyroll/entrypage/microsoft-and-readyroll?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs) ajuda você a desenvolver scripts de migração, gerenciar alterações no banco de dados usando o controle do código-fonte e automatizar com segurança as implantações de alterações no banco de dados do SQL Server, juntamente com alterações de aplicativos.
- O [Redgate SQL Prompt Core](http://www.red-gate.com/products/sql-development/sql-prompt/entrypage/microsoft-and-sql-prompt?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs) ajuda você a gravar o SQL com maior rapidez e precisão com a ajuda do preenchimento inteligente de código. O SQL Prompt preenche automaticamente palavras-chave e objetos do sistema e do banco de dados, e oferece uma coluna de sugestões conforme você digita. Isso resulta em um código mais simples e em menos erros porque você não tem que se lembrar de cada alias ou nome de coluna.

Incluído em todas as edições do Visual Studio 2017:
- O [Redgate SQL Search](http://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs) aumenta a produtividade, ajudando-o a localizar rapidamente fragmentos de SQL e objetos em vários bancos de dados.

Para obter mais informações, consulte nossa postagem de blog [Redgate Data Tools no Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudio/2017/03/07/redgate-data-tools-in-visual-studio-2017/).

### <a name="visual-studio-ide-enhancements"></a>Aprimoramentos no IDE do Visual Studio
#### <a name="interact-with-git"></a>Interagir com o Git:
Quando estiver trabalhando com um projeto no Visual Studio, é possível configurar, confirmar rapidamente e publicar o código em um serviço Git. Também é possível gerenciar os repositórios Git usando o menu e cliques de botões no canto direito inferior do IDE.

![Caixa de diálogo Interagir com o Git do Visual Studio 2017](../ide/media/vsIDE-GitInteraction.png "Ferramentas do Git no IDE do Visual Studio")

#### <a name="view-and-navigate-code-with-structure-visualizer"></a>Exibir e navegar no código com o Visualizador de Estrutura:
O Visualizador de Estrutura desenha linhas guia de estrutura (também conhecidas como guias de recuo) no código. É possível usá-las para visualizar e descobrir em qual bloco de código você está a qualquer momento sem a necessidade de rolagem. Focalizar as linhas mostra as dicas de ferramentas que permitem a abertura desse bloco e de seus pais. Esse recurso está disponível para todas as linguagens com suporte por meio de gramáticas TextMate, bem como C#, Visual Basic e XAML.

![Visualizador de estrutura do Visual Studio 2017](../ide/media/vsIDE-StructureVisualizer.png "Visualizador de estrutura no Visual Studio")

#### <a name="experience-improved-navigation-controls"></a>Melhoria da experiência de controles de navegação:
Atualizamos a experiência de navegação para ajudá-lo a chegar de um lugar a outro com mais confiança e menos distrações.

* **Ir Para** (Ctrl+F12) &ndash; navegue de qualquer tipo base ou membro para suas várias implementações.

* **Ir Para Todos** (Ctrl+T ou Ctrl+,) &ndash; navegue diretamente para qualquer declaração de arquivo/tipo/membro/símbolo. É possível filtrar a lista de resultados ou usar a sintaxe de consulta (por exemplo, “f searchTerm” para arquivos, “t searchTerm” para tipos, etc.).

 ![Melhoria de Ir Para Todos](../ide/media/vs2017ide-navigation-go-to.png "Melhoria do recurso Ir Para Todos")

* **Localizar Todas as Referências (Shift+F12)** &ndash; com a coloração de sintaxe, é possível agrupar os resultados de Localizar Todas as Referências com uma combinação de projeto, definição e caminho. Também é possível “bloquear” os resultados para que você possa continuar encontrando outras referências sem perder os resultados originais.

 ![Nova ferramenta Localizar Todas as Referências](../ide/media/vs2017ide-find-all-references.png "Exemplo da nova ferramenta Localizar Todas as Referências")

* **Guias de Recuo** &ndash; as linhas verticais cinzas pontilhadas atuam como pontos de referência no código para fornecer o contexto no quadro de visão. É possível reconhecê-las nas populares Productivity Power Tools.

Para obter mais informações sobre nossos novos recursos de produtividade, consulte a postagem de blog [Produtividade no Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudio/2016/11/28/productivity-in-visual-studio-2017-rc/) de Mark Wilson-Thomas.

### <a name="visual-c"></a>Visual C++
Você verá diversas melhorias no Visual Studio, como a distribuição de Diretrizes do C++ Core com o Visual Studio, atualização do compilador com a adição de suporte avançado para recursos do C++ 11 e C++, além da adição e atualização de funcionalidades nas bibliotecas C++. Também melhoramos o desempenho do IDE do C++, as cargas de trabalho de instalação e muito mais.

Além disso, corrigimos mais de 250 bugs e problemas relatados no compilador e nas ferramentas, muitos deles enviados pelos clientes por meio do [Microsoft Connect](https://connect.microsoft.com/VisualStudio "Microsoft Connect").

Para obter detalhes completos, consulte nossa página [Novidades do Visual C++ no Visual 2017](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio).  

### <a name="debugging-and-diagnostics"></a>Depuração e Diagnóstico

#### <a name="run-to-click"></a>Executar com um Clique:

Agora, é possível avançar com mais facilidade durante a depuração, sem configurar um ponto de interrupção para parar na linha desejada. Quando estiver parado no depurador, basta clicar no ícone exibido ao lado da linha de código que o mouse está focalizando. O código será executado e parará nessa linha na próxima vez que for acessado no caminho do código.

![Depuração do Visual Studio 2017 – Executar com um Clique](../ide/media/vs2017ide-RunToClick.png "Executar com um Clique na depuração e no diagnóstico do Visual Studio")

#### <a name="the-new-exception-helper"></a>O novo Auxiliar de Exceção:

O novo Auxiliar de Exceção ajuda você a exibir as informações de exceção rapidamente. As informações são apresentadas em um formato compacto, com acesso instantâneo às exceções internas. Ao diagnosticar uma NullReferenceException, é possível ver rapidamente o que era nulo diretamente dentro do Auxiliar de Exceção.

![A nova caixa de diálogo Auxiliar de Exceção no Visual Studio](../ide/media/vs2017ide-ExceptionHelper.png "A nova caixa de diálogo Auxiliar de Exceção")

Para obter mais informações, consulte a postagem de blog [Usando o novo Auxiliar de Exceção no Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/).

## <a name="talk-to-us"></a>Fale conosco  
 Por que enviar comentários à equipe do Visual Studio? Porque nós levamos a sério os comentários dos clientes. Orienta muito do que fazemos.  

Se você quiser fazer sugestões sobre como podemos aprimorar o Visual Studio ou relatar um problema, confira a página [Fale conosco](../ide/talk-to-us.md) para obter mais detalhes.  

### <a name="report-a-problem"></a>Relatar um problema  
 Às vezes, uma mensagem não é suficiente para transmitir o impacto total de um problema que você encontrou. Se você tiver um travamento, uma falha ou outro problema de desempenho, você poderá compartilhar facilmente conosco as etapas de reprodução e os arquivos de suporte (como capturas de tela e arquivos de rastreamento e arquivos de despejo com heap) usando a ferramenta **Relatar um Problema**. Para obter mais informações sobre como usar essa ferramenta, consulte a página [Como relatar um problema](how-to-report-a-problem-with-visual-studio-2017.md).  

### <a name="track-your-issue-in-connect"></a>Acompanhar seu problema no Connect  
 Se você quiser acompanhar o status de seus comentários do Visual Studio, basta ir até o [Connect](http://connect.microsoft.com/) e reportar o bug lá. Depois que você reportar, é possível retornar ao Connect para acompanhar o status.  

## <a name="see-also"></a>Consulte também  
* [Novidades no Visual C++](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [Novidades no C#](https://docs.microsoft.com/en-us/dotnet/articles/csharp/csharp-7)  
* [Novidades para o Team Foundation Server](https://www.visualstudio.com/en-us/docs/whats-new)
* [Notas de Versão do Visual Studio](https://www.visualstudio.com/news/vs2015-vs)

