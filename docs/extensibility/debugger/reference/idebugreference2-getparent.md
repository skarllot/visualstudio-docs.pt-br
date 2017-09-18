---
title: IDebugReference2::GetParent | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugReference2::GetParent
helpviewer_keywords:
- IDebugReference2::GetParent
ms.assetid: e3061665-ad3e-4c1b-b33f-82755fa21be3
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
ms.openlocfilehash: 897c48932cdd3ceb1c307f3d2436634936936f56
ms.lasthandoff: 02/22/2017

---
# <a name="idebugreference2getparent"></a>IDebugReference2::GetParent
Obtém a referência do pai de uma referência. Reservado para uso futuro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetParent (   
   IDebugReference2** ppParent  
);  
```  
  
```c#  
int GetParent (   
   out IDebugReference2 ppParent  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppParent`  
 [out] Retorna um [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objeto que representa o pai desta propriedade.  
  
## <a name="return-value"></a>Valor de retorno  
 Sempre retorna `E_NOTIMPL`.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
