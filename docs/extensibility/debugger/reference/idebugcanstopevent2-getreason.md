---
title: IDebugCanStopEvent2::GetReason | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
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
ms.openlocfilehash: d6b75ff3e3fc74018bb8f17d7754183309ea39c3
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Obtém o motivo por que o mecanismo de depuração (DE) deseja interromper.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetReason(   
   CANSTOP_REASON* pcr  
);  
```  
  
```c#  
int GetReason(   
   out enum_CANSTOP_REASON pcr  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pcr`  
 [out] Retorna um valor a partir de [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) enumeração que descreve o motivo para esse evento.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Normalmente, esse método é chamado antes de [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) método para que o chamador possa determinar se devem passar diferente de zero (`TRUE`) para o `IDebugCanStopEvent2::CanStop` método.  
  
 O motivo para a interrupção pode ser `CANSTOP_ENTRYPOINT`, que significa que o DE atingiu um ponto de entrada, ou `CANSTOP_STEPIN`, que significa que o DE tem entrar em uma função.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
