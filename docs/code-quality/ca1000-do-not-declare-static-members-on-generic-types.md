---
title: "CA1000: n&#227;o declarar membros est&#225;ticos em tipos gen&#233;ricos | Microsoft Docs"
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
  - "CA1000"
  - "DoNotDeclareStaticMembersOnGenericTypes"
helpviewer_keywords: 
  - "CA1000"
  - "DoNotDeclareStaticMembersOnGenericTypes"
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1000: n&#227;o declarar membros est&#225;ticos em tipos gen&#233;ricos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|  
|CheckId|CA1000|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um tipo genérico externamente visível contém um membro de `static` \(`Shared` no Visual Basic\).  
  
## Descrição da Regra  
 Quando um membro de `static` de um tipo genérico é chamado, o argumento de tipo deve ser especificado para o tipo.  Quando um membro da instância que não oferece suporte a inferência é chamado, o argumento de tipo deve ser especificado para o membro.  A sintaxe para especificar o argumento de tipo nesses dois casos é diferente e ofuscada facilmente, chamadas demonstram como os seguintes:  
  
```vb  
' Shared method in a generic type.  
GenericType(Of Integer).SharedMethod()  
  
' Generic instance method that does not support inference.  
someObject.GenericMethod(Of Integer)()  
```  
  
```c#  
// Static method in a generic type.  
GenericType<int>.StaticMethod();  
  
// Generic instance method that does not support inference.  
someObject.GenericMethod<int>();  
```  
  
 Em geral, ambas as instruções anteriores devem ser evitadas de forma que o argumento de tipo não tem que ser especificado quando o membro for chamado.  Isso resulta em uma sintaxe para chamar membros em produtos genéricas que não é diferente da sintaxe para produtos não genéricas.  Para obter mais informações, consulte [CA1004: os métodos genéricos devem fornecer o parâmetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md).  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, remova o membro estático ou altere\-o para um membro da instância.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  Fornecer produtos genéricas em uma sintaxe que seja fácil de entender e em uso reduz o tempo necessário para conhecer e aumenta a taxa de adoção de novas bibliotecas.  
  
## Regras Relacionadas  
 [CA1005: evitar parâmetros excessivos em tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: as coleções devem implementar a interface genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1002: não expor listas genéricas](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006: não aninhar tipos genéricos em assinaturas de membro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: os métodos genéricos devem fornecer o parâmetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: usar instâncias do manipulador de eventos genéricos](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007: usar genéricos quando apropriado](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Consulte também  
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)