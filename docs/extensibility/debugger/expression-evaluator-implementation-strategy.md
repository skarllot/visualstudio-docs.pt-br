---
title: "Estratégia de implementação do avaliador de expressão | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
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
ms.openlocfilehash: 3953f79922d671744fa359a07eaebb22772e1ee3
ms.lasthandoff: 02/22/2017

---
# <a name="expression-evaluator-implementation-strategy"></a>Estratégia de implementação do avaliador de expressão
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão do CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Uma abordagem para criar rapidamente um avaliador de expressão (EE) é primeiro implementar o código mínimo necessário para exibir as variáveis locais no **locais** janela. É útil observar que cada linha de **locais** janela exibe o nome, tipo e valor de uma variável local e que todos os três são representados por um [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto. O nome, tipo e valor de uma variável local podem ser obtidos um `IDebugProperty2` objeto chamando seu [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) método. Para obter mais informações sobre como exibir as variáveis locais no **locais** janela, consulte [exibindo locais](../../extensibility/debugger/displaying-locals.md).  
  
## <a name="discussion"></a>Discussão  
 Uma sequência de implementação possível começa com a implementação [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). O [analisar](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) e [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) métodos precisam ser implementados para exibir locais. Chamando `IDebugExpressionEvaluator::GetMethodProperty` retorna um `IDebugProperty2` objeto que representa um método: ou seja, um [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) objeto. Métodos propriamente ditos não são exibidos na **locais** janela.  
  
 O [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) método deve ser implementado em seguida. O mecanismo de depuração (DE) chama esse método para obter uma lista de argumentos e variáveis locais, passando `IDebugProperty2::EnumChildren` um `guidFilter` argumento de `guidFilterLocalsPlusArgs`. `IDebugProperty2::EnumChildren`chamadas [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) e [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), combinando os resultados em uma enumeração único. Consulte [exibindo locais](../../extensibility/debugger/displaying-locals.md) para obter mais detalhes.  
  
## <a name="see-also"></a>Consulte também  
 [Implementando um avaliador de expressão](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Exibir locais](../../extensibility/debugger/displaying-locals.md)
