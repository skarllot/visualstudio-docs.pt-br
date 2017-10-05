---
title: BSTR_ARRAY | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BSTR_ARRAY
helpviewer_keywords:
- BSTR_ARRAY structure
ms.assetid: 48da37f7-a237-48a9-9ff9-389c1a00862c
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 0e1d2b2228085505971102494522cdf9085d4a67
ms.contentlocale: pt-br
ms.lasthandoff: 09/26/2017

---
# <a name="bstrarray"></a>BSTR_ARRAY
Uma estrutura que descreve uma matriz de cadeias de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct tagBSTR_ARRAY {  
   DWORD dwCount;  
   BSTR* Members;  
} BSTR_ARRAY;  
```  
  
```csharp  
struct BSTR_ARRAY {  
   DWORD    dwCount;  
   string[] Members;  
}  
```  
  
## <a name="terms"></a>Termos  
 dwCount  
 Número de cadeias de caracteres em `Members` matriz.  
  
 Membros  
 Matriz de cadeias de caracteres.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é retornada a partir de [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) método.  
  
 [C++] Cada cadeia de caracteres individual deve ser liberada usando `SysFreeString`e o `Members` matriz deve ser liberada com `CoTaskMemFree`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)
