---
title: IDebugEventCallback2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
caps.latest.revision: 15
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
ms.openlocfilehash: 57601f71704353dae4ebdf83465ed8a3caffed97
ms.lasthandoff: 02/22/2017

---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Essa interface é usada pelo mecanismo de depuração (DE) para enviar eventos de depuração para o Gerenciador de sessão de depuração (SDM).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]implementa essa interface para receber eventos de um mecanismo de depuração.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Um mecanismo de depuração normalmente recebe essa interface quando chama o SDM [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md), ou [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Um mecanismo de depuração para enviar eventos para o SDM chamando [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugEventCallback2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Envia uma notificação de eventos para o SDM de depuração.|  
  
## <a name="remarks"></a>Comentários  
 Embora [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) e [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) Especifica que eles têm um `IDebugEventCallback2` interface, isso não é o caso e o ponteiro de interface sempre será um valor nulo. Em vez disso, o mecanismo de depuração deve usar o `IDebugEventCallback2` interface recebido na chamada para [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md), ou [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Se um pacote implementa [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) em código gerenciado, é altamente recomendável que <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A>ser invocada em várias interfaces que são passadas para [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).</xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A>  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Anexar](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Anexar](../../../extensibility/debugger/reference/idebugengine2-attach.md)
