---
title: Dentro do Visual Studio SDK | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d6607e30964ea7279daa0cf7d7a26127b27ec5ee
ms.lasthandoff: 02/22/2017

---
# <a name="inside-the-visual-studio-sdk"></a>Dentro do Visual Studio SDK
Esta seção fornece informações detalhadas sobre as extensões do Visual Studio, incluindo a arquitetura do Visual Studio, componentes, serviços, esquemas, utilitários e assim por diante.  
  
## <a name="extensibility-architecture"></a>Arquitetura de extensibilidade  
 A ilustração a seguir mostra a arquitetura de extensibilidade do Visual Studio. Os VSPackages oferece a funcionalidade de aplicativo, que é compartilhada entre o IDE como serviços. O IDE padrão também oferece uma ampla variedade de serviços, como <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, que fornece acesso à funcionalidade de janelas do IDE.</xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 ![Gráfico de arquitetura de ambiente](../../extensibility/internals/media/environment.gif "environment")  
Modo de exibição geral da arquitetura do Visual Studio  
  
## <a name="vspackages"></a>VSPackages  
 Os VSPackages são módulos de software que formam e estendem o Visual Studio com elementos da interface do usuário, serviços, projetos, editores e designers. Os VSPackages são a unidade de arquitetura central do Visual Studio. Para obter mais informações, consulte [VSPackages](../../extensibility/internals/vspackages.md).  
  
## <a name="visual-studio-shell"></a>Shell do Visual Studio  
 Shell do Visual Studio fornece a funcionalidade básica e suporte a comunicação entre suas extensões de componente VSPackages e MEF. Para obter mais informações, consulte [Shell do Visual Studio](../../extensibility/internals/visual-studio-shell.md).  
  
## <a name="user-experience-guidelines"></a>Diretrizes de experiência do usuário  
 Se você planeja criar novos recursos do Visual Studio, você deve dar uma olhada estas diretrizes para obter dicas de design e a usabilidade: [diretrizes de experiência de usuário do Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="commands"></a>Comandos  
 Comandos são funções que realizar tarefas, como imprimir um documento, atualizar uma exibição ou criar um novo arquivo.  
  
 Quando você estende o Visual Studio, você pode criar comandos e registrá-los com o shell do Visual Studio. Você pode especificar como esses comandos serão exibidos no IDE, por exemplo, em um menu ou barra de ferramentas. Normalmente um comando personalizado aparece no **ferramentas** menu e um comando para exibir uma janela de ferramenta seriam exibido no **outras janelas** submenu a **exibição** menu.  
  
 Quando você cria um comando, você também deve criar um manipulador de eventos para ele. O manipulador de eventos determina quando o comando é habilitado ou visível, permite que você modifique seu texto e garante que o comando responde apropriadamente quando ele está ativado. Na maioria dos casos, o IDE manipula comandos usando o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interface.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Comandos no Visual Studio são tratados começando com o contexto do comando interno, com base na seleção de local e prosseguir com o contexto mais externo, com base na seleção global. Os comandos adicionados ao menu principal são imediatamente disponibilizados para scripts.  
  
 Para obter mais informações, consulte [comandos, Menus e barras de ferramentas](../../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="menus-and-toolbars"></a>Menus e barras de ferramentas  
 Menus e barras de ferramentas fornecem uma maneira para os usuários a chamar comandos. Menus são linhas ou colunas de comandos que normalmente são exibidos como itens individuais do texto na parte superior de uma janela de ferramenta. Submenus são menus secundários que aparecem quando um usuário clica em comandos que incluem uma pequena seta. Menus de contexto exibido quando um usuário clica determinados elementos de interface do usuário. Alguns nomes de menu comuns são **arquivo**, **editar**, **exibição**, e **janela**. Para obter mais informações, consulte [estendendo Menus e comandos](../../extensibility/extending-menus-and-commands.md).  
  
 Barras de ferramentas são linhas ou colunas de botões e outros controles, como caixas de texto, caixas de listagem e caixas de combinação. Botões da barra de ferramentas normalmente têm imagens de ícone, como um ícone de pasta para uma **abrir arquivo** comando ou uma impressora para um **impressão** comando. Todos os elementos da barra de ferramentas são associados a comandos. Quando você clica em um botão da barra de ferramentas, o comando associado é executado. No caso de um controle de lista suspensa, cada item na lista suspensa é associado um comando diferente. Alguns controles de barra de ferramentas, como um controle de splitter são híbridas. Um lado do controle é um botão de barra de ferramentas e o outro lado é uma seta para baixo que exibe vários comandos quando ele for clicado.  
  
## <a name="tool-windows"></a>Janelas de Ferramentas  
 Janelas de ferramentas são usadas no IDE para exibir informações. **Caixa de ferramentas**, **Solution Explorer**, **propriedades** janela, e **navegador da Web** são exemplos de janelas de ferramenta.  
  
 Janelas de ferramentas normalmente oferecem vários controles com a qual o usuário pode interagir. Por exemplo, o **propriedades** janela permite ao usuário definir propriedades de objetos que têm um propósito específico. O **propriedades** janela é especializada nesse sentido, mas também geral porque ela pode ser usada em muitas situações diferentes. Da mesma forma, o **saída** janela é especializada porque ele fornece uma saída baseada em texto, mas geral porque vários subsistemas no Visual Studio podem ser usado para fornecer saída para o usuário do Visual Studio.  
  
 Considere a imagem a seguir do Visual Studio, que contém várias janelas de ferramenta.  
  
 ![Captura de tela](../../extensibility/internals/media/t1gui.png "T1gui")  
  
 Algumas janelas de ferramentas estão encaixadas em um único painel que exibe a janela de ferramenta do Gerenciador de soluções e oculta a ferramenta windows mas torna disponíveis clicando nas guias. A figura mostra duas outras janelas de ferramenta, o **Error List** e **saída** janela, encaixada em um único painel.  
  
 Também mostrado é o painel do documento principal, que mostra várias janelas do editor. Embora a ferramenta windows normalmente têm uma única instância (por exemplo, você pode abrir apenas uma **Solution Explorer**), janelas do editor podem ter várias instâncias, cada um deles é usada para editar um documento separado, mas todas são encaixadas no mesmo painel. A figura mostra um painel de documento que tem duas janelas do editor, uma janela de designer de formulário e uma janela do navegador que mostra a página de início. Todas as janelas no painel do documento estão disponíveis clicando em guias, mas a janela do editor que contém o arquivo EditorPane.cs está visível e ativo.  
  
 Quando você estende o Visual Studio, você pode criar ferramenta janelas que permitem que os usuários do Visual Studio interagir com a extensão. Você também pode criar seus próprios editores que permitem que os usuários do Visual Studio editar documentos. Porque seu editores e janelas de ferramenta serão integradas ao Visual Studio, você não precisa programá-los para encaixar ou aparecer em uma guia corretamente. Quando eles são registrados corretamente no Visual Studio, eles terão automaticamente os recursos típicos de janelas de ferramenta e de documentos no Visual Studio. Para obter mais informações, consulte [estendendo e personalizando janelas de ferramenta](../../extensibility/extending-and-customizing-tool-windows.md).  
  
## <a name="document-windows"></a>Janelas de documento  
 Uma janela de documento é uma janela filho com quadros de uma janela de interface de documentos múltiplos (MDI). Janelas de documento normalmente são usadas para hospedar controles de edição, editores de formulário (também conhecido como designers) ou editores de texto, mas também podem hospedar outros tipos funcionais. O **novo arquivo** caixa de diálogo inclui exemplos de janelas de documento fornecido pelo Visual Studio.  
  
 A maioria dos editores são específicos para uma linguagem de programação ou um tipo de arquivo, como conjuntos de quadros, páginas HTML, arquivos C++ ou arquivos de cabeçalho. Selecionando um modelo no **novo arquivo** caixa de diálogo, um usuário cria dinamicamente uma janela de documento para o editor para o tipo de arquivo que está associado com o modelo. Uma janela de documento também é criada quando um usuário abre um arquivo existente.  
  
 Janelas de documento são restritas a área do cliente MDI. Cada janela de documento tem uma guia na parte superior e ordem de tabulação está vinculada a outras janelas que podem ser abertas na área de MDI. Clicando na guia de uma janela do documento exibe um menu de atalho que inclui opções para dividir a área MDI em vários grupos de guia horizontal ou vertical. Dividir a área MDI permite que vários arquivos sejam exibidos ao mesmo tempo. Para obter mais informações, consulte [janelas de documento](../../extensibility/internals/document-windows.md).  
  
## <a name="editors"></a>Editores  
 O editor do Visual Studio permite personalizá-lo e usá-lo para seu próprio tipo de conteúdo por meio de Managed Extensibility Framework (MEF). Em muitos casos você não precisará criar um VSPackage para estender o editor, embora se você quiser incluir recursos do shell (por exemplo, um comando de menu ou uma tecla de atalho), você pode combinar uma extensão do MEF com um VSPackage.  
  
 Você também pode criar um editor personalizado, por exemplo, se você quiser ler e gravar em um banco de dados, ou se você quiser usar um designer. Você também pode usar um editor externo, como o bloco de notas ou o Microsoft WordPad. Para obter mais informações, consulte [Editor e extensões do serviço de linguagem](../../extensibility/editor-and-language-service-extensions.md).  
  
## <a name="language-services"></a>Serviços de linguagem  
 Se desejar que o editor do Visual Studio para dar suporte a programação novas palavras-chave ou até mesmo uma nova linguagem de programação, você pode criar um serviço de linguagem. Cada serviço de linguagem pode implementar determinados recursos do editor totalmente, parcial ou não. Dependendo de como estiver configurado, o serviço de linguagem pode fornecer o realce de sintaxe, a correspondência de colchetes, suporte IntelliSense e outros recursos no editor.  
  
 No coração de um serviço de linguagem são um analisador e um scanner. Um scanner (ou analisador léxico) divide um arquivo de origem em elementos que são conhecidos como tokens e um analisador estabelece as relações entre esses tokens. Quando você cria um serviço de linguagem, você deve implementar o analisador e o mecanismo de varredura para que o Visual Studio possa entender os tokens e a gramática da linguagem. Você pode criar serviços de idioma gerenciado ou não gerenciado. Para obter mais informações, consulte [extensibilidade de serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-extensibility.md).  
  
## <a name="projects"></a>Projetos  
 No Visual Studio, os projetos são contêineres que os desenvolvedores usam para organizar e compilar o código-fonte e outros recursos. Projetos permitem organizar, compilar, depurar e implantar o código-fonte, as referências a serviços Web e bancos de dados e outros recursos. Os VSPackages pode estender o sistema de projetos do Visual Studio, fornecendo ferramentas personalizadas, subtipos de projeto e tipos de projeto.  
  
 Projetos também podem ser coletados em uma solução, que é um agrupamento de um ou mais projetos que trabalham juntos para criar um aplicativo. Projeto e informações de status que diz respeito à solução são armazenadas em dois arquivos de solução, o arquivo de solução com base em texto (. sln) e o arquivo de opção (. suo) de usuário da solução binário. Esses arquivos são semelhantes aos arquivos de grupo (. vbg) que foram usados nas versões anteriores do [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], e o espaço de trabalho (. dsw) e o usuário opções de arquivos (. opt) que foram usados nas versões anteriores do [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 Para obter mais informações, consulte [projetos](../../extensibility/internals/projects.md) e [soluções](../../extensibility/internals/solutions.md).  
  
## <a name="project-and-item-templates"></a>Modelos de projeto e Item  
 Visual Studio inclui modelos de projeto predefinidos e modelos de item de projeto. Você pode também tornar seus próprios modelos ou adquirir modelos da comunidade e integrá-las no Visual Studio. O [MSDN Code Gallery](http://code.msdn.microsoft.com/Project/ProjectDirectory.aspx?ProjectSearchText=visual%20studio) é o lugar certo para modelos e extensões.  
  
 Modelos contêm a estrutura de projeto e os arquivos básicos necessários para criar um determinado tipo de classe, controle, biblioteca ou aplicativo. Quando você deseja desenvolver um software que se parece com um dos modelos, criar um projeto com base no modelo e, em seguida, modificar os arquivos no projeto.  
  
> [!NOTE]
>  Não há suporte para essa arquitetura de modelo para [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projetos. Para obter informações sobre como criar [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] modelos de projeto, consulte [Projetando um assistente](/visual-cpp/ide/designing-a-wizard).  
  
 Para obter mais informações, consulte [Adicionar projeto e modelos de Item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## <a name="properties-and-options"></a>Propriedades e opções  
 O **propriedades** janela exibe as propriedades de um ou vários itens selecionados: [estendendo propriedades](../../extensibility/internals/extending-properties.md) páginas de opções contêm conjuntos de opções que pertencem a um componente específico, como uma linguagem de programação ou um VSPackage: [opções e páginas de opções](../../extensibility/internals/options-and-options-pages.md). As configurações são recursos geralmente relacionados à interface do usuário que podem ser importados e exportados: [suporte para configurações de usuário](../../extensibility/internals/support-for-user-settings.md).  
  
## <a name="visual-studio-services"></a>Serviços do Visual Studio  
 Um serviço fornece um conjunto específico de interfaces de componentes consumir. Visual Studio fornece um conjunto de serviços que podem ser usadas por todos os componentes, inclusive extensões. Por exemplo, serviços do Visual Studio permitem que janelas de ferramenta a ser mostrado ou ocultado dinamicamente, habilitar o acesso à Ajuda, barra de status ou eventos de interface do usuário. Editor do Visual Studio também fornece serviços que podem ser importados por extensões de editor. Para obter mais informações, consulte [usando e fornecer serviços](../../extensibility/using-and-providing-services.md).  
  
## <a name="debugger"></a>Depurador  
 O depurador é a interface do usuário para os componentes de depuração específicas do idioma. Se você tiver criado um novo serviço de linguagem, você precisará criar um mecanismo de depuração específicas conectem o depurador. Para obter mais informações, consulte [extensibilidade do depurador do Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## <a name="source-control"></a>Controle do código-Fonte  
 Para obter informações sobre como implementar um plug-in de controle de origem ou VSPackage, consulte [Source Control](../../extensibility/internals/source-control.md).  
  
## <a name="wizards"></a>Assistentes  
 Você pode criar um assistente em conjunto com um novo tipo de projeto, para que o assistente pode ajudar os usuários tomem as decisões corretas ao criar um novo projeto desse tipo. Para obter mais informações, consulte [assistentes](../../extensibility/internals/wizards.md).  
  
## <a name="custom-tools"></a>Ferramentas personalizadas  
 Ferramentas personalizadas permitem associar uma ferramenta de um item em um projeto e executar essa ferramenta, sempre que o arquivo é salvo. Para obter mais informações, consulte [ferramentas personalizadas](../../extensibility/internals/custom-tools.md).  
  
## <a name="vssdk-utilities"></a>Utilitários VSSDK  
 O VSSDK inclui um conjunto de utilitários que podem ser necessários para trabalhar com diferentes aspectos de VSPackages. Para obter mais informações, consulte [VSSDK utilitários](../../extensibility/internals/vssdk-utilities.md).  
  
## <a name="using-windows-installer"></a>Usando o Windows Installer  
 Em alguns casos, talvez seja necessário usar o Windows Installer em vez do instalador VSIX: por exemplo, talvez seja necessário gravar no registro. Para obter informações sobre o uso do Windows Installer com as extensões, consulte [instalando os VSPackages com o Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
## <a name="help-viewer"></a>Visualizador da Ajuda  
 Você pode integrar seus próprios ajuda e F1 páginas no Visualizador da Ajuda. Para obter mais informações, consulte [SDK do Visualizador da Ajuda Microsoft](../../extensibility/internals/microsoft-help-viewer-sdk.md).
