---
title: "Avaliação de expressão (depuração do Visual Studio SDK) | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
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
ms.openlocfilehash: 68773ccac304972f4d96642a226a586d69efb783
ms.lasthandoff: 02/22/2017

---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Avaliação de expressão (depuração do Visual Studio SDK)
Durante o modo de interrupção, o IDE deve ser capaz de avaliar expressões simples envolvendo diversas variáveis do programa. Para fazer isso, o mecanismo de depuração (DE) deve ser capaz de analisar e avaliar uma expressão que é inserida em uma das janelas do IDE.  
  
 As expressões são criadas usando o [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método e são representados por resultante [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface.  
  
 O **IDebugExpression2** interface é implementada pelo chamadas e DE suas **EvalAsync** método retorne um [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface IDE, para exibir os resultados da avaliação de expressão no IDE. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) retorna uma estrutura que pode ser usada para colocar o valor de uma expressão em uma janela de observação ou a janela locais.  
  
 O pacote ou a sessão de depuração Gerenciador de depuração (SDM) chama [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) ou [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) para obter um [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface que representa o resultado da avaliação. `IDebugProperty2`tem métodos que retornam o nome, tipo e valor da expressão. Essas informações são exibidas em várias janelas do depurador.  
  
## <a name="using-expression-evaluation"></a>Usando a avaliação de expressão  
 Para usar a avaliação da expressão, você deve implementar o [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método e todos os métodos do [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) de interface, conforme mostrado na tabela a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Avalia uma expressão assíncrona.|  
|[Anular](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termina a avaliação da expressão assíncrona.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Avalia uma expressão de forma síncrona.|  
  
 Avaliação síncrona e assíncrona requerem a implementação do [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) método. Avaliação de expressão assíncrona requer a implementação de [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## <a name="see-also"></a>Consulte também  
 [Controle de execução e avaliação de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)
