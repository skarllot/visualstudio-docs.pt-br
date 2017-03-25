---
title: "Começando a desenvolver extensões do Visual Studio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
caps.latest.revision: 29
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
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: dc5416fe979ed3e52ef2df77e5b495cb98038dcd
ms.lasthandoff: 03/07/2017

---
# <a name="starting-to-develop-visual-studio-extensions"></a>Começando a desenvolver extensões do Visual Studio
Se você nunca escreveu uma extensão do Visual Studio antes, você provavelmente tem algumas dúvidas. Apresentaremos alguns dos mais comuns aqui. Se você não vir as informações que você está procurando, use os botões de comentários (**esta página foi útil?** na parte inferior da tela) para solicitar que você deseja.  
  
## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>O software necessário desenvolver extensões do Visual Studio?  
 Você precisa instalar o SDK do Visual Studio, além do Visual Studio para desenvolver extensões do Visual Studio. Você pode instalar o SDK do Visual Studio como parte da instalação normal ou pode instalá-lo mais tarde. Para obter mais informações sobre como instalar o SDK do Visual Studio, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Que tipos de coisas pode fazer com as extensões do Visual Studio?  
 O céu está o limite quando se trata de imaginando diferentes extensões do Visual Studio. Obviamente, a maioria das extensões tem algo a ver com a escrita de código, mas que não precisa ser o caso. Aqui estão alguns exemplos dos tipos de extensões, que você pode criar:  
  
-   Suporte a idiomas que não estão incluídos no Visual Studio, com coloração de sintaxe, IntelliSense e suporte de compilador e de depuração  
  
-   Ferramentas de produtividade que ampliam o núcleo IDE experiência com outros modelos, caixas de diálogo Novo, refatoração de código ou janelas de ferramenta  
  
-   Designers específicos de domínio para cenários como suporte de nuvem ou design de dados  
  
 Para obter exemplos de extensões, confira o [Galeria do Visual Studio](https://visualstudiogallery.msdn.microsoft.com/). Você também pode dar uma olhada no [Visual Studio Open Source Extensions](https://github.com/Microsoft/extendvs/blob/master/CommunityExtensions.md).  
  
## <a name="which-visual-studio-features-can-i-extend"></a>Quais recursos do Visual Studio pode estender?  
 Em teoria, você pode estender qualquer parte do Visual Studio: menus, barras de ferramentas, comandos, windows, soluções, projetos, editores e assim por diante.  
  
 Na prática, descobrimos que os recursos que a maioria das pessoas que deseja estender são comandos, menus e barras de ferramentas, windows, IntelliSense e projetos. Aqui estão links para as seções relevantes:  
  
-   [Estendendo os Menus e comandos](../extensibility/extending-menus-and-commands.md): adicionar seus próprios itens de menus do Visual Studio e barras de ferramentas. Você pode usá-los para iniciar a nova funcionalidade do Visual Studio ou seus próprios aplicativos de ajuda externo. Você também pode fornecer atalhos personalizados para seus itens de menu.  
  
-   [Estendendo e personalizando janelas de ferramenta](../extensibility/extending-and-customizing-tool-windows.md): estender janelas de ferramentas existentes ou criar suas próprias janelas de ferramenta. Por exemplo, você pode adicionar novas propriedades para o **propriedades**, ou você pode criar uma nova janela de ferramenta para adicionar recursos adicionais.  
  
-   [Editor e extensões do serviço de linguagem](../extensibility/editor-and-language-service-extensions.md): adicionar suas próprias personalizações o IntelliSense fornecido para linguagens do Visual Studio ou criar suporte para novas linguagens de programação. Você pode criar novos conclusões, sugestões e dicas de ferramenta Informaçãorápida novo. Com lâmpadas, você pode adicionar refatoração sugestões e correções de código para oferecer suporte a novas linguagens de programação.  
  
-   [Estender projetos](../extensibility/extending-projects.md)  
  
-   [Estender opções e configurações de usuário](../extensibility/extending-user-settings-and-options.md)  
  
-   [Estender propriedades e a janela de propriedades](../extensibility/extending-properties-and-the-property-window.md)  
  
-   [Estender outras partes do Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
  
-   [Shell isolado do Visual Studio](../extensibility/visual-studio-isolated-shell.md)  
  
##  <a name="BKMK_ProjectTemplate"></a>Quais modelos de projeto são fornecidos pelo VSSDK?  
 Os dois tipos principais de extensões são extensões VSPackages e MEF. Em geral, as extensões de VSPackage são usadas para extensões que utilizam ou estendem os projetos, janelas de ferramentas e comandos. Extensões do MEF são usadas para estender ou personalizar o editor do Visual Studio.  
  
 Para extensões do Visual c# e Visual Basic, o VSSDK fornece um modelo de projeto VSIX vazio que pode ser usado junto com os novos modelos de item que criam comandos de menu, janelas de ferramentas e extensões do editor. Você também pode usar este modelo para modelos de projeto do pacote, trechos de código e outros artefatos para distribuição a outros usuários.  
  
 Para C++, o Assistente de VSPackage fornece o código para adicionar comandos de menu, janelas de ferramenta e editores personalizados.  
  
 O modelo de Shell isolado é usado para empacotar uma extensão em uma versão do shell do Visual Studio que você pode colocar a marca e distribuir como seu próprio. Os tópicos a seguir mostram como começar a usar cada tipo de extensão:  
  
-   Comandos de menu: [criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   Janelas de ferramentas: [criando uma extensão com uma janela de ferramentas](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   Extensões do Editor: [criando uma extensão com um modelo de Item Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   Os VSPackages básicos: [criando uma extensão com um VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
-   Modelo de projeto do VSIX: [Noções básicas sobre o modelo de projeto do VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)  
  
-   Visual Studio isolada shell: [passo a passo: Criando um aplicativo básico de Shell isolado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Como obtenho minha extensão para se parecer com o Visual Studio?  
 Obter ótimas dicas para projetar a interface do usuário para a sua extensão em [diretrizes de experiência de usuário do Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="where-can-i-find-examples-of-vssdk-code"></a>Onde posso encontrar exemplos de código VSSDK?  
 Cada um dos links listados na seção anterior têm orientações passo a passo que mostram como implementar recursos específicos. Também é possível encontrar código-fonte aberto VSSDK exemplos no GitHub em [exemplos do Visual Studio](https://aka.ms/vs2015sdksamples).  
  
## <a name="how-can-i-distribute-my-extension"></a>Como distribuir o meu extensão?  
 Você pode instalar a extensão em outro computador ou enviá-lo para seus amigos como um arquivo. VSIX, que você instalar clicando duas vezes nele. Você pode encontrar mais informações sobre pacotes VSIX em [envio extensões do Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
 Você também pode publicar sua extensão na Galeria do Visual Studio, que é visível para um grande número de clientes do Visual Studio. Para obter um exemplo de empacotamento de uma extensão para a Galeria, consulte [passo a passo: publicando uma extensão do Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Para obter mais informações sobre o que você precisa fazer para publicar na galeria, consulte [produtos e extensões do Visual Studio](https://visualstudiogallery.msdn.microsoft.com/).
