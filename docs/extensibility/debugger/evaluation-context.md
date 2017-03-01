---
title: "Contexto de avaliação | Documentos do Microsoft"
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
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
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
ms.openlocfilehash: 666fa1d2e6c893b50c9dd84986e139a9d6091e4e
ms.lasthandoff: 02/22/2017

---
# <a name="evaluation-context"></a>Contexto de avaliação
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão do CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Quando o mecanismo de depuração (DE) chama o avaliador de expressão (EE), três argumentos passados para [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) determinar o contexto para localizar e avaliar os símbolos, conforme mostrado na tabela a seguir.  
  
## <a name="arguments"></a>Arguments  
  
|Argumento|Descrição|  
|--------------|-----------------|  
|`pSymbolProvider`|Um [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) interface que especifica o manipulador de símbolo (SH) a ser usado para identificar o símbolo.|  
|`pAddress`|Um [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) interface que especifica o ponto atual de execução. Isso pode ser usado para localizar o método que contém o código que está sendo executado.|  
|`pBinder`|Um [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) interface que pode ser usado para localizar o valor e o tipo de um símbolo recebe seu nome.|  
  
 `IDebugParsedExpression::EvaluateSync`Retorna um [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface que representa o valor resultante e seu tipo.  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces do avaliador de expressão de chave](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [Exibir locais](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
