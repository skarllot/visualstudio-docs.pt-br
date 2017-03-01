---
title: Classe TaskScheduler - membros internos | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
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
ms.openlocfilehash: 1939b612252f8708c24e8045c5102405421ce143
ms.lasthandoff: 02/22/2017

---
# <a name="taskscheduler-class---internal-members"></a>Classe TaskScheduler - membros internos
Este tópico descreve os membros internos da <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>classe ajudá-lo a implementar um depurador personalizado.</xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> Para obter informações gerais sobre essa classe, consulte o <xref:System.Threading.Tasks.TaskScheduler>tópico de referência.</xref:System.Threading.Tasks.TaskScheduler>  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName></xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (em mscorlib. dll)  
  
 Porque você não pode acessar esses membros internos do .NET Framework, a sintaxe a seguir é fornecida idioma intermediário comum (CIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler  
       extends System.Object  
```  
  
## <a name="members"></a>Membros  
  
### <a name="methods"></a>Métodos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Recupera uma matriz de todas as tarefas agendadas.|  
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Recupera uma matriz de todos os <xref:System.Threading.Tasks.TaskScheduler>objetos que estão atualmente ativos.</xref:System.Threading.Tasks.TaskScheduler>|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName></xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Elementos internos de extensões paralelas para o .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
