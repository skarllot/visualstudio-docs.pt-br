---
title: IEnumDebugErrorBreakpoints2::Skip | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugErrorBreakpoints2::Skip
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2::Skip
ms.assetid: a5a02b38-4e3a-4f0e-b529-f770c3485c8b
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
ms.openlocfilehash: b74c984fad4e0bbb45010547bd9d618acfbde26f
ms.lasthandoff: 02/22/2017

---
# <a name="ienumdebugerrorbreakpoints2skip"></a>IEnumDebugErrorBreakpoints2::Skip
Ignora o número especificado de elementos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```c#  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 [in] Número de elementos a serem ignorados.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se `celt` for maior que o número de elementos restantes; caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Se `celt` Especifica um valor maior que o número de elementos restantes, a enumeração está definida para o fim e `S_FALSE` é retornado.  
  
## <a name="see-also"></a>Consulte também  
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)
