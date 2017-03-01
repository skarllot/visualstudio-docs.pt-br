---
title: Estendendo o Shell isolado | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: 10
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
ms.openlocfilehash: cacd731802edbde4733b217a12271c61fa5ddf44
ms.lasthandoff: 02/22/2017

---
# <a name="extending-the-isolated-shell"></a>Estendendo o Shell isolado
Você pode estender o shell do Visual Studio isolada, adicionando um VSPackage, uma parte de componente Managed Extensibility Framework (MEF) ou um projeto do VSIX genérico para o seu aplicativo de shell isolado.  
  
> [!NOTE]
>  As etapas a seguir pressupõem que você criou um aplicativo de shell isolado básico usando o modelo de projeto Visual Studio Shell isolado. Para obter mais informações sobre este modelo de projeto, consulte [passo a passo: Criando um aplicativo de Shell isolado básico](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Locais para o modelo de projeto de pacote do Visual Studio  
 O modelo de projeto do pacote do Visual Studio pode ser encontrado em três locais diferentes de **novo projeto** caixa de diálogo:  
  
1.  Em **Visual Basic**, **extensibilidade**. O idioma padrão do projeto é Visual Basic.  
  
2.  Em **Visual C#**, **extensibilidade**. O idioma padrão do projeto é c#.  
  
3.  Em **outros tipos de projeto**, **extensibilidade**. O idioma padrão do projeto é C++.  
  
## <a name="adding-a-vspackage"></a>Adicionando um VSPackage  
 Você pode adicionar um VSPackage ao seu aplicativo de shell isolado. As etapas a seguir mostram como criar uma que adiciona os comandos de menu.  
  
#### <a name="to-add-a-new-vspackage"></a>Para adicionar um novo VSPackage  
  
1.  Adicione um projeto de pacote do Visual Studio chamado `MenuCommandsPackage`.  
  
2.  Sobre o **informações básicas sobre o VSPackage** página do assistente, definir **nome da empresa** para `Fabrikam` e **VSPackage nome** para `FabrikamMenuCommands`. Escolha o **próxima** botão.  
  
3.  Na página seguinte, selecione **o comando de Menu** e, em seguida, escolha **próxima**.  
  
4.  Na página seguinte, defina **nome do comando** para `Fabrikam Command` e **ID de comando** para `cmdidFabrikamCommand`e, em seguida, escolha **próxima**.  
  
5.  Sobre o **selecionar opções de projeto de teste** página, desmarque as opções de teste e, em seguida, escolha o **concluir** botão.  
  
6.  No projeto ShellExtensionsVSIX, abra o arquivo source.extension.vsixmanifest.  
  
     O **ativos** seção deve conter uma entrada para o projeto VSShellStub.AboutBoxPackage.  
  
7.  Escolha o **novo** botão.  
  
8.  No **adicionar novo ativo** janela, no **tipo** lista, selecione **Microsoft.VisualStudio.VsPackage**.  
  
9. No **fonte** lista, certifique-se de que **um projeto na solução atual** está selecionado. No **projeto** caixa de listagem, selecione **MenuCommandsPackage**.  
  
10. Salve e feche o arquivo.  
  
11. Recompile a solução e iniciar a depuração de shell isolado.  
  
12. Na barra de menus, escolha **ferramentas** menu, em seguida, **Fabrikam comando**.  
  
     Deve aparecer uma caixa de mensagem.  
  
13. Pare a depuração do aplicativo.  
  
## <a name="adding-a-mef-component-part"></a>Adicionando uma parte do componente MEF  
 As etapas a seguir mostram como adicionar uma parte do componente MEF em seu aplicativo de shell isolado.  
  
#### <a name="to-add-a-mef-component"></a>Para adicionar um componente MEF  
  
1.  No **adicionar novo projeto** caixa de diálogo **Visual C#**, **extensibilidade**, use o **margem do Editor** modelo para adicionar um projeto. Nomeie-o `ShellEditorMargin`.  
  
2.  No projeto ShellExtensionsVSIX, abra o arquivo Source.extension.vsixmanifest no modo Design, não o modo de exibição de código.  
  
3.  No `Asset` seção, escolha **adicionar conteúdo**.  
  
4.  No **adicionar novo ativo** janela, no **tipo** lista, selecione **Microsoft.VisualStudio.MefComponent**.  
  
5.  No **fonte** lista, certifique-se de que **um projeto na solução atual** está selecionado. No **projeto** caixa de listagem, selecione **ShellEditorMargin**.  
  
6.  Salve e feche o arquivo.  
  
7.  Recompile a solução e iniciar a depuração de shell isolado.  
  
8.  Abra um arquivo de texto.  
  
     Uma margem verde que contém as palavras "Hello world!" deve ser exibido na parte inferior da janela de arquivo de texto.  
  
9. Pare a depuração do aplicativo.  
  
## <a name="adding-a-generic-vsix-project"></a>Adicionando um projeto do VSIX genérico  
  
#### <a name="to-add-a-generic-vsix-project"></a>Para adicionar um projeto do VSIX genérico  
  
1.  No **adicionar novo projeto** caixa de diálogo **Visual C#**, **extensibilidade**, use o **VSIXProject** modelo para adicionar um projeto. Nomeie-o `EmptyVSIX`.  
  
2.  No projeto ShellExtensionsVSIX, abra o arquivo Source.extensions.vsixmanifest no modo Design, não o modo de exibição de código.  
  
3.  No `Assets` seção, escolha **novo**.  
  
4.  No **adicionar novo ativo** janela, no **tipo** , selecione o tipo de conteúdo que você deseja adicionar.  
  
5.  Em **fonte**, verifique se o **um projeto na solução atual** está selecionada. Na caixa de listagem, selecione o nome do seu projeto do VSIX.  
  
6.  Salve e feche o arquivo.  
  
7.  Se esse projeto inclui código compilado, você deve editar o projeto para que o assembly seja incluído na saída.  
  
    1.  Descarregue o projeto do VSIX e abra o arquivo de projeto.  
  
    2.  Na primeira `<PropertyGroup>` bloquear, altere o valor de `<CopyBuildOutputToOutputDirectory>` para `true`.  
  
    3.  Salve e recarregue o projeto.  
  
8.  Criar e executar a solução.  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Criando um aplicativo básico Shell isolado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)
