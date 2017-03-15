---
title: Alterar o valor de um Local | Documentos do Microsoft
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
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
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
ms.openlocfilehash: e53ad9613e91db64f30f1e17eafe96ede9582125
ms.lasthandoff: 02/22/2017

---
# <a name="changing-the-value-of-a-local"></a>Alterar o valor de um Local
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão do CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Quando um novo valor é digitado no campo de valor de **locais** janela, o pacote de depuração passa a cadeia de caracteres, como foi digitado para o avaliador de expressão (EE). O EE avalia essa cadeia de caracteres, que pode conter um valor simples ou uma expressão e armazena o valor resultante no local associado.  
  
 Esta é uma visão geral do processo de alteração do valor de um local:  
  
1.  Depois que o usuário inserir o novo valor, o Visual Studio chama [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) sobre o [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto associado ao local.  
  
2.  `IDebugProperty2::SetValueAsString`executa as seguintes tarefas:  
  
    1.  Avalia a cadeia de caracteres para produzir um valor.  
  
    2.  Associa associado [IDebugField](../../extensibility/debugger/reference/idebugfield.md) objeto para obter um [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objeto.  
  
    3.  Converte o valor em uma série de bytes.  
  
    4.  Chamadas [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) para colocar os bytes do valor na memória para o programa que está sendo depurado possa acessá-los.  
  
3.  O Visual Studio atualiza o **locais** exibir (consulte [exibindo locais](../../extensibility/debugger/displaying-locals.md) para obter detalhes).  
  
 Esse procedimento também é usado para alterar o valor de uma variável no **inspeção** janela exceto que é o `IDebugProperty2` objeto associado com o valor do local que é usado em vez do `IDebugProperty2` objeto associado com o próprio local.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Exemplo de implementação de valores de variáveis](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 Usa o exemplo MyCEE para percorrer o processo de alteração de valores.  
  
## <a name="see-also"></a>Consulte também  
 [Escrevendo um avaliador de expressão de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Exibir locais](../../extensibility/debugger/displaying-locals.md)
