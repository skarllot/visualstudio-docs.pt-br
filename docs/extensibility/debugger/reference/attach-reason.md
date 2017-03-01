---
title: ATTACH_REASON | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
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
ms.openlocfilehash: 4b612b1af74298d2c3ef97611c262a6c31cb6db1
ms.lasthandoff: 02/22/2017

---
# <a name="attachreason"></a>ATTACH_REASON
Especifica o motivo para o mecanismo de depuração (DE) para anexar a um nó de programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
typedef DWORD ATTACH_REASON;  
```  
  
```c#  
public enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
```  
  
## <a name="members"></a>Membros  
 ATTACH_REASON_AUTO  
 Anexe porque o processo está em modo de depuração.  
  
 ATTACH_REASON_LAUNCH  
 Anexe porque o processo foi iniciado.  
  
 ATTACH_REASON_USER  
 Anexe devido a uma solicitação de usuário.  
  
## <a name="remarks"></a>Comentários  
 Esses valores são usados como um parâmetro para o [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) e [Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) métodos.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Anexar](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Anexar](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)
