---
title: "Interfaces de avaliação da expressão | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
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
ms.openlocfilehash: 05c4bb028a2a99f77c12a1ce02028f6a6b633b0a
ms.lasthandoff: 02/22/2017

---
# <a name="expression-evaluation-interfaces"></a>Interfaces de avaliação de expressão
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão do CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 A seguir estão as Interfaces de avaliação de expressão para o [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] SDK de depuração.  
  
## <a name="discussion"></a>Discussão  
 Essas interfaces são usadas para avaliar expressões em uma pilha de chamadas durante o modo de interrupção. Eles são implementados para apenas os avaliadores de expressão de tempo de execução do common language (EE).  
  
 Cada interface na tabela mostra o componente que pode implementar na lista a seguir:  
  
-   Debug Engine (DE)  
  
-   Avaliador de expressão (EE)  
  
-   Visual Studio (VS)  
  
|Interface|Implementado por|Descrição|  
|---------------|--------------------|-----------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Representa um alias numérico para uma variável.|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Representa um alias numérico para uma variável e permite que um avaliador de expressão (EE) para obter o domínio de aplicativo para o alias.|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Representa um objeto de matriz.|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Representa um objeto de matriz gerenciada e permite que um avaliador de expressão (EE) para determinar o índice de base (limites inferiores) para a matriz.|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Representa um fichário que associa os símbolos para endereços reais na memória de depuração.|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Mesmo que o [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interface mas fornece acesso aos tipos, aliases e os visualizadores personalizados.|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Representa o avaliador de expressão.|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Representa uma versão aprimorada de um avaliador de expressão (EE).|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Representa um avaliador de expressão (EE) com uma árvore de analisador aprimorada.|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Representa uma função.|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Representa uma função e aprimora o [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interface.|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Permite que um avaliador de expressão (EE) exibir uma mensagem na janela de saída do depurador.|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Representa um objeto de código gerenciado.|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Interface base que representa qualquer símbolo associado a um endereço de memória.|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Mesmo que o [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface mas fornece acesso a informações adicionais.|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Representa uma expressão analisada pronta para ser avaliada.|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Representa um ponteiro.|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Representa um ponteiro em uma árvore de análise e estende o **IDebugPointerObject** interface.|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Fornece a capacidade de modificar o valor de um tipo por meio de um visualizador de tipo.|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Fornece acesso aos visualizadores personalizados e visualizadores de tipo.|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Fornece a capacidade de criar um [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) objeto.|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Representa uma coleção de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objetos.|  
  
## <a name="see-also"></a>Consulte também  
 [Referência da API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Escrevendo um avaliador de expressão de CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualizador de tipo e o visualizador personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
