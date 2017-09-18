---
title: DEBUGREF_INFO_FLAGS | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
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
ms.openlocfilehash: 434428f484a3d9ce7c9e27c49088ef27a1e9f086
ms.lasthandoff: 02/22/2017

---
# <a name="debugrefinfoflags"></a>DEBUGREF_INFO_FLAGS
Especifica quais informações devem ser recuperadas sobre um objeto de referência de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
typedef DWORD DEBUGREF_INFO_FLAGS;  
```  
  
```c#  
public enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
```  
  
## <a name="members"></a>Membros  
 DEBUGREF_INFO_NAME  
 Inicializar/usar o `bstrName` campo na estrutura.  
  
 DEBUGREF_INFO_TYPE  
 Inicializar/usar o `bstrType` campo na estrutura.  
  
 DEBUGREF_INFO_VALUE  
 Inicializar/usar o `bstrValue` campo na estrutura.  
  
 DEBUGREF_INFO_ATTRIB  
 Inicializar/usar o `dwAttrib` campo na estrutura.  
  
 DEBUGREF_INFO_REFTYPE  
 Inicializar/usar o `dwRefType` campo na estrutura.  
  
 DEBUGREF_INFO_REF  
 Inicializar/usar o `pReference` campo na estrutura.  
  
 DEBUGREF_INFO_VALUE_AUTOEXPAND  
 O campo de valor deve conter valor expandida automaticamente, se disponível, para este tipo de objeto.  
  
 DEBUGREF_INFO_NONE  
 Indica que nenhum sinalizador está definido.  
  
 DEBUGREF_INFO_ALL  
 Indica uma máscara dos sinalizadores.  
  
## <a name="remarks"></a>Comentários  
 Esses sinalizadores são passados para o [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) e [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) métodos para indicar quais campos do [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estrutura devem ser inicializado.  
  
 Usado para o `dwFields` membro o `DEBUG_REFERENCE_INFO` estrutura para indicar quais campos são usados e válida quando a estrutura é retornada.  
  
 Esses valores podem ser combinados com um bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
