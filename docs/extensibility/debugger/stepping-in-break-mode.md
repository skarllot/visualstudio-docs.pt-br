---
title: "Entrar no modo de interrupção | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: 7
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
ms.openlocfilehash: 5f47369fd993da277dd051d03e972a8417bf1c6a
ms.lasthandoff: 02/22/2017

---
# <a name="stepping-in-break-mode"></a>Entrar no modo de interrupção
O exemplo a seguir descreve o processo que ocorre quando o depurador está no modo de interrupção e deve percorrer o código:  
  
## <a name="stepping-process"></a>Processo de revisão  
  
1.  Chamar [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) com [STEPKIND](../../extensibility/debugger/reference/stepkind.md) e [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) argumentos para executar uma etapa.  
  
2.  Quando a etapa for concluída, enviar um [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) como um evento de parada.  
  
## <a name="see-also"></a>Consulte também  
 [Eventos do depurador de chamada](../../extensibility/debugger/calling-debugger-events.md)
