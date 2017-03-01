---
title: Campo TASK_STATE_CANCELED | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TASK_STATE_CANCELED field, Task class [.NET Framework debug engines]
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
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
ms.openlocfilehash: cf050ece5d4e06e51348c4b50fcd8fd180685278
ms.lasthandoff: 02/22/2017

---
# <a name="taskstatecanceled-field"></a>Campo TASK_STATE_CANCELED
A tarefa foi cancelada antes de que atingiu o estado de execução ou confirmados seu cancelamento e concluído sem exceção.  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName></xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (em mscorlib. dll)  
  
 Porque você não pode acessar esse membro interno do .NET Framework, a sintaxe a seguir é fornecida idioma intermediário comum (CIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)  
```  
  
## <a name="remarks"></a>Comentários  
 Se o [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) campo contém esse valor, a <xref:System.Threading.Tasks.Task.Status%2A>propriedade retorna <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.</xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> </xref:System.Threading.Tasks.Task.Status%2A>  
  
## <a name="see-also"></a>Consulte também  
 [Classe Task](../../extensibility/debugger/task-class-internal-members.md)
