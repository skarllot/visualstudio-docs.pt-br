---
title: "CA1005: evitar par&#226;metros excessivos em tipos gen&#233;ricos | Microsoft Docs"
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
  - "AvoidExcessiveParametersOnGenericTypes"
  - "CA1005"
helpviewer_keywords: 
  - "AvoidExcessiveParametersOnGenericTypes"
  - "CA1005"
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1005: evitar par&#226;metros excessivos em tipos gen&#233;ricos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveParametersOnGenericTypes|  
|CheckId|CA1005|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um tipo genérico externamente visível tiver mais de dois parâmetros de tipo.  
  
## Descrição da Regra  
 Mais parâmetros de tipo que um tipo genérico contém, é mais difícil saber e lembrar\-se do que cada parâmetro de tipo representa.  Geralmente é óbvio com um parâmetro de tipo, como em `List<T>`e, em determinados casos com dois parâmetros de tipo, como em `Dictionary<TKey, TValue>`.  Se mais de dois parâmetros de tipo existirem, dificuldade fica muito grande para a maioria dos usuários \(por exemplo, `TooManyTypeParameters<T, K, V>` em C\# ou `TooManyTypeParameters(Of T, K, V)` em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, alterar o design para não usar mais de dois parâmetros de tipo.  
  
## Quando Suprimir Alertas  
 Não suprima um aviso desta regra a menos que o design exigir menos mais de dois parâmetros de tipo.  Fornecer produtos genéricas em uma sintaxe que seja fácil de entender e em uso reduz o tempo necessário para conhecer e aumenta a taxa de adoção de novas bibliotecas.  
  
## Regras Relacionadas  
 [CA1010: as coleções devem implementar a interface genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: não declarar membros estáticos em tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: não expor listas genéricas](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006: não aninhar tipos genéricos em assinaturas de membro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: os métodos genéricos devem fornecer o parâmetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: usar instâncias do manipulador de eventos genéricos](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007: usar genéricos quando apropriado](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Consulte também  
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)