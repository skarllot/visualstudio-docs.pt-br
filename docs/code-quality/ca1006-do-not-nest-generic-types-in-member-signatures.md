---
title: "CA1006: n&#227;o aninhar tipos gen&#233;ricos em assinaturas de membro | Microsoft Docs"
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
  - "DoNotNestGenericTypesInMemberSignatures"
  - "CA1006"
helpviewer_keywords: 
  - "CA1006"
  - "DoNotNestGenericTypesInMemberSignatures"
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1006: n&#227;o aninhar tipos gen&#233;ricos em assinaturas de membro
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotNestGenericTypesInMemberSignatures|  
|CheckId|CA1006|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um membro externamente visível tem uma assinatura que contém um argumento aninhado do tipo.  
  
## Descrição da Regra  
 Um argumento aninhado classificação é um argumento do tipo que também seja um tipo genérico.  Para chamar um membro cuja assinatura contém um argumento aninhado do tipo, o usuário deve criar uma instância de um tipo genérico e passar esse tipo para o construtor de um segundo tipo genérico.  O procedimento e a sintaxe necessários são complexos e devem ser evitados.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, alterar o design para remover o argumento aninhado do tipo.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  Fornecer produtos genéricas em uma sintaxe que seja fácil de entender e em uso reduz o tempo necessário para conhecer e aumenta a taxa de adoção de novas bibliotecas.  
  
## Exemplo  
 O exemplo a seguir mostra um método que viola a regra e a sintaxe necessária para chamar o método violando.  
  
 [!code-vb[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/VisualBasic/ca1006-do-not-nest-generic-types-in-member-signatures_1.vb)]
 [!code-cs[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/CSharp/ca1006-do-not-nest-generic-types-in-member-signatures_1.cs)]  
  
## Regras Relacionadas  
 [CA1005: evitar parâmetros excessivos em tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: as coleções devem implementar a interface genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: não declarar membros estáticos em tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: não expor listas genéricas](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1004: os métodos genéricos devem fornecer o parâmetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: usar instâncias do manipulador de eventos genéricos](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007: usar genéricos quando apropriado](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Consulte também  
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)