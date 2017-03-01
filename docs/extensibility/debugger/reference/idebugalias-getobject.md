---
title: IDebugAlias::GetObject | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugAlias::GetObject
helpviewer_keywords:
- IDebugAlias::GetObject method
ms.assetid: 97bc3af6-6e55-4940-8a6d-692c61257806
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
ms.openlocfilehash: 2c4f81929fab4daad40f02c9b37a676f65560741
ms.lasthandoff: 02/22/2017

---
# <a name="idebugaliasgetobject"></a>IDebugAlias::GetObject
Obtém o objeto este alias para.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetObject(  
   IDebugObject2** ppObject  
);  
```  
  
```c#  
int GetObject(  
   Out IDebugObject2 ppObject  
)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppObject`  
 [out] O [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) representa este alias.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
