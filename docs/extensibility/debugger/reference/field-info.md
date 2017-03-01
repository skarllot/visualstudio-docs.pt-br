---
title: FIELD_INFO | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
caps.latest.revision: 14
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
ms.openlocfilehash: 28e412d0447670ce739a58b2216ba588e1f169a1
ms.lasthandoff: 02/22/2017

---
# <a name="fieldinfo"></a>FIELD_INFO
Essa estrutura descreve uma variável local, parâmetro ou outro campo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
typedef struct _tagFieldInfo {   
   FIELD_INFO_FIELDS dwFields;  
   BSTR              bstrFullName;  
   BSTR              bstrName;  
   BSTR              bstrType;  
   FIELD_MODIFIERS   dwModifiers;  
} FIELD_INFO;  
```  
  
```c#  
public struct FIELD_INFO {  
   public uint   dwFields;  
   public string bstrFullName;  
   public string bstrName;  
   public string bstrType;  
   public uint   dwModifiers;  
};  
```  
  
## <a name="members"></a>Membros  
 dwFields  
 Uma combinação de sinalizadores do [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) enumeração que especifica quais membros são preenchidos.  
  
 bstrFullName  
 O nome completo do campo.  
  
 bstrName  
 O nome curto do campo.  
  
 bstrType  
 O tipo do campo.  
  
 dwModifiers  
 Uma combinação de sinalizadores do [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) enumeração que descreve o campo.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é passada para o [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) método onde ele é preenchido.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
