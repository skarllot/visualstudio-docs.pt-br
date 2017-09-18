---
title: IDebugField::Equal | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
caps.latest.revision: 11
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
ms.openlocfilehash: 60ca6453661ba29b417279e852bee51a32796bb5
ms.lasthandoff: 02/22/2017

---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Este método compara esse campo com o campo especificado para igualdade.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Equal(   
   IDebugField* pField  
);  
```  
  
```c#  
int Equal(  
   IDebugField pField  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pField`  
 [in] O campo a ser comparado a este.  
  
## <a name="return-value"></a>Valor de retorno  
 Se os campos são os mesmos, retornará `S_OK`. Se os campos forem diferentes, retorna `S_FALSE.` caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
