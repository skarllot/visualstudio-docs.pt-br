---
title: "Avaliação de pilha de chamadas | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
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
ms.openlocfilehash: 69f3493673a74b8835c4e9fff5d8e14f6088252f
ms.lasthandoff: 02/22/2017

---
# <a name="call-stack-evaluation"></a>Avaliação de pilha de chamada
Para exibir os quadros de pilha da pilha de chamadas durante o modo de interrupção, você deve implementar o [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) método.  
  
## <a name="methods-for-evaluation"></a>Métodos de avaliação  
 Para um mecanismo de depuração simples (DE), pode haver apenas um quadro de pilha. Para examinar o quadro de pilha durante o modo de interrupção, você deve implementar os seguintes métodos de [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Obtém o contexto de código para um quadro de pilha. O contexto do código representa o ponteiro de instrução atual em um quadro de pilha.|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Obtém o contexto do documento para um quadro de pilha. O contexto de documento representa o local no código-fonte para um quadro de pilha atual. Necessário para exibir o código-fonte quando você for interrompido em um programa.|  
  
 Esses métodos exigem a implementação de vários métodos e interfaces relacionadas ao contexto. Portanto, você deve implementar o [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) método e os seguintes métodos de [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Obtém o intervalo de instrução de arquivo de um contexto de documento.|  
  
 Para enumerar os contextos de código, você deve implementar todos os métodos de [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).  
  
## <a name="see-also"></a>Consulte também  
 [Controle de execução e avaliação de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)
