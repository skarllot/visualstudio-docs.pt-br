---
title: "Como definir uma versão do .NET Framework como destino | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
ms.assetid: dea62d25-3d1b-492e-a6cc-b5154489800a
caps.latest.revision: 50
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: eea7cb983f264fb58a4b1131f84f3ec1cb196be5
ms.contentlocale: pt-br
ms.lasthandoff: 05/30/2017

---
# Como destinar uma versão do .NET Framework
<a id="how-to-target-a-version-of-the-net-framework" class="xliff"></a>
Este documento descreve como destinar uma versão do .NET Framework quando você cria um projeto e como alterar a versão de destino em um projeto existente do Visual Basic, Visual C# ou Visual F#.  
  
> [!IMPORTANT]
>  Para obter informações sobre como alterar a versão de destino de projetos do C++, consulte [Como modificar a estrutura de destino e o conjunto de ferramentas da plataforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).  
  
 **Neste tópico**  
  
-   [Definindo uma versão como destino ao criar um projeto](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_new)  
  
-   [Alterando a versão de destino](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing)  
  
##  <a name="bkmk_new"></a> Definindo uma versão como destino ao criar um projeto  
 Ao criar um projeto, a versão do .NET Framework à qual você o destina determina quais modelos é possível usar.  
  
> [!NOTE]
>  Nas edições Express do Visual Studio, é necessário criar o projeto primeiro e, em seguida, é possível alterar o destino, conforme descrito em [Alterando a versão de destino](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing), mais adiante neste tópico.  
  
#### Para destinar uma versão ao criar um projeto
<a id="to-target-a-version-when-you-create-a-project" class="xliff"></a>  
  
1.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
2.  Na lista da parte superior da caixa de diálogo **Novo Projeto**, escolha a versão do .NET Framework que você deseja que o projeto tenha como destino.  
  
    > [!NOTE]
    >  Normalmente, somente uma versão do .NET Framework é instalada com o Visual Studio. Se desejar destinar outra versão, primeiramente, você deve verificar se ela está instalada. Consulte [Visão geral do Visual Studio Multi-Targeting](../ide/visual-studio-multi-targeting-overview.md).  
  
3.  Na lista de modelos instalados, escolha o tipo de projeto que você deseja criar, nomeie o projeto e escolha o botão **OK**.  
  
     A lista de modelos mostra somente os projetos que são aceitos pela versão do .NET Framework que você escolheu.  
  
##  <a name="bkmk_existing"></a> Alterando a versão de destino  
 É possível alterar a versão de destino do .NET Framework em um projeto do Visual Basic, Visual C# ou Visual F# seguindo este procedimento.  
  
#### Para alterar a versão de destino
<a id="to-change-the-targeted-version" class="xliff"></a>  
  
1.  No **Gerenciador de Soluções**, abra o menu de atalho do projeto que você deseja alterar e, em seguida, escolha **Propriedades**.  
  
     ![Propriedades do Gerenciador de Soluções do Visual Studio](~/ide/media/vs_slnexplorer_properties.png "vs_slnExplorer_Properties")  
  
    > [!IMPORTANT]
    >  Para obter informações sobre como alterar a versão de destino de projetos do C++, consulte [Como modificar a estrutura de destino e o conjunto de ferramentas da plataforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).  
  
2.  Na coluna esquerda da janela Propriedades, escolha a guia **Aplicativo**.  
  
     ![Guia Aplicativo de Propriedades do Aplicativo do Visual Studio](../ide/media/vs_slnexplorer_properties_applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")  
  
    > [!NOTE]
    >  Depois de criar um aplicativo da Windows Store, não é possível alterar a versão de destino do Windows ou do .NET Framework.  
  
3.  Na lista **Estrutura de Destino**, escolha a versão desejada.  
  
4.  Na caixa de diálogo de verificação exibida, escolha o botão **Sim**.  
  
     O projeto é descarregado. Quando é recarregado, ele se destina à versão do .NET Framework que você acabou de escolher.  
  
    > [!NOTE]
    >  Se seu código contiver referências a outra versão do .NET Framework que não seja a que você o destinou, mensagens de erro poderão aparecer quando você compilar ou executar o código. Para resolver esses erros, você deverá modificar as referências. Consulte [Solução de problemas de erros de definição de destino do .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).  
  
## Consulte também
<a id="see-also" class="xliff"></a>  
 [Visão geral do Visual Studio Multi-Targeting](../ide/visual-studio-multi-targeting-overview.md)   
 [.NET Framework Multi-Targeting para projetos Web do ASP.NET](http://msdn.microsoft.com/Library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76)   
 [Solução de problemas de erros de definição de destino do .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)   
 [Página Aplicativo, Designer de Projeto (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Página de Aplicativo, Designer de Projeto (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [Configurando projetos](http://msdn.microsoft.com/Library/a1489abb-6294-4f8f-b71f-2cb126393526)   
 [Como modificar a estrutura de destino e o conjunto de ferramentas da plataforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)
