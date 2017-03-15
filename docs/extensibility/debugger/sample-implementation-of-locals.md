---
title: "Exemplo de implementação de locais | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
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
ms.openlocfilehash: f89ecd60e35b4613e06a864c588e4a2ed90b2c35
ms.lasthandoff: 02/22/2017

---
# <a name="sample-implementation-of-locals"></a>Implementação de exemplo de locais
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão do CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Aqui está uma visão geral de como o Visual Studio obtém os locais para um método do avaliador de expressão (EE):  
  
1.  O Visual Studio chama o mecanismo de depuração (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) para obter um [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto que representa todas as propriedades do quadro de pilha, incluindo os locais.  
  
2.  `IDebugStackFrame2::GetDebugProperty`chamadas [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) para obter um objeto que descreve o método no qual o ponto de interrupção ocorreu. O DE fornece um provedor de símbolo ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), um endereço ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) e um fichário ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).  
  
3.  `IDebugExpressionEvaluator::GetMethodProperty`chamadas [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) com fornecido `IDebugAddress` objeto para obter um [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) que representa o método que contém o endereço especificado.  
  
4.  O `IDebugContainerField` interface é consultada para o [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) interface. É essa interface que fornece acesso a locais do método.  
  
5.  `IDebugExpressionEvaluator::GetMethodProperty`cria uma instância de uma classe (chamado `CFieldProperty` no exemplo) que implementa o `IDebugProperty2` interface para representar locais do método. O `IDebugMethodField` objeto é colocado na `CFieldProperty` objeto junto com o `IDebugSymbolProvider`, `IDebugAddress` e `IDebugBinder` objetos.  
  
6.  Quando o `CFieldProperty` objeto é inicializado, [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) é chamado a `IDebugMethodField` objeto para obter um [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) estrutura que contém todas as informações de exibição sobre o próprio método.  
  
7.  `IDebugExpressionEvaluator::GetMethodProperty`Retorna o `CFieldProperty` objeto como uma `IDebugProperty2` objeto.  
  
8.  Chamadas do Visual Studio [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) em retornado `IDebugProperty2` objeto com o filtro `guidFilterLocalsPlusArgs`. Isso retorna um [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objeto que contém os locais do método. Essa enumeração é preenchida por chamadas para [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) e [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).  
  
9. Chamadas do Visual Studio [próximo](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) para obter um [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) estrutura para cada local. Essa estrutura contém um ponteiro para um `IDebugProperty2` interface para um local.  
  
10. Chamadas do Visual Studio [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) para cada local obter o nome, valor e tipo de local. Essas são as informações exibidas de **locais** janela.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Implementando GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 Descreve a implementação de [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).  
  
 [Enumerando locais](../../extensibility/debugger/enumerating-locals.md)  
 Descreve como o mecanismo de depuração (DE) faz uma chamada para enumerar os argumentos ou variáveis locais.  
  
 [Obtendo propriedades locais](../../extensibility/debugger/getting-local-properties.md)  
 Descreve como o DE faz uma chamada para obter o nome, tipo e valor de um ou mais locais.  
  
 [Obtendo valores de Local](../../extensibility/debugger/getting-local-values.md)  
 Discute como obter o valor do local, que exige que os serviços de um objeto de fichário fornecida pelo contexto de avaliação.  
  
 [Avaliar locais](../../extensibility/debugger/evaluating-locals.md)  
 Explica como os locais são avaliados.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Contexto de avaliação](../../extensibility/debugger/evaluation-context.md)  
 Fornece os argumentos que são passados quando o DE chama o avaliador de expressão (EE).  
  
 [Exemplo de MyCEE](http://msdn.microsoft.com/en-us/624a018b-9179-402f-9d48-3aec87b48f4f)  
 Demonstra uma abordagem de implementação para a criação de um avaliador de expressão para o idioma MyC.  
  
## <a name="see-also"></a>Consulte também  
 [Exibir locais](../../extensibility/debugger/displaying-locals.md)
