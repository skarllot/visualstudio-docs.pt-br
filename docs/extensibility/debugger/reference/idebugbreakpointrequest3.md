---
title: IDebugBreakpointRequest3 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
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
ms.openlocfilehash: 0e0983e8c3ece3947c8287b950fb0af50c8fdd50
ms.lasthandoff: 02/22/2017

---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Essa interface representa as informações necessárias para criar e associar qualquer tipo de ponto de interrupção. Ele é uma extensão de [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugBreakpointRequest3 : IDebugBreakpointRequest2  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Normalmente, o Gerenciador de sessão de depuração (SDM) implementa essa interface.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O mecanismo de depuração (DE) acessa essa interface chamando [QueryInterface](/visual-cpp/atl/queryinterface) na interface IDebugBreakpointRequest2 recebido em uma chamada para [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Além dos métodos herdados de [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md), o `IDebugBreakpointRequest3` interface expõe o método a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Obtém as informações de solicitação de ponto de interrupção que descreve esta solicitação de ponto de interrupção.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface é usada para fornecer informações adicionais para o DE por meio de [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) estrutura. Essas informações adicionais incluem ID do fornecedor do DE (na forma de um GUID), o nome de um tracepoint e o nome de uma restrição de ponto de interrupção.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
