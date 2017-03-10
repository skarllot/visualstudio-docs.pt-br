---
title: "CA2231: sobrecarregar igualdades de operador em ValueType.Equals substitu&#237;dos | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OverloadOperatorEqualsOnOverridingValueTypeEquals"
  - "CA2231"
  - "OverrideOperatorEqualsOnOverridingValueTypeEquals"
helpviewer_keywords: 
  - "CA2231"
  - "OverloadOperatorEqualsOnOverridingValueTypeEquals"
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2231: sobrecarregar igualdades de operador em ValueType.Equals substitu&#237;dos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverloadOperatorEqualsOnOverridingValueTypeEquals|  
|CheckId|CA2231|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Um tipo de valor substitui <xref:System.Object.Equals%2A?displayProperty=fullName> mas não implementa o operador de igualdade.  
  
## Descrição da Regra  
 Na maioria das linguagens de programação não há nenhuma implementação padrão do operador de igualdade \(\=\=\) para tipos de valor.  Se a linguagem de programação suporte sobrecargas do operador, você deve considerar implementar o operador de igualdade.  O comportamento deve ser idêntico ao de <xref:System.Object.Equals%2A>.  
  
 Você não pode usar o operador de igualdade padrão em uma implementação sobrecarregada do operador de igualdade.  Isso causará um estouro de pilha.  Para implementar o operador de igualdade, use o método de Object.Equals em sua implementação.  Por exemplo:  
  
```vb  
If (Object.ReferenceEquals(left, Nothing)) Then  
    Return Object.ReferenceEquals(right, Nothing)  
Else  
    Return left.Equals(right)  
End If  
```  
  
```c#  
if (Object.ReferenceEquals(left, null))   
    return Object.ReferenceEquals(right, null);  
return left.Equals(right);  
```  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, implemente o operador de igualdade.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso desta regra; no entanto, recomendamos que você forneça o operador de igualdade se possível.  
  
## Exemplo  
 O exemplo a seguir define um tipo que viola esta regra.  
  
 [!CODE [FxCop.Usage.EqualsGetHashCode#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.EqualsGetHashCode#1)]  
  
## Regras Relacionadas  
 [CA1046: não sobrecarregar igualdades de operador em tipos de referência](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: as sobrecargas do operador têm alternativas nomeadas](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)  
  
 [CA2226: os operadores devem ter sobrecargas simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224: substituir igualdades em igualdades de operador de sobrecarga](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218: substituir GetHashCode em igualdades de substituição](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
## Consulte também  
 <xref:System.Object.Equals%2A?displayProperty=fullName>