---
title: 'Passo a passo: Criando um SDK usando c# ou Visual Basic | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: 20
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
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: d40de5bedbb0e77aee2a0dbed34f8dc22d3835c9
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>Passo a passo: Criando um SDK usando c# ou Visual Basic
Este passo a passo, você aprenderá como criar um SDK de biblioteca de matemática simples usando o Visual c# e, em seguida, o SDK como um Visual Studio extensão (VSIX) do pacote. Você deverá concluir os procedimentos a seguir:  
  
-   [Para criar o componente de tempo de execução SimpleMath Windows](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
-   [Para criar o projeto de extensão SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
-   [Para criar um aplicativo de exemplo que usa a biblioteca de classe](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para acompanhar este passo a passo, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [SDK do Visual Studio](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a>Para criar o componente de tempo de execução SimpleMath Windows  
  
1.  Na barra de menus, escolha **arquivo**, **novo**, **novo projeto**.  
  
2.  Na lista de modelos, expanda **Visual C#** ou **Visual Basic**, escolha o **da Windows Store** nó e, em seguida, escolha o **decomponentedoWindowsRuntime** modelo.  
  
3.  No **nome** , especifique **SimpleMath**e, em seguida, escolha o **Okey** botão.  
  
4.  Em **Solution Explorer**, abra o menu de atalho para o **SimpleMath** nó do projeto e escolha **propriedades**.  
  
5.  Renomear **Class1.cs** para **Arithmetic.cs** e atualizá-lo de acordo com o código a seguir:  
  
     [!code-csharp[CreatingAnSDKUsingWinRT 3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)][!code-vb[CreatingAnSDKUsingWinRT n º 3  ](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]  
  
6.  Em **Solution Explorer**, abra o menu de atalho para o **solução 'SimpleMath'** nó e, em seguida, escolha **do Configuration Manager**.  
  
     O **do Configuration Manager** caixa de diálogo é aberta.  
  
7.  No **configuração de solução ativa** , escolha **versão**.  
  
8.  No **configuração** coluna, verifique **SimpleMath** linha é definida como **versão**e, em seguida, escolha o **fechar** botão para aceitar o Altere.  
  
    > [!IMPORTANT]
    >  O SDK para o componente SimpleMath inclui somente uma configuração. Essa configuração deve ser a compilação de lançamento ou aplicativos que usam o componente não passam na certificação o[!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)].  
  
9. Em **Solution Explorer**, abra o menu de atalho para o **SimpleMath** nó do projeto e escolha **criar**.  
  
##  <a name="createVSIX"></a>Para criar o projeto de extensão SimpleMathVSIX  
  
1.  No menu de atalho para o **solução 'SimpleMath'** nó, escolha **adicionar**, **novo projeto**.  
  
2.  Na lista de modelos, expanda **Visual C#** ou **Visual Basic**, escolha o **extensibilidade** nó e, em seguida, escolha o **projeto VSIX** modelo.  
  
3.  No **nome** , especifique **SimpleMathVSIX**e, em seguida, escolha o **Okey** botão.  
  
4.  Em **Solution Explorer**, escolha o **source.extension.vsixmanifest** item.  
  
5.  Na barra de menus, escolha **Exibir**, **Código**.  
  
6.  Substitua o XML existente com o seguinte XML:  
  
     [!code-xml[CreatingAnSDKUsingWinRT n º 1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7.  Em **Solution Explorer**, escolha o **SimpleMathVSIX** projeto.  
  
8.  Na barra de menus, escolha **projeto**, **Adicionar Novo Item**.  
  
9. Na lista de **itens comuns**, expanda **dados**e, em seguida, escolha **arquivo XML**.  
  
10. No **nome** , especifique `SDKManifest.xml`e, em seguida, escolha o **adicionar** botão.  
  
11. Em **Solution Explorer**, abra o menu de atalho para `SDKManifest.xml`, escolha **propriedades**e, em seguida, altere o valor da **incluir VSIX** propriedade **True**.  
  
12. Substitua o conteúdo do arquivo pelo XML a seguir:  

    **C#**
    ```xml
    <FileList
      DisplayName="WinRT Math Library (CS)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="http://www.msdn.microsoft.com/">
    </FileList>
    ```

    **Visual Basic**
    ```xml
    <FileList
      DisplayName="WinRT Math Library (VB)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="http://www.msdn.microsoft.com/">
    </FileList>
    ```  
  
13. Em **Solution Explorer**, abra o menu de atalho para o **SimpleMathVSIX** de projeto, escolha **adicionar**e, em seguida, escolha **nova pasta**.  
  
14. Renomear a pasta para `references`.  
  
15. Abra o menu de atalho para o **referências** pasta, escolha **adicionar**e, em seguida, escolha **nova pasta**.  
  
16. Renomeie a subpasta `commonconfiguration`, crie uma subpasta dentro dele e nomeie a subpasta `neutral`.  
  
17. Repita as quatro etapas anteriores, desta vez, a primeira pasta para a renomeação `redist`.  
  
     O projeto agora contém a seguinte estrutura de pasta:  
  
    ```
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. Em **Solution Explorer**, abra o menu de atalho para o **SimpleMath** do projeto e, em seguida, escolha **Abrir pasta no Explorador de arquivos**.  
  
19. Em **Explorador de arquivos**, navegue até a pasta bin\Release, abra o menu de atalho para o arquivo SimpleMath.winmd e, em seguida, escolha **cópia**.  
  
20. Em **Solution Explorer**, cole o arquivo na pasta references\commonconfiguration\neutral no **SimpleMathVSIX** projeto.  
  
21. Repita a etapa anterior, colar o arquivo SimpleMath.pri para a pasta redist\commonconfiguration\neutral no **SimpleMathVSIX** projeto.  
  
22. Em **Solution Explorer**, escolha **SimpleMath.winmd**.  
  
23. Na barra de menus, escolha **exibição**, **propriedades** (teclado: escolha a tecla F4).  
  
24. No **propriedades** janela, altere o **ação de compilação** propriedade **conteúdo**e, em seguida, altere o **incluir VSIX** propriedade  **True**.  
  
25. Em **Solution Explorer**, repita esse processo para **SimpleMath.pri**.  
  
26. Em **Solution Explorer**, escolha o **SimpleMathVSIX** projeto.  
  
27. Na barra de menus, escolha **criar**, **SimpleMathVSIX criar**.  
  
28. Em **Solution Explorer**, abra o menu de atalho para o **SimpleMathVSIX** do projeto e, em seguida, escolha **Abrir pasta no Explorador de arquivos**.  
  
29. Em **Explorador de arquivos**, navegue até a pasta \bin\Release. e, em seguida, execute SimpleMathVSIX.vsix para instalá-lo.  
  
30. Escolha o **instalar** botão, aguarde a conclusão da instalação e, em seguida, reinicie o Visual Studio.  
  
##  <a name="createSample"></a>Para criar um aplicativo de exemplo que usa a biblioteca de classe  
  
1.  Na barra de menus, escolha **arquivo**, **novo**, **novo projeto**.  
  
2.  Na lista de modelos, expanda **Visual C#** ou **Visual Basic**e, em seguida, escolha o **da Windows Store** nó.  
  
3.  Escolha o **aplicativo em branco** modelo, nomeie o projeto **ArithmeticUI**e, em seguida, escolha o **Okey** botão.  
  
4.  Em **Solution Explorer**, abra o menu de atalho para o **ArithmeticUI** do projeto e, em seguida, escolha **adicionar**, **referência**.  
  
5.  Na lista de tipos de referência, expanda **Windows**e, em seguida, escolha **extensões**.  
  
6.  No painel de detalhes, escolha o **SDK de matemática simples** extensão.  
  
     Informações adicionais sobre o SDK é exibida. Você pode escolher o **informações mais** link para abrir http://www.msdn.microsoft.com, conforme especificado no arquivo SDKManifest.xml, anteriormente neste passo a passo.  
  
7.  No **Gerenciador de referências** caixa de diálogo, selecione o **SDK de matemática simples** caixa de seleção e, em seguida, escolha o **Okey** botão.  
  
8.  Na barra de menus, escolha **exibição**, **Pesquisador de objetos**.  
  
9. No **procurar** , escolha **matemáticos simples**.  
  
     Agora você pode explorar Novidades no SDK.  
  
10. Em **Solution Explorer**, abra MainPage. XAML e substitua o seu conteúdo com o XAML a seguir:  

    **C#**
    ```xml
    <Page
        x:Class="WinRTMathTestCS.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WinRTMathTestCS"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```
    
    **Visual Basic**
    ```xml
    <Page
        x:Class="WinRTMathTest.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WinRTMathTest"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```
  
11. Atualize MainPage.xaml.cs para coincidir com o código a seguir:  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp 2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)][!code-vb[CreatingAnSDKUsingWinRTDemoApp n º 2  ](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]  
  
12. Pressione a tecla F5 para executar o aplicativo.  
  
13. No aplicativo, insira qualquer dois números, escolha uma operação e, em seguida, escolha o  **=**  botão.  
  
     O resultado correto é exibido.  
  
 Você criou e usado um SDK de extensão com êxito.  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Criando um SDK usando C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Passo a passo: Criando um SDK usando JavaScript](http://msdn.microsoft.com/en-us/6195ff56-4a27-45fc-bd29-4b0451225f4b)   
 [Criar um Software Development Kit](../extensibility/creating-a-software-development-kit.md)
