---
title: "CA1046: n&#227;o sobrecarregar igualdades de operador em tipos de refer&#234;ncia | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotOverloadOperatorEqualsOnReferenceTypes"
  - "CA1046"
helpviewer_keywords: 
  - "CA1046"
  - "DoNotOverloadOperatorEqualsOnReferenceTypes"
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1046: n&#227;o sobrecarregar igualdades de operador em tipos de refer&#234;ncia
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|  
|CheckId|CA1046|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um público ou um tipo público aninhado de referência sobrecarregam o operador de igualdade.  
  
## Descrição da Regra  
 Para tipos de referência, a implementação padrão do operador de igualdade está quase sempre correta.  Por padrão, duas referências são iguais apenas se apontam para o mesmo objeto.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, remova a implementação do operador de igualdade.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso desta regra quando o tipo de referência se comporta como um tipo de valor interno.  Se for significativo fazer a adição ou subtração em instâncias do tipo, provavelmente está correto implementar o operador de igualdade e suprimir a violação.  
  
## Exemplo  
 O exemplo a seguir demonstra o comportamento padrão durante a comparação de duas referências.  
  
 [!code-cs[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]  
  
## Exemplo  
 O aplicativo seguir compara referências.  
  
 [!code-cs[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]  
  
 O exemplo produz a seguinte saída.  
  
  **a nova \(\= 2,2\) e b \= novo \(2,2\) é igual?  Não**  
**c e a são iguais?  Sim**  
**b e a são \=\=?  Não**  
**c e a são \=\=?  Sim**    
## Regras Relacionadas  
 [CA1013: sobrecarregar igualdades de operador em add e subtract de sobrecarga](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)  
  
## Consulte também  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [Operadores de igualdade](../Topic/Equality%20Operators.md)