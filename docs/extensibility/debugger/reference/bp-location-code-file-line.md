---
title: BP_LOCATION_CODE_FILE_LINE | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BP_LOCATION_CODE_FILE_LINE
helpviewer_keywords:
- BP_LOCATION_CODE_FILE_LINE structure
ms.assetid: 3ff32032-d412-44d3-91bf-870cc354a09e
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
ms.openlocfilehash: d1e9acead9a0aed079e880cdfa45874b12b95eb6
ms.lasthandoff: 02/22/2017

---
# <a name="bplocationcodefileline"></a>BP_LOCATION_CODE_FILE_LINE
Contém os dados para o local de um ponto de interrupção em uma linha específica em um arquivo de origem do código.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_FILE_LINE {   
   BSTR                     bstrContext;  
   IDebugDocumentPosition2* pDocPos;  
} BP_LOCATION_CODE_FILE_LINE;  
```  
  
## <a name="members"></a>Membros  
 `bstrContext`  
 O contexto do ponto de interrupção, normalmente um nome de função ou método como visto em uma pilha de chamadas.  
  
 `pDocPos`  
 O [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) objeto que representa a posição do ponto de interrupção do documento.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é membro do [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) estrutura como parte de uma união.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
