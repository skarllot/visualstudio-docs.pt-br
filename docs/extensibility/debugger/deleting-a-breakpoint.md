---
title: "Excluir um ponto de interrupção | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 7
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
ms.openlocfilehash: 59fc778dbc9bbf8a83ecdbbdaa94827c714b649d
ms.lasthandoff: 02/22/2017

---
# <a name="deleting-a-breakpoint"></a>Excluir um ponto de interrupção
O seguinte descreve o processo ao excluir um ponto de interrupção pendente:  
  
## <a name="deletion-process"></a>Processo de exclusão  
 O Gerenciador de sessão de depuração (SDM) chama o [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) método para remover o ponto de interrupção pendente e acoplados todos os pontos de interrupção associada dele.  
  
> [!NOTE]
>  Um único ponto de interrupção de limite também pode ser excluído por uma chamada a [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>Consulte também  
 [Eventos do depurador de chamada](../../extensibility/debugger/calling-debugger-events.md)
