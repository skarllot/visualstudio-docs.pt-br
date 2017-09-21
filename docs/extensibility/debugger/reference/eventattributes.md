---
title: EVENTATTRIBUTES | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
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
ms.openlocfilehash: 9621f2e96b089fe6c5bc7cbfaeb0dce6851dc9e8
ms.lasthandoff: 02/22/2017

---
# <a name="eventattributes"></a>EVENTATTRIBUTES
Especifica os atributos de evento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
typedef DWORD EVENTATTRIBUTES;  
```  
  
```c#  
public enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
```  
  
## <a name="members"></a>Membros  
 EVENT_ASYNCHRONOUS  
 Indica que o evento é assíncrono e não é necessária nenhuma resposta ao evento.  
  
 EVENT_SYNCHRONOUS  
 Indica que o evento é síncrono; responder por meio de [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md).  
  
 EVENT_STOPPING  
 Indica que se trata de um evento de parada. Deve ser combinado com um `EVENT_ASYNCHRONOUS` ou `EVENT_SYNCHRONOUS`.  
  
 EVENT_ASYNC_STOP  
 Indica um evento de interrupção assíncrono. Atualmente, não há nenhum evento. Esse sinalizador é apenas um espaço reservado.  
  
 EVENT_SYNC_STOP  
 Indica um evento de parada síncrona (uma combinação de `EVENT_SYNCHRONOUS` e `EVENT_STOPPING`). Esse valor é usado por um mecanismo de depuração (DE) quando ele envia um evento de parada. A resposta é feita por meio de uma chamada para [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), [etapa](../../../extensibility/debugger/reference/idebugprogram2-step.md), ou [continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
 EVENT_IMMEDIATE  
 Indica um evento que é enviado imediatamente e de forma síncrona ao IDE. Esse sinalizador é combinado com outros sinalizadores como `EVENT_ASYNCHRONOUS`, `EVENT_SYNCHRONOUS`, ou `EVENT_SYNC_STOP` para indicar o tipo de evento e o fato de que o mecanismo de resposta (se houver) é conhecido.  
  
 EVENT_EXPRESSION_EVALUATION  
 O evento é um resultado da avaliação da expressão.  
  
## <a name="remarks"></a>Comentários  
 Esses valores são passados a `dwAttrib` parâmetro o [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) método.  
  
 Esses valores podem ser combinados com um bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
