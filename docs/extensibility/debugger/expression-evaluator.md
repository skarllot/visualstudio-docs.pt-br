---
title: "Avaliador de expressão | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: 19
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
ms.openlocfilehash: c8f30e8231a63ee198b264960bcc41bf7ae54fc3
ms.lasthandoff: 02/22/2017

---
# <a name="expression-evaluator"></a>Avaliador de expressão
Avaliadores de expressão (EE) examinam a sintaxe de uma linguagem para analisar e avaliar as variáveis e expressões no tempo de execução, permitindo que eles sejam exibidos pelo usuário quando o IDE está no modo de interrupção.  
  
## <a name="using-expression-evaluators"></a>Usando os avaliadores de expressão  
 As expressões são criadas usando o [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método, da seguinte maneira:  
  
1.  O mecanismo de depuração (DE) implementa a [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface.  
  
2.  O pacote de depuração obtém um `IDebugExpressionContext2` do objeto de um [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interface e, em seguida, chama o `IDebugStackFrame2::ParseText` método para obter um [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objeto.  
  
3.  As chamadas de pacote de depuração a [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) método ou o [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) método para obter o valor da expressão. `IDebugExpression2::EvaluateAsync`é chamado na janela de comando/imediato. Todos os outros componentes de interface do usuário chamar `IDebugExpression2::EvaluateSync`.  
  
4.  O resultado da avaliação da expressão é um [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto, que contém o nome, o tipo e o valor do resultado da avaliação de expressão.  
  
 Durante a avaliação da expressão, o EE requer informações do componente do provedor de símbolo. O provedor de símbolo fornece a informação simbólica usada para identificar e compreender a expressão analisada.  
  
 Quando a avaliação da expressão assíncrona for concluída, um evento assíncrono é enviado por DE por meio do Gerenciador de sessão de depuração (SDM) para notificar o IDE que a avaliação da expressão está concluída. Quando a avaliação da expressão síncrona for concluída, o resultado da avaliação é retornado da chamada para o `IDebugExpression2::EvaluateSync` método.  
  
## <a name="implementation-notes"></a>Notas de implementação  
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mecanismos de depuração esperam para se comunicar com o avaliador de expressão usando as interfaces do Common Language Runtime (CLR). Como resultado, um avaliador de expressão que funciona com o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mecanismos de depuração devem oferecer suporte o CLR (uma lista completa de CLR de todas as interfaces de depuração pode ser encontrada em debugref.doc, que é parte do [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]).  
  
## <a name="see-also"></a>Consulte também  
 [Componentes do depurador](../../extensibility/debugger/debugger-components.md)
