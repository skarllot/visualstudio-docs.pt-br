---
title: Objeto VSTextView | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: 8
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
ms.openlocfilehash: fd11409382b2db5e5cbea8c0dad25dbdb3b6cb99
ms.lasthandoff: 02/22/2017

---
# <a name="vstextview-object"></a>Objeto VSTextView
A exibição de texto é uma janela que permite aos usuários exibir e editar o texto Unicode do buffer de texto. Essencialmente, o modo de exibição é o que a maioria dos usuários, consulte como o editor. Como o modo de exibição é separado do buffer por várias camadas de texto (quebra, texto de estrutura de tópicos e assim por diante), o modo de exibição não é garantido para ser uma representação exata do texto no buffer. Para obter mais informações sobre a exibição de texto, consulte [acessando theText exibição usando a API herdada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 A tabela a seguir mostra as interfaces de <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>objeto.</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>  
  
|Interface|Descrição|  
|---------------|-----------------|  
|[IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071)|Interface OLE padrão.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget></xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Interface OLE padrão.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite></xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Interface OLE padrão.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Interface OLE padrão.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permite a criação de ações compostas (ou seja, ações que são agrupadas em uma unidade única de desfazer/refazer).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Fornece os métodos básicos para gerenciar e acessar o modo de exibição. `IVsTextView`não é thread-safe.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane></xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Cria e gerencia um painel de janela.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView></xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interage com as camadas de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView></xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Executa operações no modo de exibição de um thread diferente.|  
  
## <a name="see-also"></a>Consulte também  
 [Edição de figuras](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [Objeto VSTextBuffer](../extensibility/vstextbuffer-object.md)   
 [Acessando theText exibição usando a API herdada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
