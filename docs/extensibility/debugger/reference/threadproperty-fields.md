---
title: THREADPROPERTY_FIELDS | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
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
ms.openlocfilehash: 232106157f782e13c111589f36ed7b1583854299
ms.lasthandoff: 02/22/2017

---
# <a name="threadpropertyfields"></a>THREADPROPERTY_FIELDS
Especifica quais informações sobre um segmento a ser recuperado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD THREADPROPERTY_FIELDS;  
```  
  
```c#  
public enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>Membros  
 TPF_ID  
 Inicializar/usar o `dwThreadId` campo o [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) estrutura.  
  
 TPF_SUSPENDCOUNT  
 Inicializar/usar o `dwSuspendCount` campo o `THREADPROPERTIE`estrutura.  
  
 TPF_STATE  
 Inicializar/usar o `dwThreadState` campo o `THREADPROPERTIE`estrutura.  
  
 TPF_PRIORITY  
 Inicializar/usar o `bstrPriority` campo o `THREADPROPERTIE`estrutura.  
  
 TPF_NAME  
 Inicializar/usar o `bstrName` campo o `THREADPROPERTIE`estrutura.  
  
 TPF_LOCATION  
 Inicializar/usar o `bstrLocation` campo o `THREADPROPERTIE`estrutura.  
  
 TPF_ALLFIELDS  
 Especifica todos os campos.  
  
## <a name="remarks"></a>Comentários  
 Esses valores são passados como um argumento para o [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) método para indicar quais campos do [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) estrutura devem ser inicializado.  
  
 Esses valores também são usados em `dwFields` membro o `THREADPROPERTIES` estrutura para indicar quais campos são usados e válido.  
  
 Esses sinalizadores podem ser combinados com um bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
