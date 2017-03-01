---
title: IEnumDebugAddresses::Skip | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugAddresses::Skip
helpviewer_keywords:
- IEnumDebugAddresses::Skip method
ms.assetid: ed9a8e71-30ef-414b-9da5-c9a2a251b84e
caps.latest.revision: 6
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
ms.openlocfilehash: f29b32f346fe4b85b74ff55976e68d5b82a5b740
ms.lasthandoff: 02/22/2017

---
# <a name="ienumdebugaddressesskip"></a>IEnumDebugAddresses::Skip
Este método ignora o número especificado de elementos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Skip(  
   [in] ULONG celt  
);  
```  
  
```c#  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 [in] Número de elementos a serem ignorados.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se `celt` for maior que o número de elementos restantes; caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Se `celt` Especifica um valor maior que o número de elementos restantes, a enumeração está definida para o fim e `S_FALSE` é retornado.  
  
## <a name="see-also"></a>Consulte também  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
