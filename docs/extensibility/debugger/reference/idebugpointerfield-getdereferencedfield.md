---
title: IDebugPointerField::GetDereferencedField | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
caps.latest.revision: 7
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
ms.openlocfilehash: 48f530e08688669ff070bb42e79f4bea30062715
ms.lasthandoff: 02/22/2017

---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
Esse método retorna o tipo de objeto para o qual este objeto de ponteiro aponta.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetDereferencedField(  
   IDebugField** ppField  
);  
```  
  
```c#  
int GetDereferencedField(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppField`  
 [out] Retorna um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que descreve o tipo de objeto de destino.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Se, por exemplo, o [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) objeto aponta para um número inteiro, o [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) tipo retornado por esse método descreve que tipo de inteiro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
