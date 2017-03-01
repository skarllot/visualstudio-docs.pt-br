---
title: "Arquitetura do avaliador de expressão | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
caps.latest.revision: 13
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
ms.openlocfilehash: 860a81cb8fd9bdb92fe563c31e78aad2508cf488
ms.lasthandoff: 02/22/2017

---
# <a name="expression-evaluator-architecture"></a>Arquitetura do avaliador de expressão
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão do CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Integrar um idioma proprietário o pacote de depuração do Visual Studio significa implementar as interfaces (EE) do avaliador de expressão necessária e chamando o provedor de símbolo de tempo de execução de linguagem comum (SP) e interfaces de fichário. Os objetos de SP e fichário, junto com o endereço de execução atual, são o contexto no qual as expressões são avaliadas. As informações de que essas interfaces produzem e consumam representam os principais conceitos da arquitetura de um EE.  
  
## <a name="overview"></a>Visão Geral  
  
### <a name="parsing-the-expression"></a>Análise da expressão  
 Quando você está depurando um programa, as expressões são avaliadas para um número de razões, mas sempre quando o programa que está sendo depurado foi interrompido no ponto de interrupção (um ponto de interrupção colocado pelo usuário ou causada por uma exceção). É neste momento quando o Visual Studio obtém um quadro de pilha, conforme representado pelo [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interface do mecanismo de depuração (DE). Em seguida, o Visual Studio chama [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obter o [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface. Essa interface representa um contexto no qual as expressões podem ser avaliadas; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) é o ponto de entrada para o processo de avaliação. Até este ponto, todas as interfaces são implementadas DE.  
  
 Quando `IDebugExpressionContext2::ParseText` é chamado, o DE instancia o EE associado com o idioma do arquivo de origem onde o ponto de interrupção ocorreu (o DE também instancia o SH neste momento). O EE é representado pelo [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) interface. Em seguida, chama o DE [analisar](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para converter a expressão (na forma de texto) em uma expressão analisada, pronto para avaliação. Essa expressão analisada é representado pelo [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) interface. Observe que a expressão é analisada normalmente e não avaliada neste momento.  
  
 O DE cria um objeto que implementa o [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface coloca o `IDebugParsedExpression` do objeto para o `IDebugExpression2` objeto e retorna o `IDebugExpression2` de objeto `IDebugExpressionContext2::ParseText`.  
  
### <a name="evaluating-the-expression"></a>Avaliação da expressão  
 O Visual Studio chama o [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para avaliar a expressão analisada. Ambos os métodos chamam [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (`IDebugExpression2::EvaluateSync` chama o método imediatamente, enquanto `IDebugExpression2::EvaluateAsync` chama o método por meio de um thread em segundo plano) para avaliar a expressão analisada e retornar um [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface que representa o valor e o tipo da expressão analisada. `IDebugParsedExpression::EvaluateSync`usa o fornecido SH, endereço e fichário para converter a expressão analisada em um valor real, representado pelo `IDebugProperty2` interface.  
  
### <a name="for-example"></a>Por exemplo  
 Depois de atingir um ponto de interrupção em um programa em execução, o usuário opta por exibir uma variável de **QuickWatch** caixa de diálogo. Essa caixa de diálogo mostra o nome da variável, seu valor e seu tipo. O usuário geralmente pode alterar o valor.  
  
 Quando o **QuickWatch** caixa de diálogo é exibida, o nome da variável que está sendo examinado é enviado como texto em [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Isso retorna um [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objeto que representa a expressão analisada, nesse caso, a variável. [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) é chamado para produzir uma `IDebugProperty2` objeto que representa o tipo e o valor da variável, bem como seu nome. É essa informação é exibida.  
  
 Se o usuário altera o valor da variável, [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) é chamado com o novo valor, que altera o valor da variável na memória para que ele será usado quando o programa continua em execução.  
  
 Consulte [exibindo locais](../../extensibility/debugger/displaying-locals.md) para obter mais detalhes sobre esse processo de exibir os valores das variáveis. Consulte [alterar o valor de um Local](../../extensibility/debugger/changing-the-value-of-a-local.md) para obter mais detalhes sobre como o valor da variável é alterado.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Contexto de avaliação](../../extensibility/debugger/evaluation-context.md)  
 Fornece os argumentos que são passados quando o DE chama o EE.  
  
 [Interfaces do avaliador de expressão de chave](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 Descreve as interfaces cruciais necessárias ao escrever um EE, junto com o contexto de avaliação.  
  
## <a name="see-also"></a>Consulte também  
 [Escrevendo um avaliador de expressão de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Exibir locais](../../extensibility/debugger/displaying-locals.md)   
 [Alterar o valor de um Local](../../extensibility/debugger/changing-the-value-of-a-local.md)
