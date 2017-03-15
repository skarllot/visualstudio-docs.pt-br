---
title: "Método SetNotificationForWaitCompletion | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
caps.latest.revision: 5
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
ms.openlocfilehash: 95789b92fe107181b34af86521be7306bcf372b4
ms.lasthandoff: 02/22/2017

---
# <a name="setnotificationforwaitcompletion-method"></a>Método SetNotificationForWaitCompletion
Define ou limpa o bit de estado TASK_STATE_WAIT_COMPLETION_NOTIFICATION.  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName></xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (em mscorlib. dll)  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `enabled`  
  
 `true`Para definir o bit; `false` para desproteger o bit.  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
 O depurador definirá esse bit para ajudar a sair de um corpo de método assíncrono. Se `enabled` é `true`, esse método deve ser chamado somente em uma tarefa que ainda não foram concluída. Se `enabled` é `false`, esse método pode ser chamado em tarefas concluídas. Em ambos os casos, ele só deve ser usado para tarefas de estilo de promessa.  
  
## <a name="requirements"></a>Requisitos  
  
## <a name="see-also"></a>Consulte também  
 [Classe Task](../../extensibility/debugger/task-class-internal-members.md)
