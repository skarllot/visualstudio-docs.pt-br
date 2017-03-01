---
title: IDebugEvent2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
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
ms.openlocfilehash: a53b02eb4eb4ead23ba0609c9b8b7a5465d78508
ms.lasthandoff: 02/22/2017

---
# <a name="idebugevent2"></a>IDebugEvent2
Essa interface é usada para comunicar informações de depuração importantes, como parar no ponto de interrupção e as informações não-críticas, como uma mensagem de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração (DE) e o fornecedor de porta personalizada implementam essa interface no mesmo objeto que todas as outras interfaces de evento.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Usando a interface do argumento IID (ID) fornecido ao [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ou [evento](../../../extensibility/debugger/reference/idebugportevents2-event.md), chama o Gerenciador de sessão de depuração (SDM) [QueryInterface](/visual-cpp/atl/queryinterface) sobre o `IDebugEvent2` interface para obter a interface de eventos apropriado.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugEvent2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Obtém os atributos para este evento de depuração.|  
  
## <a name="remarks"></a>Comentários  
 Interfaces de evento mais específico, como [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), não derivam da interface IDebugEvent2, mas em vez disso, são implementados como uma interface separada no mesmo objeto como `IDebugEvent2`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
