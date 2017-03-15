---
title: Suporte para tipos de evento | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
caps.latest.revision: 12
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
ms.openlocfilehash: a1f797ef000f853ce25335f14feb0e9ec1a9be70
ms.lasthandoff: 02/22/2017

---
# <a name="supported-event-types"></a>Tipos de eventos com suporte
Depuração do Visual Studio atualmente suporta os seguintes tipos de evento:  
  
-   Eventos assíncronos  
  
     Notificar o Gerenciador de sessão de depuração (SDM) e o IDE está alterando o estado do aplicativo que está sendo depurado. Esses eventos são processados em tempo de livre do SDM e o IDE. Nenhuma resposta é enviada ao mecanismo de depuração (DE) após o evento é processado. O [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) e [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) interfaces são exemplos de eventos assíncronos.  
  
-   Eventos síncronos  
  
     Notificar o SDM e o IDE está alterando o estado do aplicativo que está sendo depurado. A única diferença entre esses eventos e eventos assíncronos é que uma resposta é enviada por meio do [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) método.  
  
     Enviar um evento síncrono é útil se você precisar DE sua para continuar o processamento depois que o IDE recebe e processa o evento.  
  
-   Eventos de parada de síncrono ou eventos de parada  
  
     Notificar o SDM e o IDE que o aplicativo que está sendo depurado parou a execução de código. Quando você envia um evento de parada por meio do método [evento](../../extensibility/debugger/reference/idebugeventcallback2-event.md), o [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) parâmetro é necessário. Interrompendo eventos continuam por uma chamada para um dos seguintes métodos:  
  
    -   [Executar](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
    -   [Etapa](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
    -   [Continuar](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
     As interfaces [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) e [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) são exemplos de eventos de interrupção.  
  
    > [!NOTE]
    >  Não há suporte para eventos de interrupção assíncrono. É um erro ao enviar um evento de interrupção assíncrono.  
  
## <a name="discussion"></a>Discussão  
 A implementação real de eventos depende do design do seu DE. O tipo de cada evento enviado é determinado por seus atributos, que são definidos quando você projeta o DE. Por exemplo, um DE pode enviar um [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) como um evento assíncrono, enquanto outro pode enviá-lo como um evento de parada.  
  
 A tabela a seguir especifica os parâmetros do programa e thread são necessários para os eventos, bem como tipos de eventos. Qualquer evento pode ser síncrono. Nenhum evento precisa ser síncronas.  
  
> [!NOTE]
>  O [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) interface é necessária para todos os eventos.  
  
|Evento|IDebugProgram2|IDebugThread2|Eventos de parada|  
|-----------|--------------------|-------------------|---------------------|  
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Permitido, mas não obrigatórios|Permitido, mas não obrigatórios|Não|  
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Necessária|Necessária|Sim|  
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Permitido, mas não obrigatórios|Permitido, mas não obrigatórios|Não|  
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Permitido, mas não obrigatórios|Permitido, mas não obrigatórios|Não|  
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Permitido, mas não obrigatórios|Permitido, mas não obrigatórios|Não|  
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Necessária|Necessária|Sim|  
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Necessária|Necessária|Não|  
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Não permitido|Não permitido|Não|  
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Não permitido|Não permitido|Não|  
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Necessária|Necessária|Sim|  
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Permitido, mas não obrigatórios|Permitido, mas não obrigatórios|Pode ser|  
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Necessária|Necessária|Sim|  
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Permitido, mas não obrigatórios|Permitido, mas não obrigatórios|Pode ser|  
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Necessária|Necessária|Sim|  
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Necessária|Necessária|Sim|  
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Permitido, mas não obrigatórios|Permitido, mas não obrigatórios|Pode ser|  
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Necessária|Permitido, mas não obrigatórios|Não|  
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Permitido, mas não obrigatórios|Permitido, mas não obrigatórios|Não|  
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Necessária|Permitido, mas não obrigatórios|Não|  
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Necessária|Permitido, mas não obrigatórios|Não|  
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Necessária|Permitido, mas não obrigatórios|Não|  
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Necessária|Permitido, mas não obrigatórios|Não|  
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Permitido, mas não obrigatórios|Permitido, mas não obrigatórios|Não|  
|IDebugStopCompleteEvent2|Necessária|Necessária|Sim|  
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Necessária|Necessária|Sim|  
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Permitido, mas não obrigatórios|Permitido, mas não obrigatórios|Não|  
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Necessária|Necessária|Não|  
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Necessária|Necessária|Não|  
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Permitido, mas não obrigatórios|Permitido, mas não obrigatórios|Não|  
  
## <a name="see-also"></a>Consulte também  
 [Envio de eventos](../../extensibility/debugger/sending-events.md)
