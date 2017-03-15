---
title: IDebugMemoryBytes2::WriteAt | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
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
ms.openlocfilehash: 69258e01dbef8e2666da19d248b73e52399992d0
ms.lasthandoff: 02/22/2017

---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Grava o número especificado de bytes de memória, começando no endereço especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT WriteAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory  
);  
```  
  
```c#  
int WriteAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pStartContext`  
 [in] O [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objeto que especifica onde iniciar a gravação de bytes.  
  
 `dwCount`  
 [in] O número de bytes a serem gravados.  
  
 `rgbMemory`  
 [in] Os bytes a serem gravados. Essa matriz deve para ser pelo menos `dwCount` bytes de tamanho.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` se nem todos os bytes poderia ser escritos ou retorna um código de erro (geralmente `E_FAIL`).  
  
## <a name="remarks"></a>Comentários  
 Se o endereço inicial não está dentro da janela de memória representada por esse [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) do objeto, nenhuma gravação ocorre e um código de erro `E_FAIL` é retornado, mesmo que se sobreponha a quantidade para gravar no espaço de memória.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
