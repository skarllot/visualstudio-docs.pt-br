---
title: "Implementando um avaliador de expressão | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
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
ms.openlocfilehash: e73ad4f5cb57bfb585bb5f82a3cb650216727ac8
ms.lasthandoff: 02/22/2017

---
# <a name="implementing-an-expression-evaluator"></a>Implementando um avaliador de expressão
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão do CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Avaliar uma expressão é uma interação complexa entre o mecanismo de depuração (DE), o provedor de símbolo (SP), o objeto de fichário e o avaliador de expressão (EE) em si. Esses quatro componentes são conectados por interfaces que são implementadas por um componente e consumidos por outro.  
  
 O EE usa uma expressão de na forma de uma cadeia de caracteres e analisa ou avalia. O EE implementa as seguintes interfaces são consumidas por DE:  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
 O EE chama o objeto de fichário, fornecido pelo DE, para obter o valor de símbolos e objetos. O EE consome as seguintes interfaces são implementadas por DE:  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
-   [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
-   [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
-   [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
-   [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
-   [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
 Implementa o EE [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2`fornece o mecanismo para descrever o resultado de uma avaliação de expressão, como uma variável local, um primitivo ou um objeto, para o Visual Studio, que exibe as informações apropriadas de **locais**, **inspeção**, ou **imediato** janela.  
  
 O SP é fornecido para o EE DE quando ele pede informações. O SP implementa as interfaces que descrevem endereços e campos, como as seguintes interfaces e seus derivados:  
  
-   [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
 O EE consome todas essas interfaces.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Estratégia de implementação do avaliador de expressão](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Define um processo de três etapas para a estratégia de implementação de (EE) do avaliador de expressão.  
  
## <a name="see-also"></a>Consulte também  
 [Escrevendo um avaliador de expressão de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
