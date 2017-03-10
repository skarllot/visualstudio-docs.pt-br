---
title: "CA1010: as cole&#231;&#245;es devem implementar a interface gen&#233;rica | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1010"
  - "CollectionsShouldImplementGenericInterface"
helpviewer_keywords: 
  - "CA1010"
  - "CollectionsShouldImplementGenericInterface"
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1010: as cole&#231;&#245;es devem implementar a interface gen&#233;rica
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CollectionsShouldImplementGenericInterface|  
|CheckId|CA1010|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um tipo externamente visível implementa a interface de <xref:System.Collections.IEnumerable?displayProperty=fullName> mas não implementa a interface de <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> , e o assembly que contém [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]de destino.  Esta regra ignora os tipos que implementam <xref:System.Collections.IDictionary?displayProperty=fullName>.  
  
## Descrição da Regra  
 Para ampliar a utilidade de uma coleção, implementar uma das interfaces genéricas da coleção.  A coleção pode ser usada para popular tipos genéricos da coleção como o seguinte:  
  
-   <xref:System.Collections.Generic.List%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, implemente uma das seguintes interfaces genéricas da coleção:  
  
-   <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.IList%601?displayProperty=fullName>  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso desta regra; no entanto, a coleção terá um uso mais limitado.  
  
## Violação de exemplo  
  
### Descrição  
 O exemplo a seguir mostra uma classe \(tipo de referência\) que deriva da classe não genérico de `CollectionBase` , que viola esta regra.  
  
### Código  
 [!code-cs[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]  
  
### Comentários  
 Para corrigir uma violação dessa violação, você deve implementar as interfaces genéricas ou alterar a classe base em um tipo que implementa as interfaces mais genéricas e não genéricas, como a classe de `Collection<T>` .  
  
## Correção pela alteração da classe base  
  
### Descrição  
 O exemplo a seguir corrige a violação alterando a classe base da coleção da classe não genérico da classe `CollectionBase` genérico de `Collection<T>` \(`Collection(Of T)` em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
### Código  
 [!code-cs[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]  
  
### Comentários  
 Alterando a classe base de uma classe já liberada é considerado uma alteração aos consumidores existentes.  
  
## Correção pela implementação da interface  
  
### Descrição  
 O exemplo a seguir corrige a violação implementando estas interfaces genéricas: `IEnumerable<T>`, `ICollection<T>`, e `IList<T>` \(`IEnumerable(Of T)`, `ICollection(Of T)`, e `IList(Of T)` em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
### Código  
 [!code-cs[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]  
  
## Regras Relacionadas  
 [CA1005: evitar parâmetros excessivos em tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1000: não declarar membros estáticos em tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: não expor listas genéricas](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006: não aninhar tipos genéricos em assinaturas de membro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: os métodos genéricos devem fornecer o parâmetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: usar instâncias do manipulador de eventos genéricos](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007: usar genéricos quando apropriado](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Consulte também  
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)