---
title: "Método GetTaskSchedulersForDebugger | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
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
ms.openlocfilehash: de3096d92fc118eb42087fca060b74329b09cccd
ms.lasthandoff: 02/22/2017

---
# <a name="gettaskschedulersfordebugger-method"></a>Método GetTaskSchedulersForDebugger
Recupera uma matriz de todos os <xref:System.Threading.Tasks.TaskScheduler>objetos que estão atualmente ativos.</xref:System.Threading.Tasks.TaskScheduler>  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName></xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (em mscorlib. dll)  
  
 Porque você não pode acessar esse membro interno do .NET Framework, a sintaxe a seguir é fornecida idioma intermediário comum (CIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Uma matriz de todos os <xref:System.Threading.Tasks.TaskScheduler>objetos que estão atualmente ativos nesta <xref:System.AppDomain>.</xref:System.AppDomain> </xref:System.Threading.Tasks.TaskScheduler>  
  
## <a name="remarks"></a>Comentários  
 Esse método não é thread-safe e não deve ser usado simultaneamente com outras instâncias do <xref:System.Threading.Tasks.TaskScheduler>.</xref:System.Threading.Tasks.TaskScheduler> Ele deve ser chamado de um depurador somente quando o depurador suspendeu a todos os outros threads.  
  
## <a name="see-also"></a>Consulte também  
 [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)
