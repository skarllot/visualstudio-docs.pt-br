---
title: Campo TASK_STATE_WAITING_ON_CHILDREN | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TASK_STATE_WAITING_ON_CHILDREN field, Task class [.NET Framework debug engines]
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
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
ms.openlocfilehash: a6f74db2f27a944ac1b7f499baafb5a5288a9e45
ms.lasthandoff: 02/22/2017

---
# <a name="taskstatewaitingonchildren-field"></a>Campo TASK_STATE_WAITING_ON_CHILDREN
A tarefa terminou de executar seu representante e implicitamente está aguardando conclusão de tarefas filhas anexadas.  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName></xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (em mscorlib. dll)  
  
 Porque você não pode acessar esse membro interno do .NET Framework, a sintaxe a seguir é fornecida idioma intermediário comum (CIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)  
```  
  
## <a name="remarks"></a>Comentários  
 Se o [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) campo contém esse valor, a <xref:System.Threading.Tasks.Task.Status%2A>propriedade retorna <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.</xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> </xref:System.Threading.Tasks.Task.Status%2A>  
  
## <a name="see-also"></a>Consulte também  
 [Classe Task](../../extensibility/debugger/task-class-internal-members.md)
