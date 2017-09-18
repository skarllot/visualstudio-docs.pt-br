---
title: IDebugMemoryContext2::Add | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
caps.latest.revision: 12
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
ms.openlocfilehash: 91291553208451801c548f1f40cd0af6be9248e7
ms.lasthandoff: 02/22/2017

---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
Adiciona o valor especificado para o contexto atual e retorna um novo contexto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Add(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```c#  
int Add(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwCount`  
 [in] O valor a ser adicionado ao contexto atual.  
  
 `ppMemCxt`  
 [out] Retorna um novo [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Um contexto de memória é um endereço para que adicionar um valor a um endereço produz um novo endereço que exige uma nova interface de contexto.  
  
 Esse método sempre deve gerar um novo contexto, mesmo se o endereço resultante está fora do espaço de memória associado a esse contexto. A única exceção a isso é se a memória não pode ser alocada para o novo contexto ou `ppMemCxt` é um valor nulo (que é um erro).  
  
## <a name="see-also"></a>Consulte também  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
