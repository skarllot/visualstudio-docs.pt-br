---
title: IDebugExceptionEvent2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
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
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: c9817ca386846833ab022c5dbca3d3807bd38ef6
ms.lasthandoff: 04/05/2017

---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
O mecanismo de depuração (DE) envia essa interface para o Gerenciador de sessão de depuração (SDM) quando uma exceção é lançada no programa que está sendo executado no momento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugExceptionEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O DE implementa essa interface para o relatório que ocorreu uma exceção no programa que está sendo depurado. O [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface deve ser implementada no mesmo objeto dessa interface. Usa o SDM [QueryInterface](/cpp/atl/queryinterface) para acessar o `IDebugEvent2` interface.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O DE cria e envia esse objeto de evento para relatar uma exceção. O evento é enviado usando o [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) função de retorno de chamada que é fornecida pelo SDM quando anexado ao programa que está sendo depurado.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugExceptionEvent2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Obtém informações detalhadas sobre a exceção que disparou este evento.|  
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Obtém uma descrição legível para a exceção gerada que disparou este evento.|  
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Determina se o mecanismo de depuração (DE) oferece suporte ou não a opção de passar essa exceção para o programa que está sendo depurado quando a execução é retomada.|  
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Especifica se a exceção deve ser passada para o programa que está sendo depurado quando retoma a execução, ou se a exceção deve ser descartada.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Comentários  
 Antes de enviar o evento, DE verifica para ver se esse evento de exceção tiver sido designado uma exceção de primeira chance ou chance de segundo por uma chamada anterior a [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md). Se ele tiver sido designado para ser uma exceção de primeira chance de `IDebugExceptionEvent2` evento é enviado para o SDM. Caso contrário, o DE dá ao aplicativo a oportunidade de lidar com a exceção. Se nenhum manipulador de exceção é fornecido e se a exceção tiver sido designada como uma exceção de segunda chance de `IDebugExceptionEvent2` evento é enviado para o SDM. Caso contrário, o DE retoma a execução do programa e o sistema operacional ou o tempo de execução lida com a exceção.  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
