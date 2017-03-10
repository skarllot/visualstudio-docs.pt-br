---
title: "CA2218: substituir GetHashCode em igualdades de substitui&#231;&#227;o | Microsoft Docs"
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
  - "CA2218"
  - "OverrideGetHashCodeOnOverridingEquals"
helpviewer_keywords: 
  - "CA2218"
  - "OverrideGetHashCodeOnOverridingEquals"
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2218: substituir GetHashCode em igualdades de substitui&#231;&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideGetHashCodeOnOverridingEquals|  
|CheckId|CA2218|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 As substituições públicas <xref:System.Object.Equals%2A?displayProperty=fullName> de um tipo mas não substitui <xref:System.Object.GetHashCode%2A?displayProperty=fullName>.  
  
## Descrição da Regra  
 <xref:System.Object.GetHashCode%2A> retorna um valor, com base na instância atual, que é adequada para algoritmos de hash e estruturas de dados como uma tabela de hash.  Dois objetos que têm o mesmo tipo e são iguais devem retornar o mesmo código hash para garantir que as instâncias dos tipos funcionem corretamente:  
  
-   <xref:System.Collections.HashTable?displayProperty=fullName>  
  
-   <xref:System.Collections.SortedList?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Dictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.SortDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.SortList?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.HybredDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>  
  
-   Tipos que implementam <xref:System.Collections.Generic.IEqualityComparer?displayProperty=fullName>  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, forneça uma implementação de <xref:System.Object.GetHashCode%2A>.  Para um par de objetos do mesmo tipo, você deve assegurar que a implementação retorna o mesmo valor se sua implementação de <xref:System.Object.Equals%2A> retorna `true` para o par.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo da classe  
  
### Descrição  
 O exemplo a seguir mostra uma classe \(tipo de referência\) que viola esta regra.  
  
### Código  
 [!code-cs[FxCop.Usage.GetHashCodeErrorClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_1.cs)]  
  
### Comentários  
 O exemplo a seguir corrige a violação substituindo <xref:System.Object.GetHashCode>.  
  
### Código  
 [!CODE [FxCop.Usage.GetHashCodeFixedClass#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeFixedClass#1)]  
  
## Exemplo de estrutura  
  
### Descrição  
 O exemplo a seguir mostra uma estrutura \(tipo de valor\) que viola esta regra.  
  
### Código  
 [!code-cs[FxCop.Usage.GetHashCodeErrorStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_2.cs)]  
  
### Comentários  
 O exemplo a seguir corrige a violação substituindo <xref:System.Object.GetHashCode>.  
  
### Código  
 [!code-cs[FxCop.Usage.GetHashCodeFixedStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_3.cs)]  
  
## Regras Relacionadas  
 [CA1046: não sobrecarregar igualdades de operador em tipos de referência](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: as sobrecargas do operador têm alternativas nomeadas](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)  
  
 [CA2226: os operadores devem ter sobrecargas simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224: substituir igualdades em igualdades de operador de sobrecarga](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2231: sobrecarregar igualdades de operador em ValueType.Equals substituídos](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)  
  
## Consulte também  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 <xref:System.Object.GetHashCode%2A?displayProperty=fullName>   
 <xref:System.Collections.HashTable?displayProperty=fullName>   
 [Operadores de igualdade](../Topic/Equality%20Operators.md)