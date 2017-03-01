---
title: "Encerramento e desanexação | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
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
ms.openlocfilehash: 0ba595f571dac7d861d42456416a52fc67cc0def
ms.lasthandoff: 02/22/2017

---
# <a name="termination-and-detaching"></a>Encerramento e desanexação
O exemplo a seguir descreve um encerramento normal.  
  
## <a name="discussion"></a>Discussão  
 Após o [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) ou [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) continua a interface, se não há nenhuma interrupção, exceções e erros de tempo de execução ou loops infinitos no aplicativo a ser depurado, o programa que está sendo depurado serão executado até a conclusão. Este é um encerramento normal.  
  
 Você deve enviar um [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) para implementar um encerramento normal. Isso requer a implementação de [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [Criando um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)
