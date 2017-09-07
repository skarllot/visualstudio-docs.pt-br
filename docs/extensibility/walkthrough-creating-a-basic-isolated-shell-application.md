---
title: 'Passo a passo: Criando um Basic aplicativo de Shell isolado | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 54
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
ms.translationtype: MT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: e007e366847ac42d3916b16cbde190e8fd755821
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>Passo a passo: Criando um aplicativo de Shell isolado básico
Este passo a passo mostra como criar uma solução de shell isolado, personalizar a janela de ferramenta sobre da Ajuda e criar um programa de instalação que instala o shell isolado.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para acompanhar este passo a passo, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [SDK do Visual Studio](../extensibility/visual-studio-sdk.md). Para implantar o shell isolado, você também deve usar o pacote redistribuível do Visual Studio Shell (isolado).  
  
## <a name="creating-an-isolated-shell-solution"></a>Criando uma solução de Shell isolado  
 Esta seção mostra como usar o modelo de projeto Visual Studio Shell isolado para criar uma solução de shell isolado. A solução contém projetos a seguir:  
  
-   O *SolutionName*. Projeto AboutBoxPackage, o que permite que você personalize a aparência da Ajuda/sobre caixa.  
  
-   O projeto ShellExtensionsVSIX, que contém o arquivo source.extension.vsixmanifest que define os diferentes componentes do aplicativo de shell isolado.  
  
-   O *SolutionName* projeto, que gera o arquivo executável que invoca o aplicativo de shell isolado. Este projeto contém a pasta de personalização do Shell, que permite personalizar a aparência e comportamento do aplicativo de shell isolado.  
  
-   O *SolutionName* projeto de interface do usuário, o que produz um assembly satélite que define os comandos de menu ativo e cadeias de caracteres localizáveis.  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>Para criar uma solução básica de shell isolado  
  
1.  Abra o Visual Studio e crie um novo projeto.  
  
2.  No **novo projeto** janela, expanda **outros tipos de projetos** e **extensibilidade**. Selecione o **Visual Studio Shell isolado** modelo de projeto.  
  
3.  Nomeie o projeto `MyVSShellStub` e especifique um local. Verifique se **criar diretório para solução** está marcada e, em seguida, clique em **Okey**.  
  
     A nova solução aparece na **Gerenciador de soluções**.  
  
4.  Compile a solução e iniciar a depuração do aplicativo de shell isolado.  
  
     O Visual Studio shell isolado é exibida. Na barra de título lê **MyVSShellStub**. O ícone da barra de título é gerado de \MyVSShellStub\Resource Files\ApplicationIcon.ico.  
  
## <a name="customizing-the-application-name-and-icon"></a>Personalizando o nome do aplicativo e o ícone  
 Talvez você queira colocar a marca do seu aplicativo usando o nome da sua empresa e seu logotipo na barra de título. As etapas a seguir mostram como alterar o nome e o ícone que são exibidos na barra de título de aplicativo personalizado alterando o arquivo de definição de pacote, MyVSShellStub.Application.pkgdef.  
  
#### <a name="to-customize-the-application-name-and-icon"></a>Para personalizar o nome do aplicativo e o ícone  
  
1.  No projeto MyVSShellStub, abra \Shell Customization\MyVSShellStub.Application.pkgdef.  
  
2.  Alterar o `AppName` valor do elemento para **"AppName" = "Fabrikam música Editor"**  
  
3.  Para alterar o ícone do aplicativo, copie um ícone diferente para o diretório de \MyVSShellStub\MyVSShellStub\MyVSShellStub\. Renomeie o arquivo ApplicationIcon.ico para ApplicationIcon1.ico. Renomeie o novo arquivo para ApplicationIcon.ico.  
  
4.  Compile a solução e inicie a depuração. O shell isolado IDE é exibida. Na barra de título tem o novo ícone ao lado das palavras **Fabrikam música Editor**.  
  
## <a name="customizing-the-default-web-browser-home-page"></a>Personalizando a página inicial do navegador da Web padrão  
 Esta seção mostra como alterar a home page do padrão da **navegador da Web** janela alterando o arquivo de definição de pacote.  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>Para personalizar a home page do navegador da Web padrão  
  
1.  No arquivo MyVSShellStub.Application.pkgdef, altere o `DefaultHomePage` valor do elemento "http://www.microsoft.com".  
  
2.  Recompile o projeto MyVSShellStub.  
  
3.  Compile a solução e inicie a depuração.  
  
4.  Em **exibição / outras janelas**, clique em **navegador da Web**. O **navegador da Web** janela exibe a home page da Microsoft Corporation.  
  
## <a name="removing-the-print-command"></a>Removendo o comando Print  
 O arquivo. VSCT em um projeto de interface do usuário do shell isolado consiste em um conjunto de declarações do formulário `<Define name=No_` *elemento*`>`, onde *elemento* é um dos comandos e menus padrão do Visual Studio.  
  
 Se uma declaração é removido do comentário, esse menu ou o comando é excluído do shell isolado. Por outro lado, se uma declaração é comentada, o menu ou o comando está incluído no shell isolado.  
  
 Nas etapas a seguir, remova o comando de impressão em seu arquivo. VSCT.  
  
#### <a name="to-remove-the-print-command"></a>Para remover o comando print  
  
1.  Verifique o **impressão** comando aparece no **arquivo** menu do aplicativo do shell isolado.  
  
2.  No projeto MyVSShellStubUI, abra \Resource Files\MyVSShellStubUI.vsct para edição.  
  
3.  Remova os comentários desta linha:  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4.  Isso remove o comando print.  
  
5.  Inicie a depuração do aplicativo de shell isolado. Verifique o **arquivo / impressão** comando não existe mais.  
  
## <a name="removing-features-from-the-isolated-shell"></a>Removendo recursos do Shell isolado  
 Você pode remover alguns dos pacotes que são carregados com o Visual Studio, editando o arquivo de .pkgundef se você não quiser esses recursos em seu aplicativo de shell isolado personalizado. Especifique o pacote em uma das subchaves da chave do registro $RootKey$ \Packages.  
  
> [!NOTE]
>  Para localizar os recursos de GUIDs do Visual Studio, consulte [pacote GUIDs de recursos do Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
 O procedimento a seguir mostra como remover o XML editor do shell isolado.  
  
#### <a name="to-remove-the-xml-editor"></a>Para remover o editor de XML  
  
1.  Abra o arquivo MyVSShellStub.pkgundef na pasta do projeto MyVSShellStub de personalização do Shell.  
  
2.  Descomente a linha a seguir:  
  
     [$RootKey$ \Packages\\{87569308-4813-40a0-9cd0-d7a30838ca3f}]  
  
3.  Recompile a solução e iniciar a depuração do shell isolado. Abra um arquivo XML, por exemplo, \MyVSShellStub\MyVSShellStub\MyVSShellStubUI\MyVSShellStubUI.vsct. Verifique se as palavras-chave XML no arquivo são coloridas de não e que digitando "<" em uma linha não exibir dicas de ferramentas XML.  
  
## <a name="customizing-the-helpabout-box"></a>Personalizando a Ajuda/sobre caixa  
 Você pode personalizar a Ajuda/sobre caixa, que é criado como parte do modelo de projeto de shell isolado.  
  
#### <a name="to-customize-the-company-name"></a>Para personalizar o nome da empresa  
  
1.  O nome da empresa, informações sobre direitos autorais, versão do produto e descrição do produto são encontrados no projeto MyVSShellStub.AboutBoxPackage, no arquivo \Properties\AssemblyInfo.cs. Abra este arquivo.  
  
2.  Alterar o `AssemblyCompany` valor **Fabrikam**, o `AssemblyProduct` e `AssemblyTitle` valores **Fabrikam música Editor**e o `AssemblyCopyright` valor **Copyright © Fabrikam 2015**:  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")]  
    [assembly: AssemblyDescription("")]  
    [assembly: AssemblyConfiguration("")]  
    [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor ")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")]  
    ```  
  
3.  Para adicionar uma descrição do produto, altere o `AssemblyDescription` valor **a descrição do editor de música Fabrikam.**:  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.")]  
    ```  
  
4.  Iniciar a depuração e no aplicativo de shell isolado, abra o **ajuda / sobre** caixa. Você deve ver as cadeias de caracteres alteradas. O título da Ajuda/sobre caixa é o mesmo que o `AssemblyTitle` valor AssemblyInfo.  
  
5.  As propriedades do **ajuda/sobre** caixa em si são encontrados no arquivo MyVSShellStub.AboutBoxPackage\AboutBox.xaml. Para alterar a largura da Ajuda/sobre caixa, vá para o `AboutDialogStyle` bloquear e definir o `Width` propriedade 200:  
  
    ```  
    <Style x:Key="AboutDialogStyle" TargetType="Window">  
        <Setter Property="Height" Value="Auto" />  
        <Setter Property="Width" Value="200" />  
        <Setter Property="ShowInTaskbar" Value="False" />  
        <Setter Property="ResizeMode" Value="NoResize" />  
        <Setter Property="WindowStyle" Value="SingleBorderWindow" />  
        <Setter Property="SizeToContent" Value="Height" />  
    </Style>  
    ```  
  
6.  Recompile a solução e iniciar a depuração do shell isolado. A Ajuda/sobre caixa deve ser aproximadamente quadrado.  
  
## <a name="before-you-deploy-the-isolated-shell-application"></a>Antes de implantar o aplicativo de Shell isolado  
 Seu aplicativo de shell isolado pode ser instalado em qualquer computador que tenha o pacote redistribuível do Visual Studio Shell (isolado). Para obter mais informações sobre o pacote redistribuível, consulte o [Downloads do Visual Studio Extensibility](http://go.microsoft.com/fwlink/?LinkID=119298) site.  
  
## <a name="deploying-the-isolated-shell-application"></a>Implantar o aplicativo de Shell isolado  
 Implantar o aplicativo de shell isolado a um computador de destino ao criar um projeto de instalação. Você deve especificar estas coisas:  
  
-   O layout das pastas e arquivos no computador de destino.  
  
-   As condições de inicialização que garantem que o .NET Framework e o Visual Studio shell em tempo de execução são instaladas no computador de destino.  
  
 O procedimento a seguir, você precisará instalar o InstallShield Limited Edition no seu computador.  
  
#### <a name="to-create-the-setup-project"></a>Para criar o projeto de instalação  
  
1.  Em **Solution Explorer**, com o botão direito no nó da solução e, em seguida, clique em **adicionar novo projeto**.  
  
2.  No **novo projeto** caixa de diálogo caixa, expanda **outros tipos de projetos** e, em seguida, selecione **instalação e implantação**. Selecione o modelo do InstallShield. Nomeie o novo projeto `MySetup` e, em seguida, clique em **Okey**.  
  
3.  Se o InstallShield Limited Edition já estiver instalado, vá para a próxima etapa.  
  
     Se o InstallShield Limited Edition já não estiver instalado, a página de download do InstallShield é exibida. Siga as instruções para baixar e instalar o produto, escolha a versão do InstallShield é compatível com sua versão do Visual Studio. Você deve decidir se deve registrar a instalação do InstallShield ou usá-la como uma avaliação. Você deve reiniciar o Visual Studio depois de concluir a instalação.  
  
    > [!IMPORTANT]
    >  Você deve iniciar o Visual Studio como administrador antes de criar um projeto do InstallShield. Se você não fizer isso, você receberá um erro quando você compilar o projeto.  
  
 As próximas etapas mostram como configurar o projeto de instalação.  
  
> [!IMPORTANT]
>  Certifique-se de que você criou a configuração de versão de seu projeto de shell isolado pelo menos uma vez antes de configurar o projeto de instalação.  
  
#### <a name="to-configure-the-setup-project"></a>Para configurar o projeto de instalação  
  
1.  No **Gerenciador de soluções**, sob o **MySetup** de projeto, escolha **Assistente de projeto**. Na parte inferior do **Assistente de projeto** janela, escolha **informações do aplicativo**. Digite **Fabrikam** como o nome da empresa e **Fabrikam música Editor** como o nome do aplicativo. Clique na seta Avançar no canto inferior direito do **Assistente de projeto**.  
  
2.  Selecione **Sim** em **seu aplicativo requer qualquer software seja instalado na máquina?** e, em seguida, selecione **pacote completo do Microsoft .NET Framework 4.5**.  
  
3.  Escolha o **arquivos de aplicativo** botão na parte inferior da janela e, em seguida, verifique se o **Fabrikam música Editor** pasta está selecionada.  
  
4.  Escolha o **adicionar arquivos** botão. No **adicionar arquivos** caixa de diálogo caixa, adicione os seguintes arquivos do **MyVSShellStub\Release** pasta:  
  
    1.  MyVSShellStub.exe.config  
  
    2.  DebuggerProxy.dll  
  
    3.  Debuggerproxy.dll  
  
    4.  MyVSShellStub.pkgdef  
  
    5.  MyVSShellStub.pkgundef  
  
    6.  MyVSShellStub.winprf  
  
    7.  Splash.bmp  
  
5.  Clique o **adicionar saídas do projeto** botão e adicionar **MyVSShellStub/primário saída**. Clique em **OK**.  
  
6.  No painel esquerdo, em **computador de destino**, com o botão direito do **Fabrikam música Editor [INSTALLDIR]** nó e adicionar um **nova pasta** chamado **extensões**.  
  
7.  Clique com botão direito do **extensões** nó no painel esquerdo e adicione uma nova pasta chamada **aplicativo**.  
  
8.  Selecione o **aplicativo** pasta e clique no **adicionar saídas do projeto** botão e selecione a saída principal do projeto MyVSShellStub.AboutBoxPackage.  
  
9. Clique o **adicionar arquivos** botão e da pasta \MyVSShellStub\Release\Extensions\Application\, adicione os seguintes arquivos:  
  
    -   MyVSShellStub.AboutBoxPackage.pkgdef  
  
    -   MyVSShellStub.Application.pkgdef  
  
10. Clique com botão direito do **Fabrikam música Editor [INSTALLDIR]** nó no painel esquerdo e adicione uma nova pasta chamada **1033**.  
  
11. Selecione a pasta 1033 e, em seguida, clique no **adicionar saídas do projeto** botão e, em seguida, selecione a saída principal do projeto MyVSShellStubUI.  
  
12. Mover para o **atalhos de aplicativos** janela.  
  
13. Clique em **novo** para criar um atalho e selecione **\Fabrikam\Fabrikam Music Editor\MyVSShellStub.Primary Output [ProgramFilesFolder]**.  
  
14. Mover para o **instalação entrevista** painel.  
  
15. Definir todos os itens **não**.  
  
16. Em **Solution Explorer**, no projeto MySetup, abra **ações e definir os requisitos de configuração \ requisitos**. O **requisitos** janela será aberta.  
  
17. Clique com botão direito **requisitos de Software do sistema** e selecione **criar nova condição de inicialização**. O **Assistente de pesquisa do sistema** é exibida.  
  
18. No **o que você deseja localizar?** painel, escolha **entrada do registro** na lista suspensa e clique **próximo**.  
  
19. No **como você deseja procurar?** painel, selecione **HKEY_LOCAL_MACHINE** como a raiz do registro. Digite **SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** para sistemas de 64 bits ou **SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** para sistemas de 32 bits e digite **instalar** como o valor do registro. Clique em **Avançar**.  
  
20. No **o que você deseja fazer com o valor?** painel, digite **este produto requer o 2015 isolado Shell redistribuível do Visual Studio seja instalado.** como o texto de exibição e clique em **concluir**.  
  
21. Recompile a solução de shell isolado para criar o projeto de instalação.  
  
     Você pode encontrar o arquivo setup.exe na seguinte pasta:  
  
     \MyVSShellStub\MySetup\MySetup\Express\SingleImage\DiskImages\DISK1  
  
## <a name="testing-the-installation-program"></a>Teste o programa de instalação  
 Para testar a instalação, copie o arquivo setup.exe para um computador diferente e execute o executável de instalação. Você deve ser capaz de executar o aplicativo de shell isolado.
