---
title: Exibindo locais | Documentos do Microsoft
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
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
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
ms.openlocfilehash: c7d9dd203bb696358d206918cb5a11fd01ef7423
ms.lasthandoff: 02/22/2017

---
# <a name="displaying-locals"></a>Exibir locais
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão do CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Execução sempre ocorre dentro do contexto de um método, também conhecido como método de inclusão ou método atual. Quando a execução será interrompida, o Visual Studio chama o mecanismo de depuração (DE) para obter uma lista de variáveis locais e os argumentos, coletivamente chamados de locais do método. O Visual Studio exibe esses locais e seus valores a **locais** janela.  
  
 Para exibir locais, DE chama o [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) método pertencente ao EE e concede a ele um contexto de avaliação, que é, um provedor de símbolo (SP), o endereço de execução atual e um objeto de fichário. Para obter mais informações, consulte [contexto de avaliação](../../extensibility/debugger/evaluation-context.md). Se a chamada for bem-sucedida, o `IDebugExpressionEvaluator::GetMethodProperty` método retorna um [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto que representa o método que contém o endereço de execução atual.  
  
 As chamadas DE [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) para obter um [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) object, que é filtrado para retornar somente locais e enumerado para produzir uma lista de [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) estruturas. Cada estrutura contém o nome, tipo e valor de um local. O tipo e valor são armazenados como cadeias de caracteres formatadas, adequadas para exibição. O nome, tipo e valor geralmente são exibidos juntos em uma linha do **locais** janela.  
  
> [!NOTE]
>  O **QuickWatch** e **inspeção** janelas também exibem variáveis com o mesmo formato de nome, valor e tipo. No entanto, esses valores são obtidos chamando [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) em vez de `IDebugProperty2::EnumChildren`.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Implementação de exemplo de locais](../../extensibility/debugger/sample-implementation-of-locals.md)  
 Usa exemplos para percorrer o processo de implementação locais.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Contexto de avaliação](../../extensibility/debugger/evaluation-context.md)  
 Explica que, quando o mecanismo de depuração (DE) chama o avaliador de expressão (EE), ele passa três argumentos.  
  
## <a name="see-also"></a>Consulte também  
 [Escrevendo um avaliador de expressão de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
