---
title: "Controle de execução | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
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
ms.openlocfilehash: 5e13a3545f9b714eef336b9184910bef13f9f59b
ms.lasthandoff: 02/22/2017

---
# <a name="control-of-execution"></a>Controle de execução
O mecanismo de depuração (DE) normalmente envia um dos eventos a seguir como o último evento de inicialização:  
  
-   O evento de ponto de entrada, se anexar a um programa acabou de ser iniciado  
  
-   O evento load concluída, se anexar a um programa que já está em execução  
  
 Ambos esses eventos são eventos de parada, que significa que o DE espera por uma resposta do usuário por meio do IDE. Para obter mais informações, consulte [modos operacionais](../../extensibility/debugger/operational-modes.md).  
  
## <a name="stopping-event"></a>Interrompendo o evento  
 Quando um evento de interrupção é enviado para a sessão de depuração:  
  
1.  O programa e o thread que contêm o ponteiro de instrução atual podem ser obtidos a interface de eventos.  
  
2.  O IDE determina o arquivo de código de origem atual e a posição que ele exibe realçado no editor.  
  
3.  A sessão de depuração normalmente responde a este evento de interrupção primeiro chamando o programa **continuar** método.  
  
4.  O programa executa até encontrar uma condição de interrupção, como atingir um ponto de interrupção, na qual o caso DE envia um evento de ponto de interrupção para a sessão de depuração. O ponto de interrupção é um evento de parada e o DE novamente aguarda uma resposta do usuário.  
  
5.  Se o usuário opta por entrar, mais ou fora de uma função, o IDE solicita que a sessão de depuração para chamar o programa `Step` método, passando a unidade da etapa (instrução, a instrução ou linha) e o tipo de etapa — ou seja, se entrar em, acima ou da função. Quando a etapa for concluída, o DE envia um evento de conclusão de etapa para a sessão de depuração, que é um evento de parada.  
  
     -ou-  
  
     Se o usuário optar por continuar a execução a partir do ponteiro de instrução atual, o IDE solicita que a sessão de depuração para chamar o programa **Execute** método. O programa continua a execução até que ele encontra a próxima condição de interrupção.  
  
     -ou-  
  
     Se a sessão de depuração é ignorar um evento de interrupção específico, a sessão de depuração chama o programa **continuar** método. Se o programa foi revisão em, acima ou fora de uma função ao encontrou a condição de interrupção, ele continua a etapa.  
  
 Programaticamente, quando o DE encontra uma condição de interrupção, ele envia eventos parando como [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) ou [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) para o Gerenciador de depuração de sessão (SDM) por meio de um [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) interface. Os passos da [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) e [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interfaces que representam o programa e o segmento que contém o ponteiro de instrução atual. As chamadas SDM [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) para obter o quadro superior da pilha e chamadas [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) para obter o contexto de documento associado com o ponteiro de instrução atual. Este contexto de documento geralmente é um número de coluna, linha e nome de arquivo do código fonte. O IDE usa para realçar o código-fonte que contém o ponteiro de instrução atual.  
  
 O SDM normalmente responde a este evento de interrupção primeiro chamando [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). O programa executa até encontrar uma condição de interrupção, como atingir um ponto de interrupção, que envia o caso DE um [IDebugBreakpointEvent2 Interface](../../extensibility/debugger/reference/idebugbreakpointevent2.md) para o SDM. O ponto de interrupção é um evento de parada e o DE novamente aguarda uma resposta do usuário.  
  
 Se o usuário opta por entrar, mais ou fora de uma função, o IDE solicita o SDM para chamar [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md), passando a ele o [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (instrução, a instrução ou linha) e o [STEPKIND](../../extensibility/debugger/reference/stepkind.md), ou seja, se entrar em, acima ou da função. Quando a etapa for concluída, o DE envia um [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) interface para o SDM, que é um evento de parada.  
  
 Se o usuário optar por continuar a execução a partir do ponteiro de instrução atual, o IDE solicita o SDM para chamar [IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md). O programa continua a execução até que ele encontra a próxima condição de interrupção.  
  
 Se o pacote de depuração é ignorar um evento de interrupção específico, o pacote de depuração chama o SDM, que chama [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Se o programa foi revisão em, acima ou fora de uma função ao encontrou a condição de interrupção, ele continua a etapa. Isso implica que o programa mantém um estado passo a passo, para que ele saiba como continuar.  
  
 As chamadas que torna o SDM `Step`, **Execute**, e **continuar** são assíncrona, o que significa que o SDM espera a chamada para retornar rapidamente. Se o DE envia o SDM um evento de interrupção no mesmo segmento antes de `Step`, **Execute**, ou **continuar** retorna, o SDM trava.  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)
