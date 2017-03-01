---
title: IDebugMemoryContext2::Compare | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
caps.latest.revision: 14
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
ms.openlocfilehash: bd6268e33f2b8efec87bd7f0c0949867cbedf053
ms.lasthandoff: 02/22/2017

---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
Compara o contexto de memória para cada contexto na matriz especificada da maneira indicada pelos sinalizadores de comparação, retornando um índice do primeiro contexto que corresponda.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Compare(   
   CONTEXT_COMPARE        compare,  
   IDebugMemoryContext2** rgpMemoryContextSet,  
   DWORD                  dwMemoryContextSetLen,  
   DWORD*                 pdwMemoryContext  
);  
```  
  
```c#  
int Compare(  
   enum_CONTEXT_COMPARE   compare,   
   IDebugMemoryContext2[] rgpMemoryContextSet,   
   uint                   dwMemoryContextSetLen,   
   out uint               pdwMemoryContext  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `compare`  
 [in] Um valor a partir de [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) enumeração que determina o tipo de comparação.  
  
 `rgpMemoryContextSet`  
 [in] Uma matriz de referências para o [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objetos para comparação.  
  
 `dwMemoryContextSetLen`  
 [in] O número de contextos na `rgpMemoryContextSet` matriz.  
  
 `pdwMemoryContext`  
 [out] Retorna o índice do primeiro contexto de memória que satisfaz a comparação.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. Retorna `E_COMPARE_CANNOT_COMPARE` se os dois contextos não podem ser comparados.  
  
## <a name="remarks"></a>Comentários  
 Não tem um mecanismo de depuração (DE) para oferecer suporte a todos os tipos de comparações, mas ele deve suportar pelo menos `CONTEXT_EQUAL`, `CONTEXT_LESS_THAN`, `CONTEXT_GREATER_THAN` e `CONTEXT_SAME_SCOPE`.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)
