---
title: Notificar a porta | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
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
ms.openlocfilehash: 0495ec0240c6087bc77661b47c1a468ff752990c
ms.lasthandoff: 02/22/2017

---
# <a name="notifying-the-port"></a>Notificar a porta
Depois de iniciar um programa, a porta deve ser notificada, da seguinte maneira:  
  
1.  Quando uma porta recebe um novo nó de programa, ele envia um evento de criação do programa volta para a sessão de depuração. O evento carrega uma interface que representa o programa.  
  
2.  A sessão de depuração consulta o programa para o identificador de um mecanismo de depuração (DE) que pode ser anexados a.  
  
3.  A sessão de depuração verifica para ver se o DE está na lista de DEs permitido para o programa. A sessão de depuração obtém essa lista de configurações de programa ativo da solução, originalmente passadas a ele pelo pacote de depuração.  
  
     O DE deve estar na lista permitida, senão a DE não será anexada ao programa.  
  
 Programaticamente, quando uma porta recebe primeiro um novo nó de programa, ele cria um [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interface para representar o programa.  
  
> [!NOTE]
>  Isso não deve ser confundido com o `IDebugProgram2` interface criada posteriormente pelo mecanismo de depuração (DE).  
  
 A porta envia um [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) eventos de criação do programa volta para o Gerenciador de depuração de sessão (SDM) por meio de uma COM `IConnectionPoint` interface.  
  
> [!NOTE]
>  Isso não deve ser confundido com o `IDebugProgramCreateEvent2` interface, que é enviado posteriormente por DE.  
  
 Junto com a interface de eventos em si, a porta envia o [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md), e [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfaces, que representam a porta, o processo e o programa, respectivamente. As chamadas SDM [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) para obter o GUID DE que pode depurar o programa. O GUID originalmente foi obtido o [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interface.  
  
 O SDM verifica para ver se o DE está na lista de DEs permitido. O SDM obtém essa lista de configurações de programa ativo da solução, originalmente passadas a ele pelo pacote de depuração. O DE deve estar na lista permitida, caso contrário, não será anexado ao programa.  
  
 Depois que a identidade do DE é conhecida, o SDM está pronto para anexá-lo para o programa.  
  
## <a name="see-also"></a>Consulte também  
 [Iniciando um programa](../../extensibility/debugger/launching-a-program.md)   
 [Anexar após uma inicialização](../../extensibility/debugger/attaching-after-a-launch.md)   
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)
