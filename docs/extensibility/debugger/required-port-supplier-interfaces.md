---
title: "As Interfaces de fornecedor porta necessárias | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: 13
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
ms.openlocfilehash: 6d61af8ab99715bd19b2abe8b9e961d5cc246498
ms.lasthandoff: 02/22/2017

---
# <a name="required-port-supplier-interfaces"></a>Interfaces de fornecedor porta necessária
Um fornecedor de porta deve implementar o [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interface.[ IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 Como um fornecedor de porta fornece portas, ele também deve implementar. Portanto, ele deve implementar as seguintes interfaces:  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     Descreve a porta e pode enumerar todos os processos em execução na porta.  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Fornece para Iniciando e encerrando processos na porta.  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Fornece um mecanismo para programas em execução no contexto desta porta para notificá-lo de destruição e criação de nó do programa. Para obter mais informações, consulte [programa nós](../../extensibility/debugger/program-nodes.md).  
  
-   `IConnectionPointContainer`  
  
     Fornece um ponto de conexão para [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).  
  
## <a name="port-supplier-operation"></a>Operação de fornecedor de porta  
 O [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) coletor recebe notificações quando o processo e os programas são criados e destruídos em uma porta. Uma porta é obrigatória para enviar [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) quando um processo é criado e [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) quando um processo for destruído na porta. Uma porta também é necessária para enviar [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) quando um programa é criado e [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) quando um programa é destruído em um processo em execução na porta.  
  
 Uma porta normalmente envia programa criar e destruir eventos em resposta ao [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) e [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) métodos, respectivamente.  
  
 Como uma porta pode iniciar e encerrar processos físicos e lógicos programas, essas interfaces também devem ser implementadas pelo mecanismo de depuração:  
  
-   [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     Descreve o processo de física. Pelo menos os seguintes métodos devem ser implementados:  
  
    -   [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    -   [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    -   [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    -   [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
    -   [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
-   [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
     Fornece uma maneira para o SDM anexar e desanexar um processo em si.  
  
-   [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
     Descreve o programa lógico. Pelo menos os seguintes métodos devem ser implementados:  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  
  
    -   [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  
  
    -   [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
-   [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     Fornece uma maneira para o SDM conectar a esse programa.  
  
## <a name="see-also"></a>Consulte também  
 [Implementando um fornecedor de porta](../../extensibility/debugger/implementing-a-port-supplier.md)
