---
title: IDebugBoundBreakpoint2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
caps.latest.revision: 11
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
ms.openlocfilehash: 3406c6b415523ff8ec46b71b649a81a44fb01c66
ms.lasthandoff: 02/22/2017

---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
Essa interface representa um ponto de interrupção que está associado a um local de código.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugBoundBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração (DE) implementa essa interface como parte de seu suporte para pontos de interrupção.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Uma chamada para [ligar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) cria essa interface. Chamadas para [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) e [próxima](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) também pode obter essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugBoundBreakpoint2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Obtém o ponto de interrupção pendente do qual o ponto de interrupção associado especificado foi criado.|  
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Obtém o estado deste ponto de interrupção associada.|  
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Obtém a contagem de ocorrências atual para este ponto de interrupção associado.|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Obtém a resolução de ponto de interrupção que descreve este ponto de interrupção.|  
|[Habilitar](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Habilita ou desabilita o ponto de interrupção.|  
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Define a contagem de ocorrências para este ponto de interrupção associada.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Define ou altera a condição associada a este ponto de interrupção associado.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Define ou alterar a contagem de passagem associada com este ponto de interrupção associado.|  
|[Excluir](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Exclui o ponto de interrupção.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)   
 [Avançar](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)   
 [Ligação](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
