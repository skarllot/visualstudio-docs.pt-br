---
title: Anexar e desanexar um programa | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
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
ms.openlocfilehash: 861417a42f0b8fa3361aa99b9aeec1b3755e44a7
ms.lasthandoff: 02/22/2017

---
# <a name="attaching-and-detaching-to-a-program"></a>Anexar e desanexar a um programa
Anexando o depurador requer o envio de sequência correta de métodos e eventos com os atributos apropriados.  
  
## <a name="sequence-of-methods-and-events"></a>Sequência de métodos e eventos  
  
1.  O Gerenciador de sessão de depuração (SDM) chama o [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método.  
  
     Com base no modelo de processo do mecanismo (DE) de depuração, o `IDebugProgramNodeAttach2::OnAttach` método retorna um dos métodos a seguir, que determina o que acontece em seguida.  
  
     Se `S_FALSE` for retornado, o mecanismo de depuração foi anexado com êxito para o programa. Caso contrário, o [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) método será chamado para concluir o processo de conexão.  
  
     Se `S_OK` for retornado, o DE deve ser carregado no mesmo processo que o SDM. O SDM realiza as seguintes tarefas:  
  
    1.  Chamadas [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) para obter as informações de mecanismo de.  
  
    2.  Cria conjunta DE.  
  
    3.  Chamadas [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
2.  O envio DE um [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) para o SDM com um `EVENT_SYNC` atributo.  
  
3.  O envio DE um [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) para o SDM com um `EVENT_SYNC` atributo.  
  
4.  O envio DE um [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) para o SDM com um `EVENT_SYNC_STOP` atributo.  
  
 Desanexação de um programa é um simples, o processo de duas etapas, da seguinte maneira:  
  
1.  As chamadas SDM [desanexar](../../extensibility/debugger/reference/idebugprogram2-detach.md).  
  
2.  O envio DE um [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).  
  
## <a name="see-also"></a>Consulte também  
 [Eventos do depurador de chamada](../../extensibility/debugger/calling-debugger-events.md)
