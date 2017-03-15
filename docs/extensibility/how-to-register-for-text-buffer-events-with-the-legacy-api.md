---
title: 'Como: registrar eventos de Buffer de texto com a API herdada | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b7da1dc26631294b6e41aa6335f2dca064c2831d
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Como: registrar eventos de Buffer de texto com a API herdada
Se você estiver acessando o buffer de texto usando a API herdada, você deve se registrar para eventos de buffer de texto, conforme mostrado no procedimento a seguir.  
  
### <a name="to-advise-text-buffer-events"></a>Para eventos de buffer de texto de aviso  
  
1.  De um ponteiro para uma das interfaces no <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>, chame `QueryInterface` de um ponteiro para <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> </xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>  
  
2.  Chamar o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A>método e passar a ID de interface de eventos para o qual você deseja registrar.</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A>  
  
     Por exemplo, se você deseja registrar para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>, em seguida, passamos uma ID de IID_IVsTextLinesEvents interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>  
  
     O buffer de texto retorna um ponteiro para o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>interface para o objeto de ponto de conexão apropriado.</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>  
  
3.  Usando esse ponteiro, chamar o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>método, transmitindo um ponteiro para a implementação da interface de eventos para o qual você deseja registrar, por exemplo, o `IVsTextLinesEvents` interface.</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>  
  
     O ambiente retorna um cookie que você pode usar para parar de ouvir eventos chamando o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A>método.</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A>  
  
## <a name="see-also"></a>Consulte também  
 [Eventos de Buffer de texto na API herdada](../extensibility/text-buffer-events-in-the-legacy-api.md)
