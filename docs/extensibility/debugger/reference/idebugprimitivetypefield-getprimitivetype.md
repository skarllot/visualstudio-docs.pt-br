---
title: IDebugPrimitiveTypeField::GetPrimitiveType | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetPrimitiveType
- IDebugPrimitiveTypeField::GetPrimitiveType
ms.assetid: a186c922-bbfe-478c-a744-b21eb4672d8f
caps.latest.revision: 10
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
ms.openlocfilehash: 30de91316b0bea149124ac3007bca92371ba4248
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprimitivetypefieldgetprimitivetype"></a>IDebugPrimitiveTypeField::GetPrimitiveType
Recupera o tipo primitivo que está associado esse campo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetPrimitiveType (  
   DWORD* pdwType  
);  
```  
  
```c#  
int GetPrimitiveType (  
   out uint pdwType  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdwType`  
 [out] O valor do [enumeração CorElementType](CorElementType%20Enumeration.xml) que representa o tipo primitivo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará `S_FALSE`.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)
