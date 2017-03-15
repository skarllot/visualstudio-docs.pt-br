---
title: IDebugThread2::Suspend | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
caps.latest.revision: 9
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
ms.openlocfilehash: aa00d0029120abad26a7f4fdcd15f828a0284f2f
ms.lasthandoff: 02/22/2017

---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Suspende um thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Suspend (   
   DWORD *pdwSuspendCount  
);  
```  
  
```c#  
HRESULT Suspend (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdwSuspendCount`  
 [out] Retorna a contagem de suspensões após a operação de suspensão.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Cada chamada para esse método incrementa a contagem de suspensões acima de 0. A contagem de suspensões é exibida no **Threads** janela de depuração.  
  
 Para cada chamada para esse método, deve haver uma chamada posterior para o [retomar](../../../extensibility/debugger/reference/idebugthread2-resume.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Retomar](../../../extensibility/debugger/reference/idebugthread2-resume.md)
