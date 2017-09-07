---
title: IDebugCanStopEvent2::GetReason | Microsoft Docs
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: b5d4c50b407406ea9a5d878decf859b8ab70863d
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Obtém o motivo por que deseja parar o mecanismo de depuração (DE).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetReason(   
   CANSTOP_REASON* pcr  
);  
```  
  
```csharp  
int GetReason(   
   out enum_CANSTOP_REASON pcr  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pcr`  
 [out] Retorna um valor da [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) enumeração que descreve o motivo para esse evento.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Normalmente, esse método é chamado antes do [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) método para que o chamador pode determinar se deseja transmitir diferente de zero (`TRUE`) para o `IDebugCanStopEvent2::CanStop` método.  
  
 O motivo para interrupção pode ser `CANSTOP_ENTRYPOINT`, que significa que o DE atingiu um ponto de entrada, ou `CANSTOP_STEPIN`, que significa que o DE tenha entrado em uma função.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
