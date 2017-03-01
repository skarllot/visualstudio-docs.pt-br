---
title: "Escrevendo um avaliador de expressão de tempo de execução linguagem comum | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
caps.latest.revision: 23
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
ms.openlocfilehash: edbd35e5bf636b7d75ca1631f8c4bc19481da29a
ms.lasthandoff: 02/22/2017

---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Escrevendo um avaliador de expressão de tempo de execução linguagem comum
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão do CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 O avaliador de expressão (EE) é a parte de um mecanismo de depuração (DE) que lida com a sintaxe e semântica da linguagem de programação que produziu o código que está sendo depurado. Expressões devem ser avaliadas no contexto de uma linguagem de programação. Por exemplo, em alguns idiomas, a expressão "A + B" significa "a soma de A e b." Em outras linguagens, a mesma expressão pode significar "A ou B." Portanto, um separado EE deve ser escrito para cada linguagem de programação que gera o código de objeto a ser depurado no IDE do Visual Studio.  
  
 Alguns aspectos do pacote de depuração do Visual Studio devem interpretar o código no contexto da linguagem de programação. Por exemplo, quando a execução é interrompida no ponto de interrupção, as expressões que o usuário tiver digitado em um **inspeção** janela deve ser avaliada e exibida. Além disso, o usuário pode alterar o valor de uma variável local digitando uma expressão em uma **inspeção** janela ou para o **imediato** janela.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Common Language Runtime e avaliação de expressão](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 Explica que quando você está integrando proprietária linguagem de programação em Visual Studio IDE, escrever um EE capaz de avaliar expressões dentro do contexto do proprietário idioma permite que você compilar para um Microsoft intermediate language (MSIL) sem escrever um mecanismo de depuração.  
  
 [Arquitetura do avaliador de expressão](../../extensibility/debugger/expression-evaluator-architecture.md)  
 Discute como implementar as interfaces EE necessárias e chamar o provedor de símbolo de tempo de execução de linguagem comum (SP) e interfaces de fichário.  
  
 [Registrando um avaliador de expressão](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 Observa que o EE deve ser registrado como uma fábrica de classes com o common language runtime e os ambientes de tempo de execução do Visual Studio.  
  
 [Implementando um avaliador de expressão](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 Descreve como o processo de avaliação de uma expressão inclui o mecanismo de depuração (DE), o provedor de símbolo (SP), o objeto de fichário e o avaliador de expressão (EE).  
  
 [Exibir locais](../../extensibility/debugger/displaying-locals.md)  
 Descreve como fazer isso, quando a execução será interrompida, o pacote de depuração chama DE para obter uma lista de argumentos e variáveis locais.  
  
 [Avaliar uma expressão de janela Inspeção](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 Documenta como o pacote de depuração do Visual Studio chama DE para determinar o valor atual de cada expressão em sua lista de observação.  
  
 [Alterar o valor de um Local](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 Explica que, ao alterar o valor de um local, cada linha da janela locais tem um objeto associado que fornece o nome, o tipo e o valor atual de um local.  
  
 [Implementando os visualizadores de tipo e visualizadores personalizados](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 Explica qual interface deve ser implementado pelo qual componente para oferecer suporte a visualizadores de tipo e visualizadores personalizados.  
  
## <a name="see-also"></a>Consulte também  
 [Extensibilidade do depurador do Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
