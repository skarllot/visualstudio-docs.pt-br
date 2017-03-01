---
title: IEnumDebugReferenceInfo2::Clone | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugReferenceInfo2::Clone
helpviewer_keywords:
- IEnumDebugReferenceInfo2::Clone
ms.assetid: 49c5a301-a33a-428f-b83b-e734c71af4ef
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
ms.openlocfilehash: 8f9243646f383685ea548da735c1270e3792d6b0
ms.lasthandoff: 02/22/2017

---
# <a name="ienumdebugreferenceinfo2clone"></a>IEnumDebugReferenceInfo2::Clone
Retorna uma cópia da enumeração atual como um objeto separado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugReferenceInfo2** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumDebugReferenceInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppEnum`  
 [out] Retorna uma cópia dessa enumeração como um objeto separado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 A cópia da enumeração tem o mesmo estado original no momento em que este método é chamado. No entanto, a cópia e o original estados são separados e podem ser alterados individualmente.  
  
## <a name="see-also"></a>Consulte também  
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
