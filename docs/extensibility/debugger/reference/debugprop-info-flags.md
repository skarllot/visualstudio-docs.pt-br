---
title: DEBUGPROP_INFO_FLAGS | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
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
ms.openlocfilehash: c5b749cffbc05fcc3fa6c533dc4bb3bdcd1ad1c0
ms.lasthandoff: 02/22/2017

---
# <a name="debugpropinfoflags"></a>DEBUGPROP_INFO_FLAGS
Especifica quais informações devem ser recuperadas sobre um objeto de propriedade de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
typedef DWORD DEBUGPROP_INFO_FLAGS;  
```  
  
```c#  
public enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
```  
  
## <a name="members"></a>Membros  
 DEBUGPROP_INFO_FULLNAME  
 Inicializar/usar o `bstrFullName` campo.  
  
 DEBUGPROP_INFO_NAME  
 Inicializar/usar o `bstrName` campo.  
  
 DEBUGPROP_INFO_TYPE  
 Inicializar/usar o `bstrType` campo.  
  
 DEBUGPROP_INFO_VALUE  
 Inicializar/usar o `bstrValue` campo.  
  
 DEBUGPROP_INFO_ATTRIB  
 Inicializar/usar o `dwAttrib` campo.  
  
 DEBUGPROP_INFO_PROP,  
 Inicializar/usar o `pProperty` campo que contém um [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interface.  
  
 DEBUGPROP_INFO_VALUE_AUTOEXPAND  
 Especifica que o campo de valor deve conter o valor auto expandida, se disponível, para este tipo de objeto.  
  
 DEBUGPROP_INFO_VALUE_NOFUNCEVAL  
 Preterido.  
  
 DEBUGPROP_INFO_VALUE_RAW  
 Retornar nenhum valores com uma melhor aparência ou membros (ou seja, não formatar os valores).  
  
 DEBUGPROP_INFO_VALUE_NO_TOSTRING  
 Não retornam valores sintetizadas especiais (por exemplo, não chame `ToString()` em um objeto para gerar um valor).  
  
 DEBUGPROP_INFO_NONE  
 Especifica que nenhum sinalizador está definido.  
  
 DEBUGPROP_INFO_STANDARD  
 Inicializar/usar o `dwAttrib`, `bstrName`, `bstrType`, e `bstrValue` campos.  
  
 DEBUGPROP_INFO_All  
 Indica uma máscara de todos os sinalizadores.  
  
## <a name="remarks"></a>Comentários  
 Esses valores são passados para o [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md), e [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) métodos para indicar quais campos devem ser inicializados de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estrutura.  
  
 Esses valores também são usados para o `dwFields` membro o `DEBUG_PROPERTY_INFO` estrutura para indicar quais campos da estrutura são válidos e usadas quando a estrutura é retornada.  
  
 Esses valores podem ser combinados com um bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
