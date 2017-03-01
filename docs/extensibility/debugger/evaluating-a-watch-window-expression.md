---
title: "Avaliar uma expressão de janela Inspeção | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
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
ms.openlocfilehash: 22b0baf1fdfd9b33a97c8c7eeb2724478972096f
ms.lasthandoff: 02/22/2017

---
# <a name="evaluating-a-watch-window-expression"></a>Avaliar uma expressão de janela Inspeção
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão do CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Quando a execução será interrompida, o Visual Studio chama o mecanismo de depuração (DE) para determinar o valor atual de cada expressão em sua lista de observação. O DE avalia cada expressão usando um avaliador de expressão (EE) e o Visual Studio exibe seu valor na **inspeção** janela.  
  
 Aqui está uma visão geral de como uma expressão de lista de observação é avaliada:  
  
1.  O Visual Studio chama o DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obter um contexto de expressão que pode ser usado para avaliar expressões.  
  
2.  Para cada expressão na lista de monitoramento, o Visual Studio chama [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) para converter o texto da expressão em uma expressão analisada.  
  
3.  `IDebugExpressionContext2::ParseText`chamadas [analisar](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) fazer o trabalho real de analisar o texto e produzir uma [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objeto.  
  
4.  `IDebugExpressionContext2::ParseText`cria um [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objeto e coloca o `IDebugParsedExpression` objeto nele. Esse,`DebugExpression2` objeto é retornado para o Visual Studio.  
  
5.  Chamadas do Visual Studio [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) para avaliar a expressão analisada.  
  
6.  `IDebugExpression2::EvaluateSync`passa a chamada para [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) para fazer a avaliação real e produzir uma [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto que é retornado para o Visual Studio.  
  
7.  Chamadas do Visual Studio [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) para obter o valor da expressão que é exibido na lista de monitoramento.  
  
## <a name="parse-then-evaluate"></a>Analisar e avaliar  
 Como analisar uma expressão complexa pode demorar muito mais do que avaliá-lo, o processo de avaliação de uma expressão é dividido em duas etapas: 1) analisar a expressão e 2) avaliar a expressão analisada. Dessa forma, a avaliação pode acontecer várias vezes, mas a expressão precisa ser analisado apenas uma vez. A expressão analisada intermediária é retornada de EE em um [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objeto que por sua vez é encapsulado e retornado de como um [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objeto. O `IDebugExpression` objeto adia a avaliação de todos os `IDebugParsedExpression` objeto.  
  
> [!NOTE]
>  Não é necessário para um EE aderir a esse processo de duas etapas, mesmo que o Visual Studio faz isso; o EE pode analisar e avaliar na mesma etapa quando [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) é chamado (Isso é como o exemplo MyCEE funciona, por exemplo). Se seu idioma pode formar expressões complexas, convém separar a etapa de análise da etapa de avaliação. Isso pode aumentar o desempenho no depurador do Visual Studio quando muitas expressões de inspeção sejam mostrados.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Implementação de exemplo de avaliação de expressão](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 Usa o exemplo MyCEE para percorrer o processo de avaliação de expressão.  
  
 [Avaliar uma expressão de inspeção](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 Explica o que acontece após a análise de uma expressão com êxito.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Contexto de avaliação](../../extensibility/debugger/evaluation-context.md)  
 Fornece os argumentos que são passados quando o mecanismo de depuração (DE) chama o avaliador de expressão (EE).  
  
## <a name="see-also"></a>Consulte também  
 [Escrevendo um avaliador de expressão de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
