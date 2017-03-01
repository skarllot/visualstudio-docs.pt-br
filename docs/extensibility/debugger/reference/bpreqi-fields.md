---
title: BPREQI_FIELDS | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
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
ms.openlocfilehash: c44847ef0f5f15e4c8b966b067feb89e91230b96
ms.lasthandoff: 02/22/2017

---
# <a name="bpreqifields"></a>BPREQI_FIELDS
Especifica as informações a serem recuperadas sobre uma solicitação de ponto de interrupção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
typedef DWORD BPREQI_FIELDS;  
```  
  
```c#  
public enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
```  
  
## <a name="members"></a>Membros  
 BPREQI_BPLOCATION  
 Inicializar/usar o `bpLocation` campo (localização do ponto de interrupção) do [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) ou [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) estrutura.  
  
 BPREQI_LANGUAGE  
 Inicializar/usar o `guidLanguage` campo o `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.  
  
 BPREQI_PROGRAM  
 Inicializar/usar o `pProgram` campo o `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.  
  
 BPREQI_PROGRAMNAME  
 Inicializar/usar o `bstrProgramName` campo o `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.  
  
 BPREQI_THREAD  
 Inicializar/usar o `pThread` campo o `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.  
  
 BPREQI_THREADNAME  
 Inicializar/usar o `bstrThreadName` campo o `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.  
  
 BPREQI_PASSCOUNT  
 Inicializar/usar o `bpPassCount` campo o `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.  
  
 BPREQI_CONDITION  
 Inicializar/usar o `bpCondition` campo (condição de ponto de interrupção) do `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.  
  
 BPREQI_FLAGS  
 Inicializar/usar o `dwFlags` campo o `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.  
  
 BPREQI_ALLOLDFIELDS  
 Inicializar/usar todos os campos para o do `BP_REQUEST_INFO` estrutura.  
  
 BPREQI_VENDOR  
 Inicializar/usar o `guidVendor` campo `BP_REQUEST_INFO2` estrutura.  
  
 BPREQI_CONSTRAINT  
 Inicializar/usar o `bstrConstraint` campo `BP_REQUEST_INFO2` estrutura.  
  
 BPREQI_TRACEPOINT  
 Inicializar/usar o `bstrTracepoint` campo `BP_REQUEST_INFO2` estrutura.  
  
 BPREQI_ALLFIELDS  
 Especifica todos os campos para o `BP_REQUEST_INFO2` estrutura.  
  
## <a name="remarks"></a>Comentários  
 Passada como um argumento para o [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) e [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) métodos para especificar quais campos do [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) estruturas devem ser inicializado.  
  
 Esses sinalizadores também são usados para indicar quais campos do `BP_REQUEST_INFO` e `BP_REQUEST_INFO2` estruturas são usados e válidos quando cada estrutura é retornada.  
  
 Esses valores podem ser combinados com um bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
