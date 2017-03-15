---
title: "CA1004: os m&#233;todos gen&#233;ricos devem fornecer o par&#226;metro de tipo | Microsoft Docs"
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
  - "CA1004"
  - "GenericMethodsShouldProvideTypeParameter"
helpviewer_keywords: 
  - "CA1004"
  - "GenericMethodsShouldProvideTypeParameter"
ms.assetid: 38755f6a-fb45-4bf2-932e-0354ad826499
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1004: os m&#233;todos gen&#233;ricos devem fornecer o par&#226;metro de tipo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|GenericMethodsShouldProvideTypeParameter|  
|CheckId|CA1004|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 A assinatura de um método genérico externamente visível não contém tipos que correspondem aos parâmetros de tipo do método.  
  
## Descrição da Regra  
 A inferência é como o argumento de tipo de um método genérico é determinado pelo tipo de argumento transmitido ao método, em vez pela especificação explícita do argumento de tipo.  Para habilitar a inferência, a assinatura de parâmetro de um método genérico deve incluir um parâmetro que seja do mesmo tipo do parâmetro de tipo para o método.  Nesse caso, o argumento do tipo não precisa ser especificado.  Quando você usa a inferência para todos os parâmetros de tipo, a sintaxe para chamar métodos genéricos e não da instância é idêntica.  Isso simplifica a utilidade de métodos genéricos.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, modificar o design de modo que a assinatura do parâmetro contém o mesmo tipo para cada parâmetro de tipo do método.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  Fornecer produtos genéricas em uma sintaxe que seja fácil de entender e em uso reduz o tempo necessário para conhecer e aumenta a taxa de adoção de novas bibliotecas.  
  
## Exemplo  
 O exemplo a seguir mostra a sintaxe para chamar dois métodos genéricos.  O argumento de tipo para `InferredTypeArgument` é inferido, e o argumento de tipo para `NotInferredTypeArgument` deve ser explicitamente especificado.  
  
 [!code-vb[FxCop.Design.Inference#1](../code-quality/codesnippet/VisualBasic/ca1004-generic-methods-should-provide-type-parameter_1.vb)]
 [!code-cs[FxCop.Design.Inference#1](../code-quality/codesnippet/CSharp/ca1004-generic-methods-should-provide-type-parameter_1.cs)]  
  
## Regras Relacionadas  
 [CA1005: evitar parâmetros excessivos em tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: as coleções devem implementar a interface genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: não declarar membros estáticos em tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: não expor listas genéricas](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006: não aninhar tipos genéricos em assinaturas de membro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1003: usar instâncias do manipulador de eventos genéricos](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007: usar genéricos quando apropriado](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Consulte também  
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)