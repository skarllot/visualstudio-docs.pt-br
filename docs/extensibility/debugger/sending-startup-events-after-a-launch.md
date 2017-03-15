---
title: "Enviar eventos de inicialização após uma inicialização | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: 9
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
ms.openlocfilehash: 72d390f9abeb939673a8fca0f5b4e3cb6b8de05e
ms.lasthandoff: 02/22/2017

---
# <a name="sending-startup-events-after-a-launch"></a>Enviar eventos de inicialização após uma inicialização
Depois que o mecanismo de depuração (DE) é anexado ao programa, ele envia uma série de eventos de inicialização para a sessão de depuração.  
  
 Inicializar eventos enviados de volta para a sessão de depuração incluem o seguinte:  
  
-   Um evento de criação do mecanismo.  
  
-   Um evento de criação do programa.  
  
-   Criação e eventos de módulo de carregamento do thread.  
  
-   Um evento complete carga, enviado quando o código é carregado e pronto para ser executado, mas antes de qualquer código é executado  
  
    > [!NOTE]
    >  Quando esse evento é continuado, variáveis globais são inicializadas e executar rotinas de inicialização.  
  
-   Outros possíveis thread criação e eventos de módulo de carregamento.  
  
-   Um evento de ponto de entrada, que sinaliza que o programa atingiu seu ponto de entrada principal, como **principal** ou `WinMain`. Esse evento não é enviado normalmente se o DE anexa a um programa que já está em execução.  
  
 O DE programaticamente, primeiro o Gerenciador de sessão de depuração (SDM) envia uma [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) interface, que representa um evento de criação do mecanismo, seguido por um [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), que representa um evento de criação do programa.  
  
 Isso é normalmente seguido por um ou mais [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) eventos de criação de threads e [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) eventos de módulo de carregamento.  
  
 Quando o código é carregado e pronto para ser executado, mas antes de qualquer código é executado, o DE envia o SDM um [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) carga completa de eventos. Por fim, se o programa não estiver sendo executado, o DE envia um [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) evento de ponto de entrada, sinalizando que o programa atingiu seu ponto de entrada principal e está pronto para depuração.  
  
## <a name="see-also"></a>Consulte também  
 [Controle de execução](../../extensibility/debugger/control-of-execution.md)   
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)
