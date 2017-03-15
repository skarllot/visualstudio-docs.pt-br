---
title: Contido idiomas | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 18
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
ms.openlocfilehash: 73a9adafc9eb44150d92cc891b9662807801a119
ms.lasthandoff: 02/22/2017

---
# <a name="contained-languages"></a>Idiomas independentes
*Contido idiomas* idiomas que estão contidas em outros idiomas. Por exemplo, HTML em [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] as páginas podem conter [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ou [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] scripts. Uma arquitetura dual-idioma é necessária para o editor de arquivo. aspx fornecer IntelliSense, colorização e outros recursos de edição de HTML e a linguagem de script.  
  
## <a name="implementation"></a>Implementação  
 A interface mais importante que você precisa implementar para idiomas contidos é o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> Essa interface é implementada por qualquer linguagem que pode ser hospedada em um idioma principal. Ele fornece acesso para o serviço de linguagem colorizador, filtro de exibição de texto e ID de serviço do idioma primário. O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>permite que você crie um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> As etapas a seguir mostram como implementar uma linguagem independente:  
  
1.  Use `QueryService()` para obter o idioma, ID de serviço e a ID de interface de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>  
  
2.  Chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A>método para criar um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> Passar um <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>interface, uma ID de item (uma ou mais das <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_NIL>, <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>, ou <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_SELECTION>) e um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> </xref:Microsoft.VisualStudio.VSConstants.VSITEMID_SELECTION> </xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT> </xref:Microsoft.VisualStudio.VSConstants.VSITEMID_NIL> </xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
3.  O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>interface, que é o objeto de coordenador de buffer de texto, fornece os serviços básicos que são necessárias para mapear locais em um arquivo primário no buffer do idioma secundário.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>  
  
     Por exemplo, em um único arquivo. aspx, o arquivo primário inclui o ASP, HTML e todo o código que está contido. No entanto, o buffer secundário, inclui apenas o código contido, junto com quaisquer definições de classe, para tornar o buffer secundário em um arquivo de código válido. O coordenador de buffer manipula o trabalho de coordenação de edições de um buffer para o outro.  
  
4.  O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>método, que é o idioma principal, informa o coordenador de buffer que texto dentro de seu buffer é mapeado para o texto correspondente no buffer secundário.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>  
  
     A linguagem passa uma matriz de <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping>estrutura, que atualmente inclui apenas um principal e um secundário span.</xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping>  
  
5.  O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A>método e o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A>método fornece o mapeamento do primário para o buffer secundário e vice-versa.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A>
