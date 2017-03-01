---
title: 'Passo a passo: Criando um SDK usando C++ | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 32
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
ms.sourcegitcommit: d4458cb2cf0f3f198b2931beec15f8eead446ba6
ms.openlocfilehash: 3baf914755f0cdd4e0aa0a6c1405126faeec0364
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-creating-an-sdk-using-c"></a>Passo a passo: Criando um SDK usando C++
Este passo a passo mostra como criar uma nativo C++ biblioteca de matemática SDK, o pacote do SDK como uma extensão do Visual Studio (VSIX) e então usá-lo para criar um aplicativo. Passo a passo é dividida nestas etapas:  
  
-   [Para criar o nativo e as bibliotecas de tempo de execução do Windows](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [Para criar o projeto de extensão NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [Para criar um aplicativo de exemplo que usa a biblioteca de classes](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para seguir este passo a passo, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="a-namecreateclasslibrarya-to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a>Para criar o nativo e as bibliotecas de tempo de execução do Windows  
  
1.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
2.  Na lista de modelos, expanda **Visual C++**, **da Windows Store**e, em seguida, selecione o **DLL (aplicativos da Windows Store)** modelo. No **nome** , especifique `NativeMath`e, em seguida, escolha o **Okey** botão.  
  
3.  Atualize NativeMath.h para coincidir com o código a seguir.  
  
     [!code-cpp[CreatingAnSDKUsingCpp n º&1;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]  
  
4.  Atualize NativeMath.cpp de acordo com este código:  
  
     [!code-cpp[CreatingAnSDKUsingCpp n º&2;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]  
  
5.  Em **Solution Explorer**, abra o menu de atalho para **solução 'NativeMath'**e, em seguida, escolha **adicionar**, **novo projeto**.  
  
6.  Na lista de modelos, expanda **Visual C++**e, em seguida, selecione o **o componente de tempo de execução do Windows** modelo. No **nome** , especifique `NativeMathWRT`e, em seguida, escolha o **Okey** botão.  
  
7.  Atualize Class1.h de acordo com este código:  
  
     [!code-cpp[CreatingAnSDKUsingCpp n º&3;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]  
  
8.  Atualize Class1.cpp de acordo com este código:  
  
     [!code-cpp[CreatingAnSDKUsingCpp n º&4;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]  
  
9. Na barra de menus, escolha **Compilar**, **Compilar Solução**.  
  
##  <a name="a-namecreatevsixa-to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a>Para criar o projeto de extensão NativeMathVSIX  
  
1.  Em **Solution Explorer**, abra o menu de atalho para **solução 'NativeMath'**e, em seguida, escolha **adicionar**, **novo projeto**.  
  
2.  Na lista de modelos, expanda **Visual C#**, **extensibilidade**e, em seguida, selecione **pacote VSIX**. No **nome** , especifique **NativeMathVSIX**e, em seguida, escolha o **Okey** botão.  
  
3.  Quando o designer de manifesto VSIX for exibida, feche-o.  
  
4.  Em **Solution Explorer**, abra o menu de atalho para **source.extension.vsixmanifest**e, em seguida, escolha **Exibir código**.  
  
5.  Use o XML a seguir para substituir o XML existente.  
  
    [!code-xml[CreatingAnSDKUsingCpp n º&6;](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

6.  Em **Solution Explorer**, abra o menu de atalho para o **NativeMathVSIX** do projeto e escolha **adicionar**, **Novo Item**.  
  
7.  Na lista de **itens do Visual c#**, expanda **dados**e, em seguida, selecione **arquivo XML**. No **nome** , especifique `SDKManifest.xml`e, em seguida, escolha o **Okey** botão.  
  
8.  Use esse XML para substituir o conteúdo do arquivo:  
  
     [!code-xml[CreatingAnSDKUsingCpp n º&5;](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]  
  
9. Em **Solution Explorer**, no **NativeMathVSIX** de projeto, crie a estrutura de pastas:  
  
    ```  
  
    \DesignTime  
          \CommonConfiguration  
                \Neutral  
                      \Include  
          \Debug  
                \x86  
    \Redist  
          \Debug  
                \x86  
    \References  
          \CommonConfiguration  
                \Neutral  
    ```  
  
10. Em **Solution Explorer**, abra o menu de atalho para **solução 'NativeMath'**e, em seguida, escolha **Abrir pasta no Explorador de arquivos**.  
  
11. Em **Explorador de arquivos**, copie \NativeMath\NativeMath.h e, em seguida, em **Solution Explorer**, no **NativeMathVSIX** de projeto, cole-o na pasta \DesignTime\CommonConfiguration\Neutral\Include\.  
  
     Copie \Debug\NativeMath\NativeMath.lib e, em seguida, cole-o na pasta \DesignTime\Debug\x86\.  
  
     Copie \Debug\NativeMath\NativeMath.dll e cole-o na pasta \Redist\Debug\x86\.  
  
     Copie DebugNativeMathWRTNativeMathWRT.dll e cole-o na pasta RedistDebugx86.  
  
     Copie DebugNativeMathWRTNativeMathWRT.winmd e cole-o na pasta ReferencesCommonConfigurationNeutral.  
  
     Copie DebugNativeMathWRTNativeMathWRT.pri e cole-o na pasta ReferencesCommonConfigurationNeutral.  
  
12. Na pasta \DesignTime\Debug\x86\, crie um arquivo de texto chamado NativeMathSDK.props e, em seguida, cole o seguinte conteúdo nele:  
  
    [!code-xml[CreatingAnSDKUsingCpp&#7;](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. Na barra de menus, escolha **exibição**, **outras janelas**, **janela propriedades** (teclado: escolha a tecla F4).  
  
14. Em **Solution Explorer**, selecione o **NativeMathWRT.winmd** arquivo. No **propriedades** janela, alterar o **Build Action** propriedade **conteúdo**e altere o **incluir na VSIX** propriedade **True**.  
  
     Repita esse processo para o **SimpleMath.pri** arquivo.  
  
     Repita esse processo para o **NativeMath.Lib** arquivo.  
  
     Repita esse processo para o **NativeMathSDK.props** arquivo.  
  
15. Em **Solution Explorer**, selecione o **NativeMath.h** arquivo. No **propriedades** janela, alterar o **incluir na VSIX** propriedade **True**.  
  
     Repita esse processo para o **NativeMath.dll** arquivo.  
  
     Repita esse processo para o **NativeMathWRT.dll** arquivo.  
  
     Repita esse processo para o **Sdkmanifest** arquivo.  
  
16. Na barra de menus, escolha **Compilar**, **Compilar Solução**.  
  
17. Em **Solution Explorer**, abra o menu de atalho para o **NativeMathVSIX** do projeto e escolha **Abrir pasta no Explorador de arquivos**.  
  
18. Em **File Explorer**, navegue até a pasta \bin\Debug\ e execute NativeMathVSIX.vsix para iniciar a instalação.  
  
19. Escolha o **instalar** botão, aguarde concluir a instalação e reinicie o Visual Studio.  
  
##  <a name="a-namecreatesamplea-to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>Para criar um aplicativo de exemplo que usa a biblioteca de classes  
  
1.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
2.  Na lista de modelos, expanda **Visual C++**, **da Windows Store**e, em seguida, selecione **aplicativo em branco**. No **nome** , especifique **NativeMathSDKSample**e, em seguida, escolha o **Okey** botão.  
  
3.  Em **Solution Explorer**, abra o menu de atalho para o **NativeMathSDKSample** do projeto e escolha **adicionar**, **referência**.  
  
4.  Sobre o **propriedades comuns**, **estrutura e referências** página de propriedades, na lista de tipos de referência, expanda **Windows**e, em seguida, selecione **extensões**. No painel de detalhes, selecione a **nativo SDK matemática** extensão e, em seguida, escolha o **adicionar nova referência** botão.  
  
5.  No **adicionar referência** caixa de diálogo, selecione o **nativo SDK matemática** caixa de seleção e, em seguida, escolha o **Okey** botão.  
  
6.  Exiba as propriedades de projeto NativeMathSDKSample.  
  
     As propriedades que você definiu no NativeMathSDK.props foram aplicadas ao adicionar a referência. Você pode verificar isso examinando o **diretórios VC + +** propriedade do projeto **propriedades de configuração**.  
  
7.  Em **Solution Explorer**, abra MainPage. XAML e, em seguida, usar o XAML a seguir para substituir seu conteúdo:  
  
     [!code-xml[CreatingAnSDKUsingCppDemoApp n º&1;](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]  
  
8.  Atualize Mainpage.xaml.h de acordo com este código:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp n º&2;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]  
  
9. Atualize MainPage.xaml.cpp de acordo com este código:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp n º&3;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]  
  
10. Escolha a tecla F5 para executar o aplicativo.  
  
11. No aplicativo, digite os dois números, selecione uma operação e, em seguida, escolha o ** = ** botão.  
  
     O resultado correto é exibido.  
  
 Este passo a passo mostrou como criar e usar um SDK de extensão para chamar um [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] biblioteca e não[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] biblioteca.  
  
## <a name="next-steps"></a>Próximas etapas  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Criando um SDK usando c# ou Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Criando um Kit de desenvolvimento de Software](../extensibility/creating-a-software-development-kit.md)
