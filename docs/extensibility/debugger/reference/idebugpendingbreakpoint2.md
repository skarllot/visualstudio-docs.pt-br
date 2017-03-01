---
title: IDebugPendingBreakpoint2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
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
ms.openlocfilehash: e3a751d0a0ad97f0c31ee75d5977c5772ee4238d
ms.lasthandoff: 02/22/2017

---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
Essa interface representa um ponto de interrupção está pronto para vincular a um local de código.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugPendingBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração (DE) implementa essa interface como parte de seu suporte para pontos de interrupção.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Uma chamada para [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) cria um ponto de interrupção pendente de um [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) interface. Uma chamada para [ligar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) cria um `IDebugBreakpoint2` interface que representa um ponto de interrupção associado no programa.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugPendingBreakpoint2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Determina se este ponto de interrupção pendente pode vincular a um local de código.|  
|[Ligação](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Associa a esse ponto de interrupção pendente para um ou mais locais de código.|  
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Obtém o estado desse pendente ponto de interrupção.|  
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Obtém a solicitação de ponto de interrupção que foi usada para criar esse ponto de interrupção pendente.|  
|[Virtualizar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Alterna o estado virtualizado isso pendentes ponto de interrupção.|  
|[Habilitar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Alterna o estado habilitado disso pendentes ponto de interrupção.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Define ou altera a condição associada a esse pendentes ponto de interrupção.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Define ou altera a contagem de passagem associada a esse pendentes ponto de interrupção.|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Enumera todos os pontos de interrupção associados a partir deste ponto de interrupção pendente.|  
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Enumera todos os pontos de interrupção de erro resultantes deste ponto de interrupção pendente.|  
|[Excluir](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Exclui todos os pontos de interrupção associados dele e esse ponto de interrupção pendente.|  
  
## <a name="remarks"></a>Comentários  
 `IDebugPendingBreakpoint2`pode ser pensada como um provedor de todas as informações necessárias para associar um ponto de interrupção ao código que pode ser aplicado a um ou vários programas.  
  
 Um ponto de interrupção pendente potencialmente pode produzir mais de um ponto de interrupção associado. Por exemplo, um ponto de interrupção em um modelo de estilo C++ pode produzir um ponto de interrupção associado para cada instância exclusiva do modelo.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)
