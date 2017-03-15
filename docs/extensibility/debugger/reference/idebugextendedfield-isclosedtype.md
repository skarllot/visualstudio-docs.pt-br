---
title: IDebugExtendedField::IsClosedType | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
caps.latest.revision: 8
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
ms.openlocfilehash: 5ac4b4fa965b375d1ad22042f8beaa26e7721816
ms.lasthandoff: 02/22/2017

---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
Determina se o campo representa um tipo fechado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT IsClosedType(  
   void  
);  
```  
  
```c#  
int IsClosedType();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se o campo for um tipo fechado, retornará `S_OK`; caso contrário, retornará `S_FALSE`.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)
