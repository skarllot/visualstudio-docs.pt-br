---
title: IDebugThread2::Resume | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
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
ms.openlocfilehash: 2f1401c40b264cc36a2f72f33b3cd9ba8be2f6a5
ms.lasthandoff: 02/22/2017

---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
Retoma a execução de um thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```c#  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdwSuspendCount`  
 [out] Retorna a contagem de suspensões após a operação de retomada.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Cada chamada para diminui esse método de contagem de suspensões até alcançar 0 nesse momento, a execução é retomada realmente. A contagem de suspensões é exibida no **Threads** janela de depuração.  
  
 Para cada chamada para esse método, deve haver uma chamada anterior a [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) método. A contagem de suspensões determina quantas vezes o `IDebugThread2::Suspend` método foi chamado até o momento.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
