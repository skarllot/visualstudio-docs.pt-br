---
title: Processos | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
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
ms.openlocfilehash: bdd6b232a40b284365c31b1ecd21500119619836
ms.lasthandoff: 02/22/2017

---
# <a name="processes"></a>Processos
Em termos de arquitetura do depurador, uma **processo**:  
  
-   É um contêiner para um conjunto de programas. É estreitamente análogo a um processo do Windows, que é um contêiner para um conjunto de threads.  
  
-   Pode identificar-se por nome, identificador ou identificador físico.  
  
-   Pode enumerar todos os programas em execução (e seus threads).  
  
-   Pode descrever em si, a porta está em execução no e o computador que o contém.  
  
-   Pode criar um ou mais programas, encerrar qualquer um dos programas que ele cria ou fazer o programa parar.  
  
-   É representado por um [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) interface, que é criado quando o processo é iniciado. Um processo é iniciado pela sessão depuração Gerenciador do (SDM) ou [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 O pacote de depuração pode anexar um mecanismo de depuração (DE) para um processo chamando [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Isso significa que o DE anexa a todos os possíveis programas em execução no processo que pode manipular. Por exemplo, se o common language runtime DE anexa a um processo, ele anexa somente para programas que estão executando o código gerenciado.  
  
## <a name="see-also"></a>Consulte também  
 [Programas](../../extensibility/debugger/programs.md)   
 [Threads](../../extensibility/debugger/threads.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Pacote de depuração](../../extensibility/debugger/debug-package.md)   
 [Mecanismo de depuração](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Anexar](../../extensibility/debugger/reference/idebugprocess2-attach.md)
