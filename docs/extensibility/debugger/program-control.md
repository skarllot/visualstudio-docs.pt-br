---
title: Programa de controle | Documentos do Microsoft
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
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
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
ms.openlocfilehash: c8d6b6d07f535ce281473b25f3abc35f56cf6d5f
ms.lasthandoff: 02/22/2017

---
# <a name="program-control"></a>Controle do programa
No Visual Studio a depuração, todos da revisão seguir e continuando rotinas ocorrerem no nível do programa:  
  
-   Ou seja, definir a próxima instrução, configurando seu computador para a próxima instrução a ser executada em um ambiente de quadro específico  
  
-   Ou seja, executar, continuar sair do modo de depuração  
  
-   Passo a passo para a próxima instrução  
  
-   Continuando com o modo de revisão atual  
  
-   Suspender os threads contidos pelo programa  
  
-   Retomando threads contidos pelo programa  
  
> [!NOTE]
>  Exibindo a pilha de chamadas é implementada no nível de thread. Para enumerar as informações do quadro ao exibir a pilha de chamadas para um thread, você deve implementar todos os métodos do [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interface.  
  
## <a name="methods-of-program-control"></a>Métodos de controle do programa  
 A tabela a seguir mostra os métodos de [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) que devem ser implementados para um mecanismo de depuração minimamente funcional (DE) e controle de execução.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continua a execução de todos os segmentos contidos por um programa de um estado parado. Necessário para o controle de execução.|  
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continua a execução de todos os segmentos contidos por um programa de um estado parado. Necessário para o controle de execução.|  
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Executa uma etapa em determinado thread. Continua executando todos os outros threads contidos pelo programa. Necessário para o controle de execução.|  
  
 Para os programas multithread, você também deve implementar o [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) método e todos os métodos do [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) interface.  
  
## <a name="see-also"></a>Consulte também  
 [Controle de execução e avaliação de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)
