---
title: "Contexto de avaliação da expressão | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
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
ms.openlocfilehash: 470b2140e3eb8fb358b8e509e88f12c97c14f25e
ms.lasthandoff: 02/22/2017

---
# <a name="expression-evaluation-context"></a>Contexto de avaliação de expressão
Em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração, uma **contexto de avaliação de expressão**:  
  
-   Representa um contexto de avaliação de expressão. Geralmente, um contexto de avaliação corresponde ao escopo léxico no qual avaliar variáveis, parâmetros, funções e métodos. Por exemplo, um contexto de avaliação de expressão associado a um quadro de pilha fornecerá o contexto para avaliar as variáveis locais, parâmetros de método e membros de classe (se aplicável).  
  
-   Ocorre quando um programa foi interrompido no ponto de interrupção. A expressão em si é uma estrutura de dados que representa uma expressão analisada está pronta para vinculação e avaliar dentro do contexto especificado.  
  
     Mais especificamente, as expressões são criadas usando o [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método. Quando uma expressão é avaliada, ele gera uma cadeia de caracteres imprimível contendo o nome e o tipo de variável ou argumento e seu valor. Essa cadeia de caracteres é exibida na janela Watch ou na janela locais do IDE.  
  
     Dado um `BSTR` e uma [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface, um mecanismo de depuração (DE) pode criar um [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface analisando uma expressão. Dado um `IDebugExpression2` interface, o DE pode obter um valor por meio da avaliação de expressão síncrona ou assíncrona. Esse valor, junto com o nome e o tipo da variável ou argumento, é enviado ao IDE para exibição.  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de avaliação de expressão](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)
