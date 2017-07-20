---
title: Tour pelos recursos do IDE do Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 06/28/2017
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 669bc5894727c207691a7e37937f432d98fee8b1
ms.openlocfilehash: 8d2c20b32201b3df85e5150828565eee84d66375
ms.contentlocale: pt-br
ms.lasthandoff: 06/30/2017

---
# <a name="visual-studio-ide-feature-tour"></a>Tour pelos recursos do IDE do Visual Studio
Este tópico apresenta os recursos do IDE do Visual Studio. O IDE do Visual Studio é um IDE (ambiente de desenvolvimento interativo); um painel de inicialização criativa que pode ser usado para exibir e editar quase todo tipo de código e, em seguida, depurar, compilar e publicar aplicativos para o Android, iOS, Windows, a Web e a nuvem. Há versões disponíveis para o Mac e Windows. Vamos examinar algumas coisas que você pode fazer com o Visual Studio e como instalá-lo e usá-lo, abordar a criação de um projeto simples, obter ponteiros no código de depuração e implantação e conhecer as várias janelas de ferramentas.

## <a name="what-can-you-do-with-the-visual-studio-ide"></a>O que pode ser feito com o IDE do Visual Studio?
Você deseja criar um aplicativo para um telefone Android? Você pode fazer isso. E quanto à criação de um jogo de última geração com o C++? É possível fazer isso e muito, muito mais. O Visual Studio fornece modelos que ajudam você a criar sites, jogos, aplicativos de área de trabalho, aplicativos móveis, aplicativos para o Office e muito mais.

![Projetos do Visual Studio](../ide/media/VSIDE_Tour_Projects_List.png)

Se preferir, basta abrir quase todo código obtido praticamente de qualquer lugar e começar a trabalhar. Achou um projeto no GitHub que você gostou? Basta clonar o repositório, abri-lo no Visual Studio e começar a codificá-lo!

### <a name="create-mobile-apps"></a>Criar aplicativos móveis
É possível criar aplicativos móveis nativos para diferentes plataformas usando o Visual C# e o Xamarin ou o Visual C++ ou aplicativos híbridos usando o JavaScript com o Apache Cordova. É possível escrever jogos móveis para o Unity, Unreal, DirectX, Cocos e muito mais. O Visual Studio inclui um emulador do Android para ajudá-lo a executar e depurar aplicativos Android.

É possível aproveitar o poder da nuvem para seus aplicativos móveis criando serviços de aplicativos do Azure. Os serviços de aplicativos do Azure permitem que os aplicativos armazenem dados na nuvem, autentiquem usuários com segurança e escalem ou reduzam verticalmente seus recursos de forma automática para acomodar as necessidades do aplicativo e dos negócios. Para saber mais, consulte [Desenvolvimento de aplicativos móveis](https://www.visualstudio.com/vs/mobile-app-development/).

### <a name="create-cloud-apps-for-azure"></a>Criar aplicativos na nuvem para o Azure
O Visual Studio oferece um pacote de ferramentas que permite criar aplicativos habilitados para a nuvem com facilidade da plataforma Microsoft Azure. É possível configurar, compilar, depurar, empacotar e implantar aplicativos e serviços no Microsoft Azure diretamente por meio do IDE. Aproveite os serviços do Azure em seus aplicativos usando os Serviços Conectados. Para obter as Ferramentas do Azure para .NET, selecione a carga de trabalho **desenvolvimento do Azure** ao instalar o Visual Studio. Para obter mais informações, consulte [Ferramentas do Visual Studio para o Azure](https://www.visualstudio.com/vs/azure-tools/).

### <a name="create-apps-for-the-web"></a>Criar aplicativos para a Web
A Internet impulsiona nosso mundo moderno e o Visual Studio pode ajudá-lo a escrever aplicativos para ele. É possível criar aplicativos Web usando o ASP.NET, Node.js, Python, JavaScript e TypeScript. O Visual Studio reconhece estruturas Web como Angular, jQuery, Express e muito mais. O ASP.NET Core e o .NET Core são executados nos sistemas operacionais Windows, Mac e Linux. Para obter mais informações, consulte [Ferramentas da Web modernas](https://www.visualstudio.com/vs/modern-web-tooling/).

### <a name="write-code-in-a-world-class-editing-environment"></a>Escrever um código em um ambiente de edição da mais alta qualidade
O Visual Studio ajuda você a escrever um código de forma rápida e fácil por meio de recursos, como coloração de sintaxe, preenchimento de declaração, IntelliSense (descrições pop-up do elemento de código selecionado), estrutura de tópicos do código, configuração de pontos de interrupção para depuração e muito mais.

![Exemplo de código JavaScript](../ide/media/vside_tour_javascript_example.gif)

Para saber mais, consulte [Escrevendo código no editor de código e de texto](https://docs.microsoft.com/visualstudio/ide/writing-code-in-the-code-and-text-editor).

O Visual Studio pode fazer ajudar você a fazer muito mais coisas. Para obter uma lista mais completa, consulte [IDE do Visual Studio](https://www.visualstudio.com/vs/).


## <a name="install-the-visual-studio-ide"></a>Instalar o IDE do Visual Studio
Para começar, baixe o Visual Studio e instale-o no sistema. É possível baixá-lo em [Visual Studio 2017](https://www.visualstudio.com/vs/visual-studio-2017/).

Agora o Visual Studio está mais leve do que nunca! O novo instalador modular permite escolher e instalar *cargas de trabalho*, que são grupos de recursos necessários para a linguagem de programação ou plataforma de sua preferência. Essa estratégia ajuda a manter a superfície de instalação do Visual Studio menor do que nunca, o que significa que ele é instalado e atualizado mais rapidamente também.

![Instalador do Visual Studio](../ide/media/vside_tour_install_dialog.png)

Além de um melhor desempenho de instalação, várias melhorias foram feitas no Visual Studio 2017 para melhorar o tempo de inicialização e de carregamento da solução geral do IDE. Por exemplo, a seleção do novo recurso Carga de Solução Leve, localizado no menu principal em **Ferramentas**, **Opções**, **Projetos e Soluções**, permite que soluções maiores sejam carregadas mais rapidamente. Para saber mais sobre como configurar o Visual Studio no sistema, consulte [Instalar o Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio).

## <a name="sign-in"></a>Entrar
Ao iniciar o Visual Studio pela primeira vez, opcionalmente, é possível entrar usando sua conta da Microsoft ou sua conta corporativa ou de estudante. Estar conectado permite sincronizar as configurações do Visual Studio, como layouts de janela, em vários dispositivos. Ele também o conecta automaticamente aos serviços que podem ser necessários, como as assinaturas do Azure e o Visual Studio Team Services.


## <a name="create-a-program"></a>Criar um programa

Uma boa maneira de aprender sobre algo é usá-lo! Vamos nos aprofundar e criar um novo programa simples.

1. Abra o Visual Studio. No menu, escolha **Arquivo**, **Novo**, **Projeto**. (Use os valores de projeto padrão.)

  ![captura de tela](../ide/media/VSIDE_Tour_NewProject1.png)

  Como alternativa, é possível criar um novo projeto usando a Página de Início. Para obter mais informações, consulte [Aproveite o Poder da Página Inicial Reprojetada (blog)](https://blogs.msdn.microsoft.com/visualstudio/2016/11/29/harness-the-power-of-the-redesigned-start-page/).

1. A caixa de diálogo **Novo Projeto** mostra vários modelos de projeto. Escolha a categoria **Universal do Windows** em **Visual C#**, escolha o modelo **Aplicativo em Branco (Universal do Windows)** e, em seguida, o botão **OK**.

  ![captura de tela](../ide/media/VSIDE_Tour_NewProject2.png)

  Isso cria um novo projeto de aplicativo em branco Universal do Windows usando o Visual C# e XAML como as linguagens de programação. Aguarde um pouco enquanto o Visual Studio configura o projeto para você. Se você precisar fornecer alguma informação, basta aceitar os valores padrão por enquanto.

1. Em breve, você deverá ver algo parecido com a captura de tela a seguir. Os arquivos de projeto são listados no lado direito em uma janela chamada Gerenciador de Soluções.

  ![captura de tela](../ide/media/VSIDE_Tour_NewProject3.png)

1. No Gerenciador de Soluções, escolha o pequeno triângulo preto ao lado do arquivo MainPage.xaml para expandi-lo e você deverá ver um arquivo MainPage.xaml.cs abaixo dele. Escolha esse arquivo (que contém o código C#) para abri-lo.

  O código C# em MainPage.xaml.cs é exibido no editor de código no lado esquerdo da tela. Observe que a sintaxe do código é colorizada automaticamente para indicar diferentes tipos de código, como instruções ou comentários. Além disso, pequenas linhas verticais tracejadas no código indicam a correspondência de chaves e os números de linha ajudam a localizar o código posteriormente. É possível escolher os pequenos sinais de subtração demarcados para recolher ou expandir o código. Esse recurso de estrutura de tópicos do código permite ocultar os códigos desnecessários, ajudando a minimizar a desordem na tela.

  ![](../ide/media/VSIDE_Tour_NewProject3a.png)

  Há outros menus e outras janelas de ferramentas disponíveis, mas por enquanto, vamos seguir em frente.

1. Adicione um botão ao formulário XAML para fornecer aos usuários uma maneira de interagir com seu aplicativo. Para fazer isso, abra o arquivo MainPage.xaml. Isso mostra uma exibição dividida: um designer acima, para colocar os controles visualmente e uma exibição de código abaixo, que mostra o código XAML por atrás do designer. Ao executar o programa posteriormente, o que você verá no designer se tornará uma janela que será vista pelos usuários, um “formulário” e o XAML subjacente determina o que é exibido no formulário.

1. No lado esquerdo da tela, escolha a guia **Caixa de Ferramentas** para abrir a Caixa de Ferramentas. A Caixa de Ferramentas contém diversos controles visuais que podem ser adicionados a formulários. Por enquanto, vamos apenas adicionar um controle de botão.

1. Expanda a seção **Controles XAML Comuns** e, em seguida, arraste o controle de Botão para fora até a parte central do formulário. (A localização exata não é importante.)

  ![captura de tela](../ide/media/VSIDE_Tour_Toolbox.png)

  Quando terminar, você deverá ver algo parecido com o mostrado a seguir.

  ![captura de tela](../ide/media/VSIDE_Tour_XAMLButton.png)

  O botão está no designer e seu código subjacente (realçado) é adicionado automaticamente ao código XAML do designer.

1. Vamos alterar um pouco do código XAML. Renomeie o texto no código do botão de `Button` para `Hello!`.

  ![captura de tela](../ide/media/VSIDE_Tour_XAMLButton2.png)

1. Agora, inicie o aplicativo. Faça isso escolhendo o botão **Iniciar** (![botão Iniciar](../ide/media/VSIDE_StartButton.png)) na barra de ferramentas, escolhendo a tecla F5 ou, no menu, escolhendo **Depurar**, **Iniciar Depuração**.

  ![captura de tela](../ide/media/VSIDE_Tour_RunButton.png)

  O aplicativo inicia seu processo de build e as mensagens de status são exibidas na janela de Saída. Em breve, você deverá ver o formulário exibido com o botão nele. Agora você tem um aplicativo em execução.

  ![captura de tela](../ide/media/VSIDE_Tour_RunProject.png)

  Obviamente, ele não executa muitas ações no momento, mas é possível adicionar mais funcionalidades a ele mais tarde se desejar.

1. Quando terminar de executar o programa, escolha o botão Parar (![botão Parar](../ide/media/VSIDE_StopButton.png)) na barra de ferramentas para interrompê-lo.

Vamos recapitular o que você fez até agora: você criou um novo projeto Universal do Windows do C# no Visual Studio, exibiu seu código, adicionou um controle ao designer, alterou uma parte do código XAML e, por fim, executou o projeto. Embora o processo tenha sido simplificado para este exemplo, isso mostra algumas partes comuns do IDE do Visual Studio que você usará para desenvolver seus próprios aplicativos. Se desejar obter mais detalhes sobre esse exemplo, consulte [Criar um aplicativo “Olá, mundo” (XAML)](https://docs.microsoft.com/windows/uwp/get-started/create-a-hello-world-app-xaml-universal).


## <a name="debug-test-and-improve-your-code"></a>Depurar, testar e melhorar o código
Nada acontece de forma perfeita o tempo todo. Quando você escrever o código, é necessário executá-lo e testá-lo para verificar o desempenho e se há bugs. O depurador de última geração do Visual Studio permite depurar o código em execução no projeto local, em um dispositivo remoto ou em um emulador, como aqueles para os dispositivos Android ou Windows Phone. Você pode percorrer o código em uma declaração por vez e inspecionar variáveis à medida que avança, você pode percorrer aplicativos com multithread e pode definir pontos de interrupção que são atingidos somente quando uma condição especificada for verdadeira. É possível monitorar os valores de variáveis enquanto o código é executado e muito mais. Tudo isso pode ser gerenciado no próprio editor de código, para que você não precise deixar o código.

![Depuração](../ide/media/VSIDE_Tour_Debugging.png)

Para testes, o Visual Studio oferece testes de unidade, IntelliTest, testes de carga e desempenho e muito mais. Para obter mais detalhes sobre o processo de depuração do Visual Studio, consulte [Tour pelos recursos do depurador](../debugger/debugger-feature-tour.md). Para saber mais sobre testes, consulte [Ferramentas de teste](https://www.visualstudio.com/vs/testing-tools/). Para saber mais sobre como melhorar o desempenho de seus aplicativos, consulte [Tour pelos recursos de criação de perfil](../profiling/profiling-feature-tour.md).

## <a name="deploy-your-finished-application"></a>Implantar o aplicativo concluído  
Quando o aplicativo está pronto para ser implantado em usuários ou clientes, o Visual Studio fornece as ferramentas para fazer isso, independentemente de você estar implantando na Windows Store, em um site do SharePoint ou com as tecnologias InstallShield ou Windows Installer. Ele é todo acessível por meio do IDE. Para obter mais informações, consulte [Implantação de aplicativos, serviços e componentes](../deployment/deploying-applications-services-and-components.md).

## <a name="quick-tour-of-the-ide"></a>Tour rápido pelo IDE
Para fornecer uma visão geral visual de alto nível do Visual Studio, a imagem a seguir mostra o Visual Studio com um projeto aberto, juntamente com várias janelas de ferramentas essenciais que provavelmente você usará.
 - O [Gerenciador de Soluções](../ide/solutions-and-projects-in-visual-studio.md) permite exibir, navegar e gerenciar os arquivos de código.
 - A janela [Editor](../ide/writing-code-in-the-code-and-text-editor.md) mostra o código e permite editar o código-fonte e os dados do designer.
 - A janela [Saída](../ide/reference/output-window.md) exibe mensagens de saída da compilação, execução, depuração e muito mais.
 - O [Team Explorer](https://www.visualstudio.com/docs/connect/work-team-explorer) permite que você controle itens de trabalho e compartilhe código com outras pessoas usando tecnologias de controle de versão como [Git](https://git-scm.com/) e [TFVC (Controle de Versão do Team Foundation)](https://www.visualstudio.com/docs/tfvc/overview).
 - O [Cloud Explorer](https://azure.microsoft.com/documentation/articles/vs-azure-tools-resources-managing-with-cloud-explorer/) permite exibir e gerenciar seus recursos do Azure, como máquinas virtuais, tabelas, bancos de dados SQL e muito mais.

![O IDE do Visual Studio](../ide/media/visualstudioide.png)  

Veja a seguir alguns outros recursos comuns de produtividade do Visual Studio.  

- A caixa de pesquisa [Início Rápido](https://docs.microsoft.com/en-us/visualstudio/ide/reference/quick-launch-environment-options-dialog-box) é uma ótima maneira de encontrar rapidamente o que você precisa no Visual Studio. Comece inserindo o nome de qualquer coisa que você está procurando e o Visual Studio oferecerá opções que levam você exatamente para o local desejado. O Início Rápido também mostra os links que iniciam o Instalador do Visual Studio em qualquer Carga de Trabalho ou Componente Individual.

  ![Caixa de pesquisa Início Rápido](../ide/media/VSIDE_Tour_QuickLaunch.png)

-  [Refatoração](../ide/refactoring-in-visual-studio.md) inclui operações como renomeação inteligente de variáveis, mover linhas de código selecionadas para uma função distinta, mover o código para outros locais, reordenação de parâmetros de função e muito mais.

 ![Refatoração](../ide/media/VSIDE_refactor.png)  

-  **IntelliSense** é um termo abrangente para um conjunto de recursos populares que exibe informações de tipo sobre seu código diretamente no editor e, em alguns casos, escreve pequenos pedaços de código pra você. É como ter a documentação básica embutida no editor, o que evita que você tenha que consultar informações de tipo em uma janela de ajuda separada. Os recursos do IntelliSense variam de acordo com a linguagem. Para obter mais informações, consulte [IntelliSense do Visual C#](../ide/visual-csharp-intellisense.md), [IntelliSense do Visual C++](../ide/visual-cpp-intellisense.md), [IntelliSense do JavaScript](../ide/javascript-intellisense.md), [IntelliSense específico do Visual Basic](../ide/visual-basic-specific-intellisense.md). A ilustração a seguir mostra alguns recursos do IntelliSense em funcionamento:  

  ![Lista de membros do Visual Studio](../ide/media/vs2017_Intellisense.png)  

-  **Rabiscos** são sublinhados vermelhos ondulados que alertam você sobre erros ou problemas potenciais no código em tempo real durante a digitação. Isso permite que você os corrija imediatamente sem esperar que o erro seja descoberto durante a compilação ou o tempo de execução. Se você passar o mouse sobre o rabisco, verá informações adicionais sobre o erro. Uma lâmpada também podem aparecer na margem esquerda com sugestões de como corrigir o erro. Para obter mais informações, consulte [Realizar ações rápidas com lâmpadas](../ide/perform-quick-actions-with-light-bulbs.md).  

 ![Rabiscos](../ide/media/vs2017_squiggle.png)  

-  A janela [Hierarquia de Chamada](../ide/reference/call-hierarchy.md) pode ser aberta no menu de contexto do editor de texto para mostrar os métodos que chamam e que são chamados pelo método sob o cursor (ponto de inserção).

 ![Janela de Hierarquia de Chamada](../ide/media/VSIDE_call_hierarchy.png)

-  [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) habilita a localizar referências e alterações em seu código, bugs vinculados, itens de trabalho, análises de código e testes de unidade, tudo sem sair do editor.

 ![CodeLens](../ide/media/codelensoverview.png)

-  A janela [Espiar Definição](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) mostra uma definição de método ou de tipo embutida, sem navegar para fora de seu contexto atual.  

 ![Espiar Definição](../ide/media/VSIDE_peek_definition.png)

-  A opção de menu de contexto **Ir para Definição** leva você diretamente para o local em que a função ou o objeto estão definidos. Outros comandos de navegação também estão disponíveis clicando com o botão direito do mouse no editor.

 ![Ir para Definição](../ide/media/VSIDE_go_to_definition.png)

- Uma ferramenta relacionada, o [Pesquisador de Objetos](http://msdn.microsoft.com/f89acfc5-1152-413d-9f56-3dc16e3f0470), permite a inspeção de assemblies do .NET ou do Windows Runtime no sistema para ver quais tipos eles contêm e quais membros (propriedades, métodos e eventos) esses tipos contêm.

  ![Pesquisador de Objetos mostrando System.Timer](../ide/media/objectbrowser.png)  

## <a name="manage-your-source-code-and-collaborate-with-others"></a>Gerenciar seu código-fonte e colaborar com outros
É possível gerenciar o código-fonte em repositórios Git hospedados por qualquer provedor, incluindo o GitHub. Se preferir, use o [VSTS (Visual Studio Team Services)](https://www.visualstudio.com/team-services/) para gerenciar o código junto com bugs e itens de trabalho de todo o projeto. Consulte [Introdução aos Serviços de Equipe e Git](https://www.visualstudio.com/en-us/docs/git/gitquickstart-vs2017) para obter mais informações sobre o gerenciamento de repositórios Git no Visual Studio usando o Team Explorer.  O Visual Studio também tem outros recursos de controle do código-fonte internos. Para saber mais sobre eles, consulte [Novos Recursos do Git no Visual Studio 2017 (blog)](https://blogs.msdn.microsoft.com/visualstudioalm/2017/03/06/new-git-features-in-visual-studio-2017/).

O Visual Studio Team Services é um serviço baseado em nuvem para hospedar projetos de software e permitir a colaboração em equipes. O VSTS oferece suporte a sistemas Git e Team Foundation Source Control, bem como as metodologias de desenvolvimento Agile, CMMI e Scrum. O TFVC (Controle de Versão do Team Foundation) usa um repositório de servidor único e centralizado para arquivos de versão e de controle. É sempre feito check-in das alterações locais no servidor central em que outros desenvolvedores podem obter as alterações mais recentes.

O TFS (Team Foundation Server) é o hub de gerenciamento do ciclo de vida do aplicativo para o Visual Studio. Ele habilita a participação de todos os envolvidos com o processo de desenvolvimento usando uma única solução. O TFS também é útil para gerenciar equipes e projetos heterogêneos.

Se você tiver uma conta do Visual Studio Team Services ou um Team Foundation Server na rede, conecte-se a ela por meio da janela do Team Explorer no Visual Studio. Nessa janela você pode fazer check-in ou check-out de código no controle do código-fonte, gerenciar itens de trabalho, iniciar compilações e acessar salas da equipe e espaços de trabalho. É possível abrir o Team Explorer na caixa **Início Rápido** ou no menu principal, em **Exibir, Team Explorer** ou em **Equipe, Gerenciar Conexões**.
A seguinte imagem mostra a janela do Team Explorer em uma solução que é hospedada no VSTS.

![Team Explorer para Visual Studio](../ide/media/vs2017_teamexplorer.png)  

Para obter mais informações sobre o Visual Studio Team Services, consulte [Visual Studio Team Services](https://www.visualstudio.com/team-services/). Para obter mais informações sobre o Team Foundation Server, consulte [Team Foundation Server](https://www.visualstudio.com/products/tfs-overview-vs).


## <a name="connect-to-services-databases-and-cloud-based-resources"></a>Conectar a serviços, bancos de dados e recursos baseados em nuvem
A nuvem é fundamental para o mundo conectado de hoje e o Visual Studio fornece os meios para aproveitá-lo. Por exemplo, o recurso Serviços Conectados permite conectar seu aplicativo aos serviços. Seus aplicativos podem usá-lo para armazenar os dados no armazenamento do Azure, entre outras coisas.

![Serviços conectados](../ide/media/VSIDE_Tour_Connected_Services.png)

A escolha de um serviço na página **Serviços Conectados** inicia um Assistente dos Serviços Conectados, que configura o projeto e baixa os pacotes NuGet necessários para ajudá-lo a começar a codificar no serviço.

É possível exibir e gerenciar seus recursos de nuvem baseados no Azure no Visual Studio usando o [Cloud Explorer](https://azure.microsoft.com/documentation/articles/vs-azure-tools-resources-managing-with-cloud-explorer/). O Cloud Explorer mostra os recursos do Azure em todas as contas gerenciadas na assinatura do Azure à qual você está conectado. É possível obter o Cloud Explorer selecionando a carga de trabalho de desenvolvimento do Azure no instalador do Visual Studio.

![Cloud Explorer](../ide/media/VSIDE_CloudExplorer.png)

O **Gerenciador de Servidores** ajuda você a procurar e gerenciar instâncias e ativos do SQL Server no Azure, no Salesforce.com, no Office 365 e em sites. Para abrir o Gerenciador de Servidores, no menu principal, escolha **Exibir**, **Gerenciador de Servidores**. Consulte [Adicionar novas conexões](https://docs.microsoft.com/visualstudio/data-tools/add-new-connections) para obter mais informações sobre como usar o Gerenciador de Servidores.

O [SSDT (SQL Server Data Tools)](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt) é um ambiente de desenvolvimento avançado do SQL Server, Banco de Dados SQL do Azure e Azure SQL Data Warehouse. Ele permite compilar, depurar, manter e refatorar bancos de dados. Você pode trabalhar com um projeto de banco de dados ou diretamente com uma instância local ou não de banco de dados conectado.

O **Pesquisador de Objetos do SQL Server** no Visual Studio fornece uma exibição dos objetos de banco de dados semelhante ao SQL Server Management Studio. O Pesquisador de Objetos do SQL Server permite realizar trabalhos leves de design e administração de banco de dados, incluindo edição de dados de tabela, comparação de esquemas e execução de consultas usando menus contextuais diretamente no Pesquisador de Objetos do SQL Server e muito mais. Consulte [Gerenciar objetos usando o Pesquisador de Objetos](https://docs.microsoft.com/sql/ssms/object/manage-objects-by-using-object-explorer) para obter mais informações.

![Pesquisador de Objetos do SQL Server](../ide/media/vs2015_sqlobjectexplorer.png)  

## <a name="extend-visual-studio"></a>Estenda o Visual Studio
Se o Visual Studio não tiver a funcionalidade exata de que você precisa, será possível adicioná-la! É possível personalizar o IDE de acordo com o estilo e fluxo de trabalho, adicionar suporte para ferramentas externas que ainda não estão integradas ao Visual Studio e modificar a funcionalidade existente para aumentar a produtividade. O Visual Studio fornece ferramentas, controles e modelos da Microsoft, de nossos parceiros e da comunidade. Para saber mais sobre como estender o Visual Studio, consulte [Estender o IDE do Visual Studio](https://www.visualstudio.com/vs/extend/).

## <a name="learn-more-and-find-out-whats-new"></a>Saiba mais e descubra as novidades
Se você nunca usou o Visual Studio antes, conheça os conceitos básicos, começando com a [Introdução ao Visual Studio](../ide/get-started-with-visual-studio.md) ou confira os cursos gratuitos do Visual Studio disponíveis na [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!index=2&lang=1033).
Se você quiser conferir as novas funcionalidades no Visual Studio 2017, consulte [Novidades no Visual Studio 2017](../ide/whats-new-in-visual-studio.md).

Parabéns por concluir o tour pelo IDE do Visual Studio! Esperamos que você tenha aprendido algo útil sobre alguns de seus principais recursos.

## <a name="see-also"></a>Consulte também
* [Visual Studio IDE](https://www.visualstudio.com/vs/)
* [Downloads do Visual Studio](https://www.visualstudio.com/downloads/)
* [O blog do Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/)
* [Fóruns do Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/en-US/home?category=visualstudio%2Cvsarch%2Cvsdbg%2Cvstest%2Cvstfs%2Cvsdata%2Cvsappdev%2Cvisualbasic%2Cvisualcsharp%2Cvisualc)
* [Microsoft Virtual Academy](https://mva.microsoft.com/)
* [Channel 9](https://channel9.msdn.com/)

