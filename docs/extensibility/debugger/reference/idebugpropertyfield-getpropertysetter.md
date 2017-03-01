---
title: IDebugPropertyField::GetPropertySetter | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPropertyField::GetPropertySetter
helpviewer_keywords:
- IDebugPropertyField::GetPropertySetter method
ms.assetid: 744d76fd-2bcc-4917-a040-ce4cc714ef61
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
ms.openlocfilehash: a719664a3c61c8d802be34c86d17ad1191bec94e
ms.lasthandoff: 02/22/2017

---
# <a name="idebugpropertyfieldgetpropertysetter"></a>IDebugPropertyField::GetPropertySetter
Obtém o método que define a propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetPropertySetter(   
   IDebugMethodField** ppField  
);  
```  
  
```c#  
int GetPropertySetter(  
   out IDebugMethodField ppField  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppField`  
 [out] Retorna um [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) que representa o método que define a propriedade do objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Para obter o método que obtém a propriedade, chame o [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)
