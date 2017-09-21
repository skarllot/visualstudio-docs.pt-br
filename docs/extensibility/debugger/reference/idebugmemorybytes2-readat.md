---
title: IDebugMemoryBytes2::ReadAt | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
caps.latest.revision: 13
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
ms.openlocfilehash: 8d89bcaa34e62141e5cbe21ee09e9fdb219f7d76
ms.lasthandoff: 02/22/2017

---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
Lê uma sequência de bytes, começando em um local especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT ReadAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory,  
   DWORD*                pdwRead,  
   DWORD*                pdwUnreadable  
);  
```  
  
```c#  
int ReadAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory,  
   out uint             pdwRead,  
   ref uint             pdwUnreadable  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pStartContext`  
 [in] O [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objeto que especifica onde iniciar a leitura de bytes.  
  
 `dwCount`  
 [in] O número de bytes a serem lidos. Também especifica o comprimento da `rgbMemory` matriz.  
  
 `rgbMemory`  
 [no, out] Matriz preenchido com os bytes realmente lidos.  
  
 `pdwRead`  
 [out] Retorna o número de bytes contíguos realmente lidos.  
  
 `pdwUnreadable`  
 [no, out] Retorna o número de bytes ilegíveis. Pode ser um valor nulo se o cliente não tem interesse em número de bytes ilegíveis.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Se 100 bytes são solicitados e os 50 primeiro são legíveis, os próximos 20 são ilegíveis e os 30 restantes são legíveis, esse método retorna:  
  
 *`pdwRead` = 50  
  
 *`pdwUnreadable` = 20  
  
 Nesse caso, porque `*pdwRead + *pdwUnreadable < dwCount`, o chamador deve fazer uma chamada adicional para ler os bytes restantes 30 a 100 original solicitada e o [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objeto passado a `pStartContext` parâmetro deve ser avançado por 70.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
