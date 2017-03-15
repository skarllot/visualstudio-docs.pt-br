---
title: "CA2224: substituir igualdades em igualdades de operador de sobrecarga | Microsoft Docs"
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
  - "CA2224"
  - "OverrideEqualsOnOverloadingOperatorEquals"
  - "OverrideEqualsOnOverridingOperatorEquals"
helpviewer_keywords: 
  - "CA2224"
  - "OverrideEqualsOnOverloadingOperatorEquals"
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2224: substituir igualdades em igualdades de operador de sobrecarga
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|  
|CheckId|CA2224|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Um tipo público implementa o operador de igualdade, mas não substitui <xref:System.Object.Equals%2A?displayProperty=fullName>.  
  
## Descrição da Regra  
 O operador de igualdade deve ser sintaticamente uma maneira conveniente de acessar a funcionalidade do método de <xref:System.Object.Equals%2A> .  Se você implementa o operador de igualdade, sua lógica deve ser idêntica à de <xref:System.Object.Equals%2A>.  
  
 O compilador C\# emite um aviso se seu código viola a regra.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, é necessário descartar a implementação do operador de igualdade, ou a substituição <xref:System.Object.Equals%2A> e fazer com que os dois métodos retorna os mesmos valores.  Se o operador de igualdade não apresenta o comportamento inconsistente, você poderá corrigir a violação fornecendo uma implementação de <xref:System.Object.Equals%2A> que chama o método de <xref:System.Object.Equals%2A> na classe base.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso dessa regra se o operador de igualdade retorna o mesmo valor que a implementação herdada de <xref:System.Object.Equals%2A>.  A seção de exemplo inclui um tipo que pode suprimir com segurança um aviso desta regra.  
  
## Exemplos de definições inconsistentes de igualdade  
  
### Descrição  
 O exemplo a seguir mostra um tipo com definições inconsistentes de igualdade.  `BadPoint` alterar o significado de igualdade fornecendo uma implementação personalizada do operador de igualdade, mas não substitui <xref:System.Object.Equals%2A> de forma que se com comportamento da mesma forma.  
  
### Código  
 [!code-cs[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]  
  
## Exemplo  
 O código a seguir testa o comportamento de `BadPoint`.  
  
 [!code-cs[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]  
  
 O exemplo produz a seguinte saída.  
  
  **a \= \(\[0\] 1,1\) e b \= \(\[1\] 2,2\) é igual?  Não**  
**um \=\= b?  Não**  
**a1 e a são iguais?  Sim**  
**a1 \=\= a?  Sim**  
**b e bcopy são iguais?  Não**  
**\=\= de b bcopy?  Sim**    
## Exemplo  
 O exemplo a seguir mostra um tipo que viola tecnicamente essa regra, mas não se comporta de maneira inconsistente.  
  
 [!code-cs[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]  
  
## Exemplo  
 O código a seguir testa o comportamento de `GoodPoint`.  
  
 [!code-cs[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]  
  
 O exemplo produz a seguinte saída.  
  
  **a \= \(1,1\) e \(b \= 2,2\) é igual?  Não**  
**um \=\= b?  Não**  
**a1 e a são iguais?  Sim**  
**a1 \=\= a?  Sim**  
**b e bcopy são iguais?  Sim**  
**\=\= de b bcopy?  Sim**    
## Exemplo da classe  
  
### Descrição  
 O exemplo a seguir mostra uma classe \(tipo de referência\) que viola esta regra.  
  
### Código  
 [!code-cs[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]  
  
## Exemplo  
 O exemplo a seguir corrige a violação substituindo <xref:System.Object.Equals%2A?displayProperty=fullName>.  
  
 [!code-cs[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]  
  
## Exemplo de estrutura  
  
### Descrição  
 O exemplo a seguir mostra uma estrutura \(tipo de valor\) que viola esta regra.  
  
### Código  
 [!code-cs[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]  
  
## Exemplo  
 O exemplo a seguir corrige a violação substituindo <xref:System.ValueType.Equals%2A?displayProperty=fullName>.  
  
 [!code-cs[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]  
  
## Regras Relacionadas  
 [CA1046: não sobrecarregar igualdades de operador em tipos de referência](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: as sobrecargas do operador têm alternativas nomeadas](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)  
  
 [CA2226: os operadores devem ter sobrecargas simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2218: substituir GetHashCode em igualdades de substituição](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231: sobrecarregar igualdades de operador em ValueType.Equals substituídos](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)