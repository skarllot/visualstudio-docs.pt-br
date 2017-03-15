---
title: IDebugStackFrame2::GetThread | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugStackFrame2::GetThread
helpviewer_keywords:
- IDebugStackFrame2::GetThread
ms.assetid: cbeef85b-3dd7-4f97-adc2-c4d197d979fc
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
ms.openlocfilehash: 05de936d1fc763ecdb40c1c849b4c9a58d0bfc81
ms.lasthandoff: 02/22/2017

---
# <a name="idebugstackframe2getthread"></a>IDebugStackFrame2::GetThread
Obtém o thread associado a um quadro de pilha.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetThread (   
   IDebugThread2** ppThread  
);  
```  
  
```c#  
int GetThread (   
   out IDebugThread2 ppThread  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppThread`  
 [out] Retorna um [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa o thread.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
