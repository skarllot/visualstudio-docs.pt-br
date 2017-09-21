---
title: BP_UNBOUND_REASON | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
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
ms.openlocfilehash: c7cc94a3ef2599b5b39fc8c5335a5a065146ef27
ms.lasthandoff: 02/22/2017

---
# <a name="bpunboundreason"></a>BP_UNBOUND_REASON
Fornece o motivo de que um ponto de interrupção foi desassociado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
typedef DWORD BP_UNBOUND_REASON;  
```  
  
```c#  
public enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
```  
  
## <a name="members"></a>Membros  
 BPUR_UNKNOWN  
 O motivo é desconhecido.  
  
 BPUR_CODE_UNLOADED  
 O código que contém o ponto de interrupção foi descarregado.  
  
 BPUR_BREAKPOINT_REBIND  
 O ponto de interrupção tem sido se recuperar para um local diferente. Isso pode acontecer após editar e continuar as operações quando move o ponto de interrupção ou quando o ponto de interrupção é associado a um arquivo com um caminho que não é mais válido.  
  
 BPUR_ BREAKPOINT_ERROR  
 O ponto de interrupção é considerado erro depois que ele está vinculado. Isso acontece para pontos de interrupção gerenciados cujas condições não são mais válidas.  
  
## <a name="remarks"></a>Comentários  
 Retornado pelo [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
