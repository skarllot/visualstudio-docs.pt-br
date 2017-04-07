---
title: SDK do Visual Studio | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: 56
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
ms.openlocfilehash: b3cd444e48893057a057c39c515e51ff8b509b34
ms.lasthandoff: 03/07/2017

---
# <a name="visual-studio-sdk"></a>SDK do Visual Studio
O SDK do Visual Studio ajuda você a ampliar os recursos do Visual Studio ou integrar novos recursos no Visual Studio. Você pode distribuir as extensões para outros usuários, bem como a Galeria do Visual Studio. A seguir está algumas das maneiras em que você pode estender o Visual Studio:  
  
-   Adicionar comandos, botões, menus e outros elementos de interface do usuário ao IDE  
  
-   Adicionar janelas de ferramenta para a nova funcionalidade  
  
-   Estenda o IntelliSense para um determinado idioma, ou fornecer o IntelliSense para novas linguagens de programação  
  
-   Use as lâmpadas para fornecer dicas e sugestões para ajudam os desenvolvedores a escrevam códigos melhores  
  
-   Habilitar o suporte para um novo idioma  
  
-   Adicionar um tipo de projeto personalizado  
  
-   Alcance milhões de desenvolvedores por meio da Galeria do Visual Studio  
  
 Se você nunca escreveu uma extensão do Visual Studio antes, você deve encontrar mais informações sobre esses recursos e [começando a desenvolver extensões do Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="installing-the-visual-studio-sdk"></a>Instalar o SDK do Visual Studio  
 O SDK do Visual Studio é um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>O que há de novo no SDK do Visual Studio 2017  
 O SDK do Visual Studio tem alguns novos recursos como o suporte para o carregamento da solução leve e o formato do VSIX v3, bem como quebrar as alterações que podem exigir que você atualize sua extensão. Para obter mais informações, consulte [o que há de novo no SDK do Visual Studio 2017](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Diretrizes de experiência de usuário do Visual Studio  
 Obter ótimas dicas para projetar a interface do usuário para a sua extensão em [diretrizes de experiência de usuário do Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 Você também pode aprender como fazer sua extensão combinam bem com dispositivos DPI alto com nosso [abordar problemas de DPI](../extensibility/addressing-dpi-issues2.md) tópico.  
  
 Aproveitar o [serviço de imagem e catálogo](../extensibility/image-service-and-catalog.md) para gerenciamento de imagem grande e suporte para DPI alto e temas.  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>Localizando e instalando extensões existentes do Visual Studio  
 Você pode encontrar as extensões do Visual Studio no **extensões e atualizações** caixa de diálogo no **ferramentas** menu. Para obter mais informações, consulte [Localizando e usando extensões do Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). Você também pode encontrar extensões no [Galeria do Visual Studio](https://visualstudiogallery.msdn.microsoft.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Referência SDK do Visual Studio  
 Você pode encontrar a referência de API do SDK do Visual Studio em [referência de SDK do Visual Studio](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Amostras do Visual Studio SDK  
 Você pode encontrar exemplos de código-fonte aberto de extensões do SDK do VS no GitHub em [exemplos do Visual Studio](https://aka.ms/vs2015sdksamples). Repositório GitHub contém exemplos que ilustram diversos recursos extensíveis no Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Outros recursos do Visual Studio SDK  
 Se você tiver dúvidas sobre o VSSDK ou deseja compartilhar suas experiências de desenvolvimento de extensões, você pode usar o [Visual Studio Extensibility Forum](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) ou [ExtendVS Chat de grupo](https://gitter.im/Microsoft/extendvs).  
  
 Você pode encontrar mais informações no [Arcana VSX blog](http://blogs.msdn.com/b/vsx/) e uma série de blogs escritos por MVPs da Microsoft:  
  
-   [Extensões do Visual Studio Favoritos](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Extensibilidade do Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [Estendendo o Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>Consulte também  
 [Criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Como: migrar projetos de extensibilidade para o Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)   
 [Perguntas Frequentes: Convertendo suplementos em extensões VSPackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Gerenciamento de vários Threads em código gerenciado](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Estendendo Menus e comandos](../extensibility/extending-menus-and-commands.md)   
 [Adicionando comandos em barras de ferramentas](../extensibility/adding-commands-to-toolbars.md)   
 [Estendendo e personalizando janelas de ferramenta](../extensibility/extending-and-customizing-tool-windows.md)   
 [Editor e extensões do serviço de linguagem](../extensibility/editor-and-language-service-extensions.md)   
 [Estendendo projetos](../extensibility/extending-projects.md)   
 [Opções e configurações de usuário estendendo](../extensibility/extending-user-settings-and-options.md)   
 [Criando modelos de Item e projeto personalizados](../extensibility/creating-custom-project-and-item-templates.md)   
 [Estendendo propriedades e a janela de propriedades](../extensibility/extending-properties-and-the-property-window.md)   
 [Estendendo a outras partes do Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Usando e fornecer serviços](../extensibility/using-and-providing-services.md)   
 [Gerenciando os VSPackages](../extensibility/managing-vspackages.md)   
 [Visual Studio isolada Shell](../extensibility/visual-studio-isolated-shell.md)   
 [Envio de extensões do Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [Dentro do Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Suporte para o SDK do Visual Studio](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Arquivo morto](../extensibility/archive.md)   
 [Referência do SDK do Visual Studio](../extensibility/visual-studio-sdk-reference.md)
