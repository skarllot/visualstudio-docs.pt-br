---
title: IDebugBinder | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
caps.latest.revision: 16
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
ms.openlocfilehash: 28872d108bf55dab5b27a2acecfec90591405221
ms.lasthandoff: 02/22/2017

---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão do CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Essa interface associa um campo de símbolo, normalmente retornado pelo provedor de símbolo, em um contexto de memória ou um objeto que contém o valor atual do símbolo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugBinder : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Esta interface dá suporte à avaliação de expressão e deve ser implementada pelo mecanismo de depuração (DE).  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface é usada no processo de avaliação de expressão e normalmente é usada na implementação do [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) e [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugBinder`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Ligação](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Obtém o contexto de memória ou um objeto que contém o valor atual do símbolo.|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Determina o tipo de tempo de execução de um objeto.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Converte um endereço de memória ou local do objeto em um contexto de memória.|  
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Obtém um [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objeto usado para criar parâmetros de função.|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Obtém o tipo exato de uma variável.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface retorna objetos que são usados pelo avaliador de expressão em analisar árvores. O avaliador de expressão analisa uma expressão usando o provedor de símbolo para converter os símbolos na expressão em instâncias de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), que descrevem cada símbolo em termos de seu tipo e o local no código-fonte. O [ligar](../../../extensibility/debugger/reference/idebugbinder-bind.md) método converte `IDebugField` objetos [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objetos que se conectar ou associar um símbolo de tipo para um valor real na memória. Essas `IDebugObject` objetos são armazenados em uma árvore de análise para avaliação posterior.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de avaliação de expressão](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
