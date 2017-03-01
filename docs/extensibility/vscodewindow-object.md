---
title: Objeto VSCodeWindow | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
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
ms.openlocfilehash: d0ea2351a38573b087268e97d23815567ba4f3b3
ms.lasthandoff: 02/22/2017

---
# <a name="vscodewindow-object"></a>Objeto VSCodeWindow
Uma janela de código é uma janela de documento especializados que pode incluir uma ou mais exibições de texto, geralmente o <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>objeto.</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>  
  
 Em termos de arquitetura, a janela de código é uma janela de documento que está dentro de um quadro de janela. Funcionalmente, a janela de código é simplesmente uma janela de documento com recursos adicionais. No modo de interface de documentos múltiplos (MDI), a janela de código é o quadro de filho MDI. Para obter mais informações, consulte [personalizando janelas de código usando a API herdada](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).  
  
 A tabela a seguir inclui as interfaces de <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>objeto.</xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider></xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Fornece um mecanismo de acesso genérico para localizar um serviço que identifica um identificador global exclusivo (GUID).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Representa vários documentos interface MDI filho que contém um ou mais modos de exibição de código.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane></xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Preenche um quadro de janela.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider></xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Edição de figuras](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)
