---
title: IDebugCanStopEvent2::CanStop | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
caps.latest.revision: 10
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
ms.openlocfilehash: 63bd3542957d04a8b54d4f9c8f6f1526bee9676b
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Notifica o mecanismo de depuração (DE) ou não interromper no local atual do código ou simplesmente continuar a execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT CanStop (   
   BOOL fCanStop  
);  
```  
  
```c#  
int CanStop (   
   int fCanStop  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `fCanStop`  
 [in] Diferente de zero (`TRUE`) se o DE parar no local atual do código; caso contrário, zero (`FALSE`).  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O receptor desse evento normalmente chama o [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) método para determinar o motivo pelo qual o DE que deseja interromper e, em seguida, chama o `IDebugCanStopEvent2::CanStop` método com a resposta apropriada.  
  
 Se o DE é interrompido, ele envia um evento que descreve o motivo para interromper. Normalmente, há dois eventos que são enviados, uma quebra de sinal ou usuário representada pelo [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) interface e um evento de ponto de interrupção representado pelo [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) interface.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
