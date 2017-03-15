---
title: "Avaliar expressões | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
caps.latest.revision: 11
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
ms.openlocfilehash: 09e24b896dd5d4fcca380718c0b9a80d11cf3301
ms.lasthandoff: 02/22/2017

---
# <a name="evaluating-expressions"></a>Avaliando expressões
As expressões são criadas de cadeias de caracteres passadas do Autos, inspeção, QuickWatch ou windows imediatas. Quando uma expressão é avaliada, ele gera uma cadeia de caracteres imprimível que contém o nome e o tipo de variável ou argumento e seu valor. Essa cadeia de caracteres é exibida na janela do IDE correspondente.  
  
## <a name="implementation"></a>Implementação  
 Expressões são avaliadas quando um programa foi interrompido no ponto de interrupção. A expressão em si é representada por um [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface, que representa uma expressão analisada está pronta para vinculação e avaliação dentro do contexto de avaliação da expressão especificada. O quadro de pilha determina o contexto de avaliação de expressão, que fornece o mecanismo de depuração (DE) Implementando a [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface.  
  
 Dada uma cadeia de caracteres de usuário e uma [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface, um mecanismo de depuração (DE) pode obter um [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface, passando a cadeia de caracteres do usuário para o [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método. A interface IDebugExpression2 retornada contém a expressão analisada pronta para avaliação.  
  
 Com o `IDebugExpression2` interface, o DE pode obter o valor da expressão por meio da avaliação da expressão síncronas ou assíncronas, usando [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Esse valor, junto com o nome e o tipo da variável ou argumento, é enviado ao IDE para exibição. O valor, nome e tipo são representados por um [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface.  
  
 Para habilitar a avaliação da expressão, um DE deve implementar o [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) e [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaces. Avaliação síncrona e assíncrona requerem a implementação do [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [Quadros de pilha](../../extensibility/debugger/stack-frames.md)   
 [Contexto de avaliação de expressão](../../extensibility/debugger/expression-evaluation-context.md)   
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)
