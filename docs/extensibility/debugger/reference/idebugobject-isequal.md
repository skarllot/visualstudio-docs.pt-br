---
title: IDebugObject::IsEqual | Microsoft Docs
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 9780a18ff72058a90739c421061fabd9ce8520e1
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
Compara a um objeto com esse objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT IsEqual(   
   IDebugObject* pObject,  
   BOOL*         pfIsEqual  
);  
```  
  
```csharp  
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
 Normalmente, esse método pode comparar os endereços dos valores representados pelo `pObject` parâmetro e isso [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto; se os endereços são iguais e, em seguida, os objetos podem ser considerados iguais.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
