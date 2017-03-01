---
title: Classe - membros internos de tarefa | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
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
ms.openlocfilehash: 21acb0a52dfde7ad565e9764e2a333a9925a2171
ms.lasthandoff: 02/22/2017

---
# <a name="task-class---internal-members"></a>Classe Task - membros internos
Este tópico descreve os membros internos da <xref:System.Threading.Tasks.Task?displayProperty=fullName>classe ajudá-lo a implementar um depurador personalizado.</xref:System.Threading.Tasks.Task?displayProperty=fullName> Para obter informações gerais sobre essa classe, consulte o <xref:System.Threading.Tasks.Task>tópico de referência.</xref:System.Threading.Tasks.Task>  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName></xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (em mscorlib. dll)  
  
 Porque você não pode acessar esses membros internos do .NET Framework, a sintaxe a seguir é fornecida idioma intermediário comum (CIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
.class public auto ansi System.Threading.Tasks.Task  
       extends System.Object  
       implements System.Threading.IThreadPoolWorkItem,  
                  System.IAsyncResult,  
                  System.IDisposable,  
                  System.Threading.ICancelableOperation  
```  
  
## <a name="members"></a>Membros  
  
### <a name="methods"></a>Métodos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[Método SetNotificationForWaitCompletion](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Define ou limpa o bit de estado TASK_STATE_WAIT_COMPLETION_NOTIFICATION.|  
|[Método NotifyDebuggerOfWaitCompletion](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Método de espaço reservado usado como um destino de ponto de interrupção pelo depurador.|  
  
### <a name="fields"></a>Campos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[m_action](../../extensibility/debugger/m-action-field.md)|O delegado que representa o código para executar no <xref:System.Threading.Tasks.Task>objeto.</xref:System.Threading.Tasks.Task>|  
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Armazena propriedades adicionais de <xref:System.Threading.Tasks.Task>objeto.</xref:System.Threading.Tasks.Task>|  
|[m_Parent](../../extensibility/debugger/m-parent-field.md)|O campo existente para o <xref:System.Threading.Tasks.Task?displayProperty=fullName>propriedade parent.</xref:System.Threading.Tasks.Task?displayProperty=fullName>|  
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Armazena informações sobre o estado atual do <xref:System.Threading.Tasks.Task>objeto.</xref:System.Threading.Tasks.Task>|  
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Um objeto que representa os dados que serão usados pela ação.|  
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|O campo existente para o <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName>propriedade.</xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName>|  
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|O próximo identificador disponível para um <xref:System.Threading.Tasks.Task>objeto.</xref:System.Threading.Tasks.Task>|  
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Indica que a tarefa foi cancelada antes de que atingiu o estado de execução ou que a tarefa confirmada seu cancelamento e concluída sem exceção.|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Indica que a tarefa está em execução.|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Indica que a tarefa foi concluída devido a uma exceção sem tratamento.|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Indica que a tarefa de execução concluída com êxito.|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Indica que a tarefa terminou de executar seu representante e está aguardando implicitamente tarefas filhas anexadas sejam concluídas.|  
  
## <a name="remarks"></a>Comentários  
 Os seguintes métodos internos são úteis para um mecanismo de depuração porque eles marcam a entrada para <xref:System.Threading.Tasks.Task>a execução de código:</xref:System.Threading.Tasks.Task>  
  
-   `Execute`  
  
-   `ExecuteEntry`  
  
-   `ExecuteWithThreadLocal`  
  
-   `Finish`  
  
-   `InnerInvoke`  
  
-   `InternalWait`  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName></xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [Elementos internos de extensões paralelas para o .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
