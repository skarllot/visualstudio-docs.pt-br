---
title: "O que há de novo no SDK do Visual Studio 2015 | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 13
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
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: 8d77fce54b12b90f6a2632fd1c1741990be42a08
ms.lasthandoff: 02/22/2017

---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>O que há de novo no SDK do Visual Studio 2015
O SDK do Visual Studio tem os seguintes recursos novos e atualizados para o Visual Studio 2015, Visual Studio 2015 atualizado e 2017 do Visual Studio.  
  
## <a name="vs-2015-sdk-update-1"></a>Atualização do SDK do VS 2015 1  
 Atualização 1 inclui ferramentas para ajudar a sua extensão funcionam bem com temas de cores e o serviço de imagem do Visual Studio.  
  
 Esses tópicos estão sob o [VSSDK utilitários](../extensibility/internals/vssdk-utilities.md) seção:  
  
-   O [ferramentas de temas de cores](../extensibility/internals/color-theming-tools.md) ajudá-lo a criar e editar cores personalizadas para o Visual Studio.  
  
-   O [ferramentas de serviço de imagem](../extensibility/internals/image-service-tools.md) permitem que você trabalhe com arquivos de manifesto de imagem do Visual Studio.  
  
## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Nova maneira de adicionar o SDK do Visual Studio para o Visual Studio  
 A partir do Visual Studio 2015, você não precisa fazer o download do SDK do Visual Studio separadamente. Em vez disso, você pode instalá-lo como parte do processo de instalação normal, ou você pode optar por instalá-lo mais tarde. Quando você abre ou cria uma solução VSIX, Visual Studio solicitará que você instale as ferramentas de extensibilidade do Visual Studio. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="new-ways-of-creating-extensions"></a>Novas maneiras de criar extensões  
 A partir do SDK do Visual Studio 2015, você tem opções diferentes para criar extensões, dependendo da linguagem de programação que você está usando.  
  
### <a name="visual-c-and-visual-basic"></a>Visual C# e Visual Basic  
 Para c# e Visual Basic, há uma ampla variedade de modelos de item de projeto que permitem que você crie os VSPackages, comandos de menu, janelas de ferramenta, classificadores de editor, editor ornamentos e extensões de margem do editor. Você pode adicionar qualquer ou todos eles para o projeto do VSIX padrão. Para obter mais informações, consulte:  
  
-   [Criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   [Criando uma extensão com uma janela de ferramentas](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   [Criando uma extensão com um modelo de Item Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   [Criando uma extensão com um VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
     O Assistente de VSPackage não cria mais extensões em c# ou Visual Basic.  
  
### <a name="c"></a>C++  
 Para C++, o Assistente de VSPackage suporte a editores personalizados, janelas de ferramentas e comandos de menu. Procure no **novo projeto** caixa de diálogo no **Visual C++ / extensibilidade**.  
  
## <a name="vs-sdk-reference-assemblies-via-nuget"></a>Assemblies de referência SDK do VS por meio do NuGet  
 Para maior portabilidade e compartilhamento de projetos de extensibilidade, você pode usar as versões do NuGet dos assemblies de referência do SDK do VS.  Eles estão disponíveis em [nuget.org](http://www.nuget.org) publicado por [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) e podem ser facilmente adicionados ao seu projeto ou solução por meio do Visual Studio **referencia / gerenciar pacotes NuGet** caixa de diálogo. Você pode adicionar individuais referências aos assemblies de extensibilidade específica ou adicione o SDK do VS referencia assemblies ao mesmo tempo usando o SDK do VS [pacote Meta](http://www.nuget.org/packages/VSSDK_Reference_Assemblies). Para saber mais sobre o NuGet, consulte [visão geral do NuGet](http://docs.nuget.org/) e [gerenciar pacotes de NuGet usando a caixa de diálogo](http://docs.nuget.org/Consume/Package-Manager-Dialog).  
  
 Quando você usa as versões do NuGet dos assemblies de referência do SDK do VS, outro usuário não precisa instalar o SDK do VS para abrir e criar seu projeto.  Os assemblies de referência do NuGet e ferramentas de compilação do SDK do VS serão instaladas automaticamente em seu computador para o projeto.  
  
 Os modelos de item do SDK do VS usam NuGet para suas referências e ferramentas de compilação para que você obtenha os benefícios do NuGet por padrão.  
  
> [!NOTE]
>  Você pode continuar a usar os assemblies de referência do SDK do VS instalado com seus projetos (localizado em \<local de instalação do Visual Studio > \ VSSDK\VisualStudioIntegration\Common\Assemblies) e projetos de extensibilidade existentes não precisam ser atualizados para usar os pacotes do NuGet.  O projeto **referencia / adicionar referência** caixa de diálogo continuará a usar os assemblies de referência do SDK do VS instalado.  
>   
>  Se você quiser modificar seus projetos existentes para usar o NuGet, consulte [como: VSPackages migrar para o Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) que tem uma seção sobre como atualizar projetos de extensibilidade para pacotes do NuGet.  
  
## <a name="light-bulbs"></a>Lâmpadas  
 Uma das maneiras de novo mais interessantes de escrever código de extensão é fornecida pelo projeto Roslyn. Para obter mais informações, consulte [Roslyn](https://github.com/dotnet/Roslyn).  
  
 As lâmpadas são um novo recurso que acompanha o VSSDK. Eles são os ícones usados no editor do Visual Studio que se expandem para exibir um conjunto de ações de refatoração de código ou correções para problemas identificados pelos analisadores de código internos. Para obter mais informações, consulte [passo a passo: exibindo sugestões de lâmpada](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
## <a name="updated-user-experience-guidelines"></a>Diretrizes de experiência do usuário atualizada  
 Criando novas extensões ou recursos para o Visual Studio? Confira atualizado e expandida [diretrizes de experiência de usuário do Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Você encontrará o [tokens de cores](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [tamanhos de fonte](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [especificações de layout de caixa de diálogo](../extensibility/ux-guidelines/layout-for-visual-studio.md)e outras diretrizes necessárias para integrar a nova interface do usuário com o Visual Studio.
