---
title: Programas | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: 12
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
ms.openlocfilehash: 982d966208433905115e76a36d358c656005e3d3
ms.lasthandoff: 02/22/2017

---
# <a name="programs"></a>Programas
Em termos de arquitetura do depurador, uma **programa**:  
  
-   É um contêiner para um conjunto de threads e um conjunto de módulos. Um programa não tem nenhum única analogia no sistema operacional Windows.  
  
     Um programa é um tipo de subprocesso. Por exemplo, quando você estiver depurando um site da Web, um script pode ser visto como um programa. Embora um script é executado no processo do mecanismo de script, independente dos outros scripts, ele também tem seu próprio conjunto de threads. Um mecanismo de depuração (DE) anexa a um programa e não a um processo ou um thread.  
  
-   Pode identificar em si e o processo está executando e podem ser anexado para ser desconectado da e descrevem o DE que o criou, se houver. Um programa pode executar, interromper, continuar e ser encerrada.  
  
-   Pode enumerar todos os segmentos. Um programa também pode fornecer seu próprio fluxo de desmontagem e pode enumerar todos os contextos de código da posição de um determinado documento.  
  
-   É representado por um [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interface, criada para o programa está anexado, ou como parte do processo de anexação, dependendo da implementação. Quando uma porta enumera os programas de um processo, cada programa é criado de acordo com um correspondente [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interface é passada como um argumento para [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Embora os mecanismos de depuração também criar `IDebugProgram2` interfaces para representar programas, esses programas não são criados de acordo com um nó de programa. O `IDebugProgramNode2` interfaces criados por um DE são usados para depuração real, enquanto aquelas criadas por uma porta são usadas apenas para descobrir quais programas estão em execução em um processo.  
  
## <a name="see-also"></a>Consulte também  
 [Processos](../../extensibility/debugger/processes.md)   
 [Nós de programa](../../extensibility/debugger/program-nodes.md)   
 [Módulos](../../extensibility/debugger/modules.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Mecanismo de depuração](../../extensibility/debugger/debug-engine.md)   
 [Posição do documento](../../extensibility/debugger/document-position.md)   
 [Contexto de código](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
