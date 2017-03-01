---
title: IDebugCustomAttribute::GetParentField | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
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
ms.openlocfilehash: 81ef2f6d125720ff7df30429395dc8a3b4d2f0cd
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
Obtém o campo ao qual o atributo personalizado é anexado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetParentField(   
   IDebugField** ppField  
);  
```  
  
```c#  
int GetParentField(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppField`  
 [out] Retorna o [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto que representa o campo ao qual o atributo personalizado é anexado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Chamar o [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) método retornado [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) é de objeto para determinar qual tipo de campo pai.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
