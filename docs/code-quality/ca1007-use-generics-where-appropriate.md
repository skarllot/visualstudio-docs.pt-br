---
title: "CA1007: usar gen&#233;ricos quando apropriado | Microsoft Docs"
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
  - "CA1007"
  - "UseGenericsWhereAppropriate"
helpviewer_keywords: 
  - "CA1007"
  - "UseGenericsWhereAppropriate"
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1007: usar gen&#233;ricos quando apropriado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseGenericsWhereAppropriate|  
|CheckId|CA1007|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um método externamente visível contém um parâmetro de referência do tipo <xref:System.Object?displayProperty=fullName>, e o assembly que contém [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]de destino.  
  
## Descrição da Regra  
 Um parâmetro de referência é um parâmetro que é alterado usando a palavra\-chave de `ref` \(`ByRef` em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  O tipo de argumento que é fornecido para um parâmetro de referência deve corresponder exatamente ao tipo do parâmetro de referência.  Para usar um tipo derivado do tipo de parâmetro de referência, o tipo deve primeiro ser convertido e é atribuído a uma variável do tipo do parâmetro de referência.  O uso de um método genérico permite que todos os tipos, sujeito a restrições, serão passados para o método sem primeira conversão o tipo para o tipo do parâmetro de referência.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, execute o método genérico e substituir o parâmetro de <xref:System.Object> usando um parâmetro de tipo.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 O exemplo a seguir mostra uma rotina de uso geral de troca que é implementada como métodos e não genéricas.  Observe que as cadeias de caracteres são trocadas com eficácia usando o método genérico comparado ao método não.  
  
 [!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
 [!code-cs[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]  
  
## Regras Relacionadas  
 [CA1005: evitar parâmetros excessivos em tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: as coleções devem implementar a interface genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: não declarar membros estáticos em tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: não expor listas genéricas](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006: não aninhar tipos genéricos em assinaturas de membro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: os métodos genéricos devem fornecer o parâmetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: usar instâncias do manipulador de eventos genéricos](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
## Consulte também  
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)