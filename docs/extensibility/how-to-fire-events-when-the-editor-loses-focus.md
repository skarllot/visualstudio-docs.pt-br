---
title: 'Como: disparar eventos quando o Editor perde o foco | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
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
ms.openlocfilehash: 8124527d2e1bdfd17f66714a3fd6999e9a0bfd95
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Como: disparar eventos quando o Editor perde o foco
Às vezes, é necessário saber quando um editor perde o foco no quadro da janela. Por exemplo, talvez seja necessário extrair o código de uma janela de código após o editor não está mais focalizado nele. O procedimento a seguir fornece as etapas a seguir para receber notificações do editor perde o foco.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Disparar um evento em resposta a um editor perde o foco  
  
1.  Monitorar eventos de seleção, obtendo um <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>objeto de <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.</xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> </xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>  
  
2.  Chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A>e fornecê-la a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>objeto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> </xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A>  
  
3.  Em sua chamada para <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, procure `elementid==SEID_WindowFrame`.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>  
  
4.  Teste o `varValueNew` parâmetro para duas coisas:  
  
    1.  O quadro de janela que você está procurando.  
  
    2.  O ponto em que o seu programa perde a seleção do quadro de janela.
