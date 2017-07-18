---
title: "Página de Aplicativo, Designer de Projeto (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesApplicationWPF
- vb.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
ms.assetid: 8cec9fea-cd92-47ff-88dd-7c928f0b4a74
caps.latest.revision: 64
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
ms.sourcegitcommit: 6fbf89668d47d55d1d77a1d7f11765567fc73405
ms.openlocfilehash: 4be8a1f36d81e2cb36d9daab9817f04d18ecb94a
ms.contentlocale: pt-br
ms.lasthandoff: 05/26/2017

---
# <a name="application-page-project-designer-visual-basic"></a>Página de Aplicativo, Designer de Projeto (Visual Basic)
Use a página **Aplicativo** do Designer de Projeto para especificar as propriedades e configurações de aplicativo de um projeto.  
  
 Para acessar a página **Aplicativo**, escolha um nó de projeto (não o nó **Solução**) no **Gerenciador de Soluções**. Em seguida, escolha **Projeto**, **Propriedades** na barra de menus. Quando o Designer de Projeto for exibido, clique na guia **Aplicativo**.  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="general-application-settings"></a>Configurações Gerais de Aplicativos  
 As opções a seguir permitem definir as configurações gerais para um aplicativo.  
  
 **Nome do assembly**  
 Especifica o nome do arquivo de saída que conterá o manifesto do assembly. Se você alterar essa propriedade, a propriedade **Nome de Saída** também será alterada. Também é possível fazer essa alteração em um prompt de comando usando [/out (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/out). Para obter informações sobre como acessar esta propriedade de forma programática, consulte <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.  
  
 **Namespace raiz**  
 Especifica o namespace base para todos os arquivos no projeto. Por exemplo, se você configurasse o **Namespace raiz** para `Project1` e tivesse um `Class1` fora de qualquer namespace em seu código, seu namespace seria `Project1.Class1`. Se você tivesse um `Class2` em um namespace `Order` no código, seu namespace seria `Project1.Order.Class2`.  
  
 Se você desmarcar **Namespace raiz**, será possível especificar a estrutura do namespace do seu projeto no código.  
  
> [!NOTE]
>  Se você usar a palavra-chave global em uma [Instrução Namespace](/dotnet/visual-basic/language-reference/statements/namespace-statement), será possível definir um namespace fora do namespace raiz do seu projeto. Se você desmarcar a **Namespace raiz**, `Global` se tornará o namespace de nível superior, que acaba com a necessidade da palavra-chave `Global` em uma instrução `Namespace`. Para obter mais informações, consulte "Palavra-chave nas declarações de Namespace global" em [Namespaces no Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/namespaces).  
  
 Para obter informações sobre como criar namespaces no seu código, consulte [Instrução Namespace](/dotnet/visual-basic/language-reference/statements/namespace-statement).  
  
 Para obter mais informações sobre a propriedade de namespace raiz, consulte [/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace).  
  
 Para obter informações sobre como acessar esta propriedade de forma programática, consulte <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.  
  
 **Estrutura de destino (todas as configurações)**  
 Especifica a versão no .NET Framework que o aplicativo direciona. Essa opção pode ter valores diferentes dependendo de quais versões do .NET Framework estão instaladas em seu computador.  
  
 O valor padrão corresponde à estrutura de destino especificada na caixa de diálogo **Novo projeto**.  
  
> [!NOTE]
>  Os pacotes de pré-requisitos listados na [Caixa de diálogo Pré-requisitos](../../ide/reference/prerequisites-dialog-box.md) são definidos automaticamente quando você abre a caixa de diálogo pela primeira vez. Se você alterar posteriormente a estrutura de destino do projeto, será necessário especificar os pré-requisitos manualmente para corresponder à nova estrutura de destino.  
  
 Para obter mais informações, consulte [Como destinar uma versão do .NET Framework](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) e [Visão geral de multiplataforma Visual Studio](../../ide/visual-studio-multi-targeting-overview.md).  
  
 **Tipo de aplicativo**  
 Especifica o tipo de aplicativo a ser compilado. Para aplicativos [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)], é possível especificar **aplicativo da Windows Store**, **Biblioteca de Classes** ou **Arquivo WinMD**. Para a maioria dos outros tipos de aplicativo, é possível especificar **aplicativos do Windows**, **aplicativo de Console**, **Biblioteca de Classes**, **Serviço Windows** ou **Biblioteca de Controles da Web**.  
  
 Para um projeto de aplicativo Web, é necessário especificar **Biblioteca de Classes**.  
  
 Se você especificar a opção **Arquivo WinMD**, os tipos poderão ser projetados em uma linguagem de programação do Windows Runtime. Ao empacotar a saída do projeto como um arquivo WinMD, é possível codificar um aplicativo em várias linguagens e ter interoperação de código como se você tivesse escrito tudo na mesma linguagem. É possível usar a opção **Arquivo WinMD** para soluções que direcionam as bibliotecas do Windows Runtime, incluindo os aplicativos [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)]. Para obter mais informações, consulte [Criando componentes do Windows Runtime em C# e Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).  
  
> [!NOTE]
>  O Windows Runtime pode projetar tipos para que eles sejam exibidos como objetos nativos em qualquer que os use. Por exemplo, aplicativos JavaScript que interagem com o Windows Runtime usam-no como um conjunto de objetos JavaScript e aplicativos C# usam a biblioteca como uma coleção de objetos .NET. Ao empacotar a saída do projeto como um arquivo WinMD, você pode aproveitar a mesma tecnologia que o Windows Runtime usa.  
  
 Para obter mais informações sobre a propriedade **Tipo de aplicativo**, consulte [/target (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/target). Para obter informações sobre como acessar essa propriedade de forma programática, consulte <xref:VSLangProj.ProjectProperties.OutputType%2A>.  
  
 **Ícone**  
 Define o arquivo .ico que você deseja usar como o ícone do programa. Selecione **\<Procurar.. >** para procurar um gráfico existente. Consulte [-win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) (ou [-win32icon (opções do compilador C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option)) para obter mais informações. Para acessar essa propriedade de forma programática, consulte <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.  
  
 **Formulário de inicialização/objeto de inicialização/URI de inicialização**  
 Especifica o formulário de inicialização ou ponto de entrada do aplicativo.  
  
 Se **Habilitar estrutura de aplicativo** estiver selecionado (o padrão), essa lista será denominada **Formulário de inicialização** e mostrará somente formulários, porque a estrutura de aplicativo dá suporte somente a formulários de inicialização, não objetos.  
  
 Se o projeto for um Aplicativo de Navegador do WPF, essa lista será denominada **URI de inicialização** e o padrão será **Page1.xaml**. A lista **URI de inicialização** permite que você especifique o recurso de interface do usuário (um elemento XAML) que o aplicativo exibe quando o ele é iniciado. Para obter mais informações, consulte <xref:System.Windows.Application.StartupUri%2A>.  
  
 Se **Habilitar estrutura de aplicativo** estiver desmarcado, essa lista se tornará **Objeto de inicialização** e mostrará os formulários e classes ou módulos com um `Sub Main`.  
  
 **Objeto de inicialização** define o ponto de entrada a ser chamado quando o aplicativo é carregado. Geralmente, isso é definido como o principal formulário em seu aplicativo ou como o procedimento `Sub Main` que deve ser executado quando o aplicativo é iniciado. Como as bibliotecas de classe não têm um ponto de entrada, sua única opção para essa propriedade é **(Nenhum)**. Para obter mais informações, consulte [/main](/dotnet/visual-basic/reference/command-line-compiler/main). Para acessar essa propriedade de forma programática, consulte <xref:VSLangProj.ProjectProperties.StartupObject%2A>.  
  
 **Informações do assembly**  
 Clique neste botão para exibir a [Caixa de diálogo de Informações do Assembly](../../ide/reference/assembly-information-dialog-box.md).  
  
 **Habilitar estrutura de aplicativo**  
 Especifica se um projeto usará a estrutura de aplicativo. A configuração dessa opção afeta as opções disponíveis em **Formulário de inicialização**/**Objeto de inicialização**.  
  
 Se essa caixa de seleção estiver selecionada, seu aplicativo usará o padrão `Sub Main`. Marcar essa caixa de seleção habilita os recursos na seção **Propriedades da estrutura dos aplicativos do Windows** e também exige que você selecione um formulário de inicialização.  
  
 Se essa caixa de seleção estiver desmarcada, seu aplicativo usará o `Sub Main` personalizado que você especificou no **Formulário de inicialização**. Nesse caso, é possível especificar um objeto de inicialização (um `Sub Main` personalizado em um método ou em uma classe) ou um formulário. Além disso, as opções na seção **Propriedades da estrutura dos aplicativos do Windows** ficam indisponíveis.  
  
 **Exibir configurações do Windows**  
 Clique neste botão para gerar e abrir o arquivo app.manifest. O Visual Studio usa esse arquivo para gerar dados de manifesto do aplicativo. Em seguida, defina nível de execução solicitado pelo UAC modificando a marcação `<requestedExecutionLevel>` no app.manifest da seguinte maneira:  
  
 `<requestedExecutionLevel level="asInvoker" />`  
  
 O ClickOnce funciona com um nível de `asInvoker` ou no modo virtualizado (não há geração de manifesto). Para especificar o modo virtualizado, remova toda a marcação de app.manifest.  
  
 Para obter mais informações sobre a geração de manifesto, consulte [Implantação do ClickOnce no Windows Vista](../../deployment/clickonce-deployment-on-windows-vista.md).  
  
## <a name="windows-application-framework-properties"></a>Propriedades da estrutura dos aplicativos do Windows  
 As seguintes configurações estão disponíveis na seção **Propriedades da estrutura dos aplicativos do Windows**. Essas opções estarão disponíveis somente se a caixa de seleção **Habilitar estrutura de aplicativo** estiver selecionada. A seção depois desta descreve as configurações **Propriedades da estrutura do aplicativos do Windows** para aplicativos WPF (Windows Presentation Foundation).  
  
 **Habilitar estilos visuais do XP**  
 Habilita ou desabilita os estilos visuais do Windows XP, também conhecidos como *Temas do Windows XP*. Os estilos visuais do Windows XP habilitam, por exemplo, controles com cantos arredondados e cores dinâmicas. O padrão é habilitado. Para obter mais informações sobre estilos visuais do Windows XP, consulte [Recursos do Windows XP e controles do Windows Forms](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)).  
  
 **Criar um aplicativo de instância única**  
 Marque esta caixa de seleção para impedir que usuários executem várias instâncias do aplicativo. A configuração padrão para essa caixa de seleção é desmarcada. Essa configuração permite que várias instâncias do aplicativo sejam executadas.  
  
 **Salvar My.Settings no desligamento**  
 Marque esta caixa de seleção para especificar que as configurações `My.Settings` do aplicativo são salvas quando os usuários desligam seus computadores. A configuração padrão é habilitado. Se essa opção estiver desabilitada, será possível salvar as configurações do aplicativo manualmente chamando `My.Settings.Save`.  
  
 **Modo de autenticação**  
 Selecione **Windows** (o padrão) para especificar o uso da autenticação do Windows para identificar o usuário conectado no momento. É possível recuperar essas informações no tempo de execução usando o objeto `My.User`. Selecione **Definido pelo aplicativo** se você for fornecer seu próprio código para autenticar usuários em vez de usar os métodos de autenticação padrão do Windows.  
  
 **Modo de fechamento**  
 Selecione **Quando o formulário de inicialização fechar** (o padrão) para especificar que o aplicativo saia quando o formulário definido como o formulário de inicialização for fechado, mesmo se outros formulários estiverem abertos. Selecione **Quando o último formulário fechar** para especificar que o aplicativo saia quando o último formulário for fechado ou quando a instrução `My.Application.Exit` ou `End` for chamada explicitamente.  
  
 Selecione **No desligamento explícito** para especificar que o aplicativo saia quando você chamar explicitamente `Shutdown`.  
  
 Selecione **No fechamento da última janela** para especificar que o aplicativo saia quando a última janela for fechada ou quando você chamar explicitamente `Shutdown`. Essa é a configuração padrão.  
  
 Selecione **No fechamento da janela principal** para especificar que o aplicativo saia quando a janela principal for fechada ou quando você chamar explicitamente `Shutdown`.  
  
 **Tela inicial**  
 Selecione o formulário que você deseja usar como uma tela inicial. É necessário ter criado anteriormente uma tela inicial usando um formulário ou modelo. O padrão é **(Nenhum)**.  
  
 **Exibir eventos de aplicativo**  
 Clique neste botão para exibir um arquivo de código de eventos no qual você pode gravar eventos para os eventos de estrutura do aplicativo `Startup`, `Shutdown`, `UnhandledException`, `StartupNextInstance` e `NetworkAvailabilityChanged`. Também é possível substituir determinados métodos de estrutura do aplicativo. Por exemplo, é possível alterar o comportamento de exibição da tela inicial substituindo `OnInitialize`.  
  
### <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-applications"></a>Propriedades do Windows Presentation Foundation para aplicativos WPF (Windows Presentation Foundation)  
 As seguintes configurações estão disponíveis na seção **Propriedades da estrutura dos aplicativos do Windows** quando o projeto é um aplicativo Windows Presentation Foundation. Essas opções estarão disponíveis somente se a caixa de seleção **Habilitar estrutura de aplicativo** estiver selecionada. As opções listadas nesta tabela estão disponíveis somente para aplicativos WPF ou aplicativos de navegador WPF. Elas não estão disponíveis para bibliotecas de controle de usuário ou de controle personalizado WPF.  
  
 **Modo de fechamento**  
 Esta propriedade é aplicável somente a aplicativos Windows Presentation Foundation.  
  
 Selecione **No desligamento explícito** para especificar que o aplicativo saia quando você chamar explicitamente <xref:System.Windows.Application.Shutdown%2A>.  
  
 Selecione **No fechamento da última janela** para especificar que o aplicativo saia quando a última janela for fechada ou quando você chamar explicitamente <xref:System.Windows.Application.Shutdown%2A>. Essa é a configuração padrão.  
  
 Selecione **No fechamento da janela principal** para especificar que o aplicativo saia quando a janela principal for fechada ou quando você chamar explicitamente <xref:System.Windows.Application.Shutdown%2A>.  
  
 Para obter mais informações sobre como usar essa configuração, consulte <xref:System.Windows.Application.Shutdown%2A>  
  
 **Editar XAML**  
 Clique neste botão para abrir e modificar o arquivo de definição de aplicativo (Application.xaml) no editor XAML. Quando você clica nesse botão, Application.xaml é aberto no nó de definição de aplicativo. Talvez seja necessário editar esse arquivo para executar determinadas tarefas, como a definição de recursos. Se o arquivo de definição de aplicativo não existir, o Designer de Projeto criará um.  
  
 **Exibir eventos de aplicativo**  
 Clique neste botão para exibir o arquivo de classe parcial `Application` (Application.xaml.vb) em um editor de código. Se o arquivo não existir, o Designer de Projeto criará um com o namespace e o nome de classe apropriado.  
  
 O objeto <xref:System.Windows.Application> gera eventos quando ocorrem determinadas alterações no estado do aplicativo (por exemplo, na inicialização ou no desligamento do aplicativo). Para obter uma lista completa dos eventos que essa classe expõe, consulte <xref:System.Windows.Application>. Esses eventos são manipulados na seção de código do usuário da classe parcial `Application`.  
  
## <a name="see-also"></a>Consulte também  
[Gerenciando propriedades do aplicativo](../../ide/application-properties.md)
 [Escrevendo código em soluções do Office](/office-dev/office-dev/writing-code-in-office-solutions)
