---
title: Campo TASK_STATE_RAN_TO_COMPLETION | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TASK_STATE_RAN_TO_COMPLETION field, Task class [.NET Framework debug engines]
ms.assetid: 0f4830af-fe0c-4141-b768-817f4e426b8c
caps.latest.revision: 8
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
ms.openlocfilehash: 0830375006371f24a25ec7cb91960e6c93734f6d
ms.lasthandoff: 02/22/2017

---
# <a name="taskstaterantocompletion-field"></a>Campo TASK_STATE_RAN_TO_COMPLETION
A execução da tarefa foi concluída com êxito.  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName></xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (em mscorlib. dll)  
  
 Porque você não pode acessar esse membro interno do .NET Framework, a sintaxe a seguir é fornecida idioma intermediário comum (CIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
.field static assembly literal int32 TASK_STATE_RAN_TO_COMPLETION = int32(0x02000000)  
```  
  
## <a name="remarks"></a>Comentários  
 Se o [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) campo contém esse valor, a <xref:System.Threading.Tasks.Task.Status%2A>propriedade retorna <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.</xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> </xref:System.Threading.Tasks.Task.Status%2A>  
  
## <a name="see-also"></a>Consulte também  
 [Classe Task](../../extensibility/debugger/task-class-internal-members.md)
