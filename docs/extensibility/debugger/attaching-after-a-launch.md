---
title: "Anexar após uma inicialização | Documentos do Microsoft"
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
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
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
ms.openlocfilehash: f3a1385bad429507af8f6b7a39d93fea520f6fd6
ms.lasthandoff: 02/22/2017

---
# <a name="attaching-after-a-launch"></a>Anexar após uma inicialização
Depois que um programa tiver sido iniciado, a sessão de depuração está pronta para conectar o mecanismo de depuração (DE) a esse programa.  
  
## <a name="design-decisions"></a>Decisões de design  
 Porque a comunicação é mais fácil dentro de um espaço de endereço compartilhado, você deve decidir se faz mais sentido para facilitar a comunicação entre a sessão de depuração e DE, ou DE e o programa. Escolha entre os seguintes:  
  
-   Se faz mais sentido para facilitar a comunicação entre a sessão de depuração e DE, a sessão de depuração cria conjunta DE e solicita que o DE anexar ao programa. Isso deixa a sessão de depuração e DE juntos em um espaço de endereço e o ambiente de tempo de execução e o programa juntos em outro.  
  
-   Se faz mais sentido para facilitar a comunicação entre DE e o programa, o ambiente de tempo de execução conjunta cria DE. Isso deixa o SDM em um espaço de endereço e o DE, ambiente de tempo de execução e programa juntos em outro. Isso é típico de a DE que é implementada com um interpretador para executar scripts de idiomas.  
  
    > [!NOTE]
    >  Como o DE anexa ao programa é dependente de implementação. Comunicação entre DE e o programa também é dependente da implementação.  
  
## <a name="implementation"></a>Implementação  
 Programaticamente, quando o Gerenciador de sessão de depuração (SDM) primeiro recebe o [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) o objeto que representa o programa a ser iniciado, ele chama o [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) método, passando um [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) objeto, que é posteriormente usado para passar eventos de depuração para o SDM. O `IDebugProgram2::Attach` método chama o [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método. Para obter mais informações sobre como o SDM recebe o `IDebugProgram2` de interface, consulte [notificar a porta](../../extensibility/debugger/notifying-the-port.md).  
  
 Se seu DE precisa ser executado no mesmo espaço de endereço que o programa que está sendo depurado, normalmente porque o DE é parte de um interpretador de execução de um script, o `IDebugProgramNodeAttach2::OnAttach` método retorna `S_FALSE`, indicando que ele concluído o processo de conexão.  
  
 Se, por outro lado, o DE é executado no espaço de endereço do SDM, o `IDebugProgramNodeAttach2::OnAttach` método retorna `S_OK` ou [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interface não é implementada em todo o [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) objeto associado ao programa que está sendo depurado. Nesse caso, o [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) método eventualmente é chamado para concluir a operação de anexação.  
  
 No último caso, você deve chamar o [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) método no `IDebugProgram2` objeto que foi passado para o `IDebugEngine2::Attach` método, armazenar o `GUID` no programa local do objeto e retornar esse `GUID` quando o `IDebugProgram2::GetProgramId` método é chamado posteriormente neste objeto. O `GUID` é usado para identificar o programa exclusivamente entre os vários componentes de depuração.  
  
 Observe que no caso do `IDebugProgramNodeAttach2::OnAttach` método retornando `S_FALSE`, o `GUID` para usar para o programa é passado ao método e é o `IDebugProgramNodeAttach2::OnAttach` método que define a `GUID` no objeto de programa local.  
  
 O DE agora está conectado ao programa e pronto para enviar os eventos de inicialização.  
  
## <a name="see-also"></a>Consulte também  
 [Anexar diretamente a um programa](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Notificar a porta](../../extensibility/debugger/notifying-the-port.md)   
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Anexar](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Anexar](../../extensibility/debugger/reference/idebugengine2-attach.md)
