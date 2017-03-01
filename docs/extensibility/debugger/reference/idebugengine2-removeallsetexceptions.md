---
title: IDebugEngine2::RemoveAllSetExceptions | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords:
- IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
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
ms.openlocfilehash: b8a8074ea53054057515487f4d50cbe6cec5bb53
ms.lasthandoff: 02/22/2017

---
# <a name="idebugengine2removeallsetexceptions"></a>IDebugEngine2::RemoveAllSetExceptions
Remove a lista de exceções, que o IDE tiver definido para um idioma ou a arquitetura de tempo de execução específica.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT RemoveAllSetExceptions(   
   REFGUID guidType  
);  
```  
  
```c#  
int RemoveAllSetExceptions(   
   ref Guid guidType  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `guidType`  
 [in] O GUID para o idioma ou o GUID para o mecanismo de depuração é específico para uma arquitetura de tempo de execução.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 As exceções removidas por este método foram definidas por chamadas anteriores para o [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) método.  
  
 Para remover uma exceção específica, chame o [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
