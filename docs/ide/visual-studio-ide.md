---
title: IDE do Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/17/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 772b6cf4-cee5-42d0-bc18-b4eb07e22ff0
caps.latest.revision: 35
author: kempb
ms.author: kempb
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
translationtype: Human Translation
ms.sourcegitcommit: c8f031247985fa623e23d79a7614330e78196024
ms.openlocfilehash: 22da86b2a327db88ac5c863f528eaeaf8b000db7

---
# <a name="visual-studio-ide"></a>Visual Studio IDE
O Microsoft Visual Studio 2017 RC é um pacote de ferramentas de criação de software que abrange desde a fase de planejamento até o design da interface do usuário, a codificação, o teste, a depuração, a análise da qualidade e do desempenho do código, a implantação nos clientes e a coleta de telemetria da utilização. Essas ferramentas foram projetadas para funcionar em conjunto da maneira mais perfeita possível e são todas expostas por meio do Ambiente de Desenvolvimento Integrado (IDE) do Visual Studio.  

 Você pode usar o Visual Studio para criar vários tipos de aplicativos, desde aplicativos simples de armazenamento e jogos para clientes móveis, até sistemas grandes e complexos que movimentam empresas e data centers. Você pode criar  

 - aplicativos e jogos que são executados não somente no Windows, mas também no Android e no iOS.

 - sites e serviços Web com base em ASP.NET, JQuery, AngularJS e outras estruturas populares.

 - aplicativos para plataformas e dispositivos tão diversos quanto: Azure, Office, Sharepoint, Hololens, Kinect e Internet das Coisas, para citar apenas alguns exemplos.

 - jogos e aplicativos de uso intensivo de gráficos para uma variedade de dispositivos Windows, incluindo o Xbox, usando o DirectX.


 O Visual Studio fornece, por padrão, suporte para C#, C e C++, JavaScript, TypeScript, F# e Visual Basic. O Visual Studio funciona e se integra bem com o Xamarin por meio do [Xamarin para Visual Studio](https://www.xamarin.com/visual-studio) e com aplicativos de terceiros como o Unity por meio da extensão [Ferramentas do Visual Studio para Unity](../cross-platform/visual-studio-tools-for-unity.md) e com o Apache Cordova por meio das [Ferramentas do Visual Studio para Apache Cordova](../misc/get-started-with-visual-studio-tools-for-apache-cordova2.md). Você pode estender o Visual Studio, criando ferramentas personalizadas que realizem tarefas especializadas com o [SDK do Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="find-out-whats-new"></a>Descubra as novidades
 Se você nunca usou o Visual Studio, conheça os fundamentos, começando com a [Introdução ao Visual Studio](../ide/get-started-with-visual-studio.md).
Se você quiser saber sobre as novas funcionalidades no Visual Studio 2017 RC, consulte [Novidades no Visual Studio 2017 RC](../ide/whats-new-in-visual-studio.md).

## <a name="set-up-visual-studio"></a>Configurar o Visual Studio
 Você pode descobrir qual edição do Visual Studio é adequada para você em [Produtos Visual Studio](https://www.visualstudio.com/products/).

 Você pode instalar o Visual Studio 2017 RC, baixando-o de [Downloads do Visual Studio](https://www.visualstudio.com/vs/). Para saber mais sobre o processo de instalação, confira [Instalando o Visual Studio 2017 RC](https://go.microsoft.com/fwlink/?linkid=833223).

## <a name="quick-tour-of-the-ide"></a>Tour rápido pelo IDE
 A imagem a seguir mostra o IDE do Visual Studio com um projeto aberto junto com várias janelas de ferramentas importantes.
 - O [Gerenciador de Soluções](../ide/solutions-and-projects-in-visual-studio.md) permite exibir e navegar em seus arquivos de código.
 - O [Team Explorer](https://www.visualstudio.com/en-us/docs/connect/work-team-explorer) permite que você controle itens de trabalho e compartilhe código com outras pessoas usando tecnologias de controle de versão como [Git](https://git-scm.com/) e [TFVC (Controle de Versão do Team Foundation)](https://www.visualstudio.com/en-us/docs/tfvc/overview).
 - O [Cloud Explorer](https://azure.microsoft.com/en-us/documentation/articles/vs-azure-tools-resources-managing-with-cloud-explorer/) permite exibir e gerenciar seus recursos do Azure, como máquinas virtuais, tabelas, bancos de dados SQL e muito mais.
 - A janela [Editor](../ide/writing-code-in-the-code-and-text-editor.md) permite que você exiba e edite o código-fonte e os dados de designer.
 - A janela [Saída](../ide/reference/output-window.md) exibe a saída da compilação, execução, depuração e muito mais.


 ![IDE do Visual Studio](../ide/media/visualstudioide.png "VisualStudioIDE")  

 ### <a name="sign-in"></a>Entrar
  Ao iniciar o Visual Studio pela primeira vez, você pode entrar usando sua conta da Microsoft ou sua conta corporativa ou de estudante. Ao entrar você estará habilitado para sincronizar suas configurações, como layouts de janela, entre vários dispositivos e conectar-se automaticamente aos serviços que precisar, como as assinaturas do Azure e o Visual Studio Team Services. Se você tiver uma licença baseada em assinatura, será necessário entrar no Visual Studio regularmente para manter seu token de licença atualizado. Se você tiver uma licença de chave do produto (Product Key), não será necessário entrar, mas se você o fizer será muito mais conveniente para conectar-se ao Visual Studio Team Services e às suas contas com o Azure, Office 365 e Salesforce.com. Para obter mais informações, consulte [Entrando no Visual Studio](../ide/signing-in-to-visual-studio.md).

  Se você tiver várias contas do Visual Studio Team Services, várias contas do Azure ou várias assinaturas do MSDN, poderá vinculá-las e acessar recursos e serviços em todas as suas contas com um logon único. Para obter mais informações, consulte [Trabalhar com várias contas de usuário](../ide/work-with-multiple-user-accounts.md).

 ### <a name="stay-up-to-date"></a>Mantenha-se atualizado
  O ícone de sinalizador de notificação no canto superior da barra de título informa quando as atualizações estão disponíveis para o Visual Studio ou para qualquer componente relacionado que você instalou. Você pode optar por descartar ou tomar ação em relação a essas notificações. Para obter mais informações, consulte [Notificações do Visual Studio](../ide/visual-studio-notifications.md).

 ### <a name="find-things-and-get-help"></a>Encontre as coisas e obter ajuda
  A janela [Início Rápido](../ide/reference/quick-launch-environment-options-dialog-box.md), contornada em vermelho na captura de tela a seguir, é uma maneira rápida para localizar comandos, ferramentas e recursos do Visual Studio e assim por diante quando você não souber o atalho de teclado ou a localização no menu. Basta digitar o que você está procurando e o Início Rápido lhe dará um link para a informação.

 ![Resultados de Início Rápido para 'novo projeto'](../ide/media/Productivity_QuickLaunch.png "Productivity_QuickLaunch")

 No Visual Studio, você pode pressionar **F1** para ir para a Ajuda online da janela ativa. Você também pode pressionar **F1** no editor de código para ir para a página de ajuda da API ou da palavra-chave na posição atual do cursor do sistema. Por exemplo, em um arquivo C#, coloque o cursor do sistema em algum lugar ou no final de uma declaração `System.String` e pressione **F1** para ir para a página de ajuda da [Cadeia de caracteres](assetId:///T:System.String?qualifyHint=False&autoUpgrade=True).

### <a name="give-feedback"></a>Enviar comentários
 É fácil fornecer comentários sobre o Visual Studio sempre que você quiser. Clique no ícone de comentários na barra de título ao lado de **QuickLaunch** e, em seguida, clique em **Relatar um problema** ou **Fornecer uma sugestão**.

![Enviar comentários](../ide/media/VSIDE_reportproblem.png)

 Edições de pré-lançamento do Visual Studio também tem uma opção **Classificar este Produto**. Examinamos todos esses comentários e usamos para aprimorar o produto. Para obter mais informações, consulte [Fale conosco](../ide/talk-to-us.md).

### <a name="personalize-the-ide"></a>Personalizar o IDE
 Você pode personalizar o layout da janela de acordo com seu estilo de desenvolvimento. Você pode encaixar, deixar flutuante ou ocultar qualquer janela a qualquer momento e também pode executar o editor no modo de tela inteira. Você pode criar e salvar vários layouts de janela personalizados que mostram apenas as janelas necessárias para contextos específicos. Por exemplo, é possível criar um layout de tela inteira para ver apenas o editor de código. E você pode criar layouts diferentes para depuração e para operações de equipe. Para obter mais informações, consulte [Personalizando layouts de janela](../ide/customizing-window-layouts-in-visual-studio.md).

 Você poderá personalizar o Visual Studio de muitas outras formas e usar perfil móvel das configurações se você trabalhar em vários computadores. Para obter mais informações, confira [Personalizando o IDE](../ide/personalizing-the-visual-studio-ide.md).

 Existem atalhos de teclado para quase tudo e também é possível personalizá-los. Para criar novos atalhos, digite "Teclado" em Início Rápido para abrir a caixa de diálogo Teclado. A partir daí, você poderá pressionar F1 para ir para a página de ajuda se precisar de mais informações sobre as opções. Para obter mais informações, consulte [Atalhos de teclado padrão no Visual Studio](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="connect-to-visual-studio-team-services-and-team-foundation-server"></a>Conectar-se ao Visual Studio Team Services e ao Team Foundation Server
  O VSTS (Visual Studio Team Services) é um serviço baseado em nuvem para hospedagem de projetos de software e para habilitar a colaboração nas equipes. O VSTS oferece suporte a sistemas Git e Team Foundation Source Control, bem como as metodologias de desenvolvimento Agile, CMMI e Scrum. O TFVC (Controle de Versão do Team Foundation) usa um repositório de servidor único e centralizado para arquivos de versão e de controle. É sempre feito check-in das alterações locais no servidor central em que outros desenvolvedores podem obter as alterações mais recentes. O TFS (Team Foundation Server) 2015 é o hub de gerenciamento do ciclo de vida do aplicativo para o Visual Studio. Ele habilita a participação de todos os envolvidos com o processo de desenvolvimento usando uma única solução. O TFS também é útil para gerenciar equipes e projetos heterogêneos.

  Se você tiver uma conta do Visual Studio Team Services ou um Team Foundation Server em sua rede, será possível conectar-se a eles através da janela do Team Explorer. Nessa janela você pode fazer check-in ou check-out de código no controle do código-fonte, gerenciar itens de trabalho, iniciar compilações e acessar salas da equipe e espaços de trabalho. Você pode abrir o Team Explorer no **Início Rápido** ou no menu principal, em **Exibir, Team Explorer** ou **Equipe, Gerenciar Conexões**.  Para obter mais informações sobre o Visual Studio Team Services, consulte [www.visualstudio.com](https://www.visualstudio.com/). Para obter mais informações sobre o Team Foundation Server, consulte [Team Foundation Server](https://www.visualstudio.com/products/tfs-overview-vs).

  A imagem a seguir mostra o painel do Team Explorer para uma solução que é hospedada no VSTS:

 ![Team Explorer para Visual Studio](../ide/media/vs2017_teamexplorer.png "VS2017_TeamExplorer")  

## <a name="create-solutions-and-projects"></a>Criar soluções e projetos
  Embora você possa usar o Visual Studio para procurar arquivos de código individuais, é mais comum que você esteja trabalhando em um *Projeto*. Um projeto do Visual Studio é uma coleção de arquivos e recursos que são compilados em um arquivo executável binário único para aplicativos (por exemplo, um .exe, DLL ou appx). Para sites que não são de ASP.NET, nenhum executável é produzido e o projeto contém apenas o HTML, os arquivos JavaScript e as imagens. Como você pode precisar criar vários binários ou sites que estão bastante relacionados algumas vezes, o Visual Studio tem o conceito de Solução, que pode conter vários projetos ou sites. Quando você cria um projeto, na verdade está criando um projeto em uma solução e depois você pode adicionar mais projetos a essa solução se precisar. Por exemplo, se você tiver um projeto de DLL, você poderá adicionar um projeto .exe à solução que carrega e consome a DLL.

  Um *modelo de projeto* é uma coleção de arquivos de código e definições de configuração previamente preenchidos que você configura rapidamente para criar um tipo específico de aplicativo. O Visual Studio vem com muitos modelos de projeto para escolher e se nenhum dos modelos padrão funcionar pra você, é possível criar os seus próprios modelos. Depois de criar um projeto com um modelo, você pode começar a escrever seu próprio código nele, seja nos arquivos fornecidos ou em novos arquivos adicionados. Para obter mais informações, consulte [Soluções e projetos](../ide/solutions-and-projects-in-visual-studio.md). A ilustração a seguir mostra a caixa de diálogo Novo Projeto com os modelos de projeto que estão disponíveis para aplicativos ASP.NET.

 ![Caixa de diálogo Novo Projeto do Visual Studio](../ide/media/vs2017_newprojectdialog.png "VS2017_NewProjectDialog")  

## <a name="write-navigate-and-understand-code"></a>Escrever, navegar e compreender o código  
 Se você é um desenvolvedor, a janela do editor é o lugar em que você provavelmente passa a maior parte do tempo. O Visual Studio inclui suporte interno de edição para C#, C++, Visual Basic, F#, JavaScript, TypeScript, XML, HTML e CSS. O Visual Studio também oferece suporte à edição e compilação de muitas outras linguagens.

 Você pode editar os arquivos individuais no editor de texto, escolhendo **Arquivos, Abrir, Arquivo**. Para editar arquivos em um projeto aberto, escolha e abra o nome do arquivo no Gerenciador de Soluções. O código é colorizado e você pode personalizar o esquema de cores digitando "Cores" no Início Rápido. Você pode ter várias janelas do editor de texto com guias abertas ao mesmo tempo. Você pode dividir cada janela de forma independente. Também é possível executar o editor de texto no modo de tela inteira.  

 ![O código no editor de código](../ide/media/codewindow.png "Editor de código")  

 O editor de texto é altamente interativo (se desejar que ele seja assim), com muitos recursos de produtividade que ajudarão a escrever códigos mais rapidamente. Os recursos variam por linguagem e você não precisa usar nenhum deles. Digite "Editor" no Início Rápido para ativar ou desativar recursos. Alguns dos recursos de produtividade comuns são:  

-  [Refatoração](../ide/refactoring-in-visual-studio.md) inclui operações como renomeação inteligente de variáveis, mover linhas de código selecionadas para uma função distinta, mover o código para outros locais, reordenação de parâmetros de função e muito mais.

  ![Refatoração](../ide/media/VSIDE_refactor.png)  

-  **IntelliSense** é um termo abrangente para um conjunto de recursos populares que exibe informações de tipo sobre seu código diretamente no editor e, em alguns casos, escreve pequenos pedaços de código pra você. É como ter a documentação básica embutida no editor, o que evita que você tenha que consultar informações de tipo em uma janela de ajuda separada. Os recursos do IntelliSense variam de acordo com a linguagem. Para obter mais informações, consulte [IntelliSense do Visual C#](../ide/visual-csharp-intellisense.md), [IntelliSense do Visual C++](../ide/visual-cpp-intellisense.md), [IntelliSense do JavaScript](../ide/javascript-intellisense.md), [IntelliSense específico do Visual Basic](../ide/visual-basic-specific-intellisense.md). A ilustração a seguir mostra alguns recursos do IntelliSense em funcionamento:  

     ![Lista de membros do Visual Studio](../ide/media/vs2017_Intellisense.png "vs2017_Intellisense")  

-  **Rabiscos** alerta sobre erros ou problemas potenciais em seu código em tempo real, enquanto você digita, permitindo que você corrija imediatamente sem esperar que o erro seja descoberto durante o momento da compilação ou da execução. Se você passar o mouse sobre o rabisco, verá informações adicionais sobre o erro. Uma lâmpada também podem aparecer na margem esquerda com sugestões de como corrigir o erro. Para obter mais informações, consulte [Realizar ações rápidas com lâmpadas](../ide/perform-quick-actions-with-light-bulbs.md).  

  ![Rabiscos](../ide/media/vs2017_squiggle.png "VS2017_Squiggles")  

-  [Indicadores](../ide/setting-bookmarks-in-code.md) permitem que você navegue rapidamente até linhas específicas nos arquivos em que você está trabalhando ativamente.

    ![Janela de indicadores](../ide/media/VSIDE_bookmarks.png)

-  A janela [Hierarquia de Chamada](../ide/reference/call-hierarchy.md) pode ser invocada no menu de contexto do editor de texto para mostrar os métodos que chamam e são chamados pelo método sob o cursor.

    ![Janela de Hierarquia de Chamada](../ide/media/VSIDE_call_hierarchy.png)

-  **CodeLens** habilita a localizar referências e alterações em seu código, bugs vinculados, itens de trabalho, análises de código e testes de unidade, tudo sem sair do editor.

    ![CodeLens](../ide/media/codelensoverview.png)

  Para obter mais informações, consulte [Localizar alterações de código e outros históricos](../ide/find-code-changes-and-other-history-with-codelens.md).  

-  A janela **Espiar Definição** mostra uma definição de método ou de tipo embutida, sem navegar para fora de seu contexto atual. Agora esta janela funciona também para XAML.  

    ![Espiar Definição](../ide/media/VSIDE_peek_definition.png)

-  A opção de menu de contexto **Ir para Definição** leva você diretamente para o local em que a função ou o objeto estão definidos. Outros comandos de navegação também estão disponíveis clicando com o botão direito do mouse no editor.

    ![Ir para Definição](../ide/media/VSIDE_go_to_definition.png)

- Uma ferramenta relacionada, o [Pesquisador de Objetos](http://msdn.microsoft.com/en-us/f89acfc5-1152-413d-9f56-3dc16e3f0470), habilita a inspeção de assemblies de .NET ou de Windows Runtime em seu sistema para ver que tipos eles contêm e quais métodos e propriedades esses tipos contêm.  

     ![Pesquisador de Objetos mostrando System.Timer](../ide/media/objectbrowser.png "ObjectBrowser")  

 A maioria dos itens no menu Editar e no menu Exibir está relacionada ao editor de códigos de alguma forma. Para obter mais informações sobre o editor, consulte [Escrevendo código](../ide/writing-code-in-the-code-and-text-editor.md) e [Editando seu código](https://www.visualstudio.com/features/ide-vs).  

## <a name="compile-and-build-your-code"></a>Compilar e criar seu código  
 Criar um projeto significa para compilar o código-fonte e executar todas as etapas necessárias para produzir o executável. Linguagens diferentes têm operações de build diferentes e sites regulares não compilam. Independentemente do tipo de projeto, o menu **Compilar** é o local padrão para estes comandos. Para compilar e executar seu código com um único pressionamento de teclas, pressione a tecla F5. Todo compilador é completamente configurável por meio do IDE. A barra de ferramentas Compilar permite que você especifique se deseja criar uma versão de depuração do seu programa, com símbolos e verificação de erros adicionais habilitados para dar suporte a pontos de interrupção e passo a passo no depurador ou um build de lançamento, que é o que você finalmente entregará aos usuários. Você pode configurar mais definições de build e muitas outras configurações na página de propriedades de um projeto. Escolha o menu de contexto (clique com o botão direito do mouse) do nó do projeto no Gerenciador de Soluções e, em seguida, escolha o comando Propriedades. Você também pode executar compilações da linha de comando.  

 A saída do build, incluindo mensagens de erro ou sucesso, aparece na Janela de Saída. A Lista de Erros (mostrada abaixo) fornece informações detalhadas sobre erros de build.  

 ![Lista de Erros mostrando o erro do compilador C&#35;](../ide/media/VS2017_errorlist.png "VS2017_error_list")  

## <a name="debug-your-code"></a>Depurar seu código  
 O depurador de ponta do Visual Studio permite que você depure o código em execução em seu projeto local, em um dispositivo remoto ou em um emulador, como aqueles para os dispositivos Android ou Windows Phone. Você pode percorrer o código em uma declaração por vez e inspecionar variáveis à medida que avança, você pode percorrer aplicativos com multithread e pode definir pontos de interrupção que são atingidos somente quando uma condição especificada for verdadeira. Você pode monitorar os valores de variáveis enquanto o código é executado. Tudo isso pode ser gerenciado no próprio editor de código, para que você não tenha que deixar o contexto do seu código.  

 ![Janela de inspeção de configurações do ponto de interrupção](../ide/media/dbg_breakpoints_peekwindow.png "DBG_Breakpoints_PeekWindow")  

 O próprio depurador tem várias janelas que permitem que você exiba e manipule variáveis locais, a pilha de chamadas e outros aspectos do ambiente de tempo de execução. Você pode encontrar essas janelas no menu **Depurar**.  

 A [Janela Imediata](../ide/reference/immediate-window.md) permite a digitação de uma expressão e a visualização imediada de seu resultado.

![Janela imediata](../ide/media/VSIDE_immediate_window.png)

 A janela [IntelliTrace](../debugger/intellitrace.md) registra cada chamada de método e outros eventos em um programa .NET em execução e pode ajudar a localizar rapidamente a origem de um problema.

 Para obter mais informações, consulte [Depuração no Visual Studio](../debugger/debugging-in-visual-studio.md).  

## <a name="test-your-code"></a>Testar seu código  
 O Visual Studio inclui uma estrutura de teste de unidade para código gerenciado (.NET) e outra para o C++ nativo. Para criar testes de unidade é só adicionar um Projeto de Teste à sua solução, escrever seus testes e, em seguida, executá-los na janela Gerenciador de Testes. Para obter mais informações, consulte [Efetuar teste de unidade em seu código](../test/unit-test-your-code.md).  

 ![Gerenciador de testes de unidade](../ide/media/ute_failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")  

## <a name="analyze-code-quality-and-performance"></a>Analisar o desempenho e a qualidade do código  
 O Visual Studio inclui ferramentas avançadas para análise estática e em tempo de execução. As ferramentas de análise estática ajudam a identificar possíveis erros no design, na globalização, na interoperabilidade, no desempenho, na segurança e em outras categorias. O teste de desempenho ou criação de perfil envolve a medição de como o seu programa é executado. Acesse essas ferramentas no menu **Analisar**. Para obter mais informações, consulte [Melhorando a qualidade com as ferramentas de diagnóstico do Visual Studio](../test/improve-code-quality.md).  

## <a name="connect-to-cloud-services-and-databases"></a>Conectar-se aos serviços de nuvem e bancos de dados  
 O [Cloud Explorer](https://azure.microsoft.com/en-us/documentation/articles/vs-azure-tools-resources-managing-with-cloud-explorer/) no Visual Studio mostra os recursos do Azure em todas as contas gerenciadas na assinatura do Azure em que você está conectado. Você pode obter o Cloud Explorer instalando o [SDK do Azure](https://azure.microsoft.com/en-us/downloads/).


 ![Cloud Explorer](../ide/media/VSIDE_CloudExplorer.png)

 O [Gerenciador de Servidores](https://msdn.microsoft.com/en-us/library/cd2cz7yy.aspx) também está disponível para ajudá-lo a navegar e gerenciar instâncias e ativos do SQL Server no Azure, no Salesforce.com, no Office 365 e em sites.

 O Visual Studio inclui o [SSDT](https://msdn.microsoft.com/en-us/data/tools.aspx) (Microsoft SQL Server Data Tools), que permite você criar, depurar, manter e refatorar bancos de dados. Você pode trabalhar com um projeto de banco de dados ou diretamente com uma instância local ou não de banco de dados conectado.  

 O [Pesquisador de Objetos do SQL Server](https://msdn.microsoft.com/en-us/library/hh231250.aspx) no Visual Studio oferece uma exibição de seus objetos de banco de dados semelhante ao SQL Server Management Studio. O Pesquisador de Objetos do SQL Server permite que você realize tarefas de administração e design leves de banco de dados, incluindo edição de dados de tabela, comparação de esquemas e execução de consultas usando menus contextuais diretamente do Pesquisador de Objetos do SQL Server. O SSDT também inclui tipos de projetos e ferramentas especiais para desenvolvimento de soluções de BI (Business Intelligence) do SQL Server 2012 Analysis Services, Reporting Services e Integration Services (anteriormente conhecidas como Business Intelligence Development Studio).  

 ![Pesquisador de objetos do SQL Server](../ide/media/vs2015_sqlobjectexplorer.png "vs2015_SQLObjectExplorer")  

## <a name="deploy-your-finished-application"></a>Implantar o aplicativo concluído  
 Quando seu aplicativo está pronto ser implantado para os clientes, o Visual Studio fornece as ferramentas para fazer isso, não importa se você está implantando na Windows Store, em um site do SharePoint ou com tecnologias InstallShield ou o Windows Installer. Tudo isso está acessível por meio do IDE. Para obter mais informações, consulte [Implantação de aplicativos, serviços e componentes](../deployment/deploying-applications-services-and-components.md).  

## <a name="architecture-and-modeling-tools-enterprise-only"></a>Ferramentas de arquitetura e modelagem (somente Enterprise)  
 Você pode usar as ferramentas de arquitetura e modelagem do Visual Studio para projetar e modelar seu aplicativo. Essas ferramentas ajudam a visualizar a estrutura, o comportamento e as relações do código. Você pode criar modelos em diferentes níveis de detalhe em todo o ciclo de vida do aplicativo como parte do processo de desenvolvimento. Você pode controlar os requisitos, as tarefas, os casos de teste, os bugs e outros trabalhos associados com seus modelos vinculando os elementos de modelo a itens de trabalho do Team Foundation Server e ao plano de desenvolvimento. Para obter mais informações, consulte [Criar design e modelar seu aplicativo](../modeling/analyze-and-model-your-architecture.md).  

## <a name="extend-visual-studio-through-the-visual-studio-sdk"></a>Estender o Visual Studio por meio do SDK do Visual Studio  
 O Visual Studio é uma plataforma extensível. Uma extensão do Visual Studio é uma ferramenta personalizada que se integra com o IDE. Você pode adicionar extensões de terceiros ou criar suas próprias extensões. Para obter mais informações, consulte [Começar a desenvolver extensões do Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  

 As [Diretrizes de experiência de usuário do Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md) são uma referência essencial para qualquer pessoa que deseja escrever extensões para o Visual Studio. Essas diretrizes específicas da plataforma incluem informações sobre design, fontes, cores, ícones, controles comuns e outros padrões de interação de caixa de diálogo que farão com que seu novo recurso se integre de maneira perfeita com o Visual Studio.  

## <a name="see-also"></a>Consulte também  
 [Instalando o Visual Studio 2017 RC](../install/install-visual-studio.md)   
 [Editando o seu código](https://www.visualstudio.com/features/ide-vs)   
 [Novidades no Visual Studio 2017 RC](../ide/whats-new-in-visual-studio.md)   
 [Portabilidade, migração e atualização de projetos do Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)   
 [Fale conosco](../ide/talk-to-us.md)



<!--HONumber=Feb17_HO4-->


