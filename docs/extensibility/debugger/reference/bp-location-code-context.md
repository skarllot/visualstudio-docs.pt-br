---
title: BP_LOCATION_CODE_CONTEXT | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BP_LOCATION_CODE_CONTEXT
helpviewer_keywords:
- BP_LOCATION_CODE_CONTEXT structure
ms.assetid: 37412896-021a-4f73-9bb7-4125502c2e18
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
ms.openlocfilehash: 8f095a168e92f671bb743aae3c1967e22f8c7374
ms.lasthandoff: 02/22/2017

---
# <a name="bplocationcodecontext"></a>BP_LOCATION_CODE_CONTEXT
Descreve o local de um ponto de interrupção é ligado diretamente ao endereço no programa que está sendo depurado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_CONTEXT {   
   IDebugCodeContext2* pCodeContext;  
} BP_LOCATION_CODE_CONTEXT;  
```  
  
## <a name="members"></a>Membros  
 pCodeContext  
 O [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que identifica a posição do ponto de interrupção no código.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é membro do [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) estrutura como parte de uma união.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
