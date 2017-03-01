---
title: IDebugClassField::EnumNestedClasses | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
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
ms.openlocfilehash: 007c55d7c7e03777dd40ec7fef91479486dd7bab
ms.lasthandoff: 02/22/2017

---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
Cria um enumerador para as classes aninhadas nessa classe.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT EnumNestedClasses(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumNestedClasses(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppEnum`  
 [out] Retorna um [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa a lista de classes aninhadas. Retorna um valor nulo se não houver nenhuma classe aninhada.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, Retorna S_OK ou retorna S_FALSE se não houver nenhuma classe aninhada. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Cada elemento da enumeração é uma [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objeto que descreve uma classe aninhada.  
  
 Uma classe aninhada é uma classe definida dentro de outra classe. Por exemplo:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 O [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) enumeração contém um objeto representando o `NestedClass` classe.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
