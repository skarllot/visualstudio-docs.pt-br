---
title: IDebugObject::IsEqual | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
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
ms.openlocfilehash: 35d65729a75d06cb8aefc330441cefb09c95bb04
ms.lasthandoff: 02/22/2017

---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
Compara um objeto com esse objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT IsEqual(   
   IDebugObject* pObject,  
   BOOL*         pfIsEqual  
);  
```  
  
```c#  
int IsEqual(  
   IDebugObject pObject,  
   out int      pfIsEqual  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pObject`  
 [in] Um [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto que representa o objeto a ser comparado.  
  
 `pfIsEqual`  
 [out] Retorna diferente de zero (`TRUE`) se os valores dos objetos forem iguais; caso contrário, retorna zero (`FALSE`).  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Normalmente, esse método pode comparar os endereços dos valores representados pelo `pObject` parâmetro e isso [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto; se os endereços forem iguais, os objetos podem ser considerados iguais.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
