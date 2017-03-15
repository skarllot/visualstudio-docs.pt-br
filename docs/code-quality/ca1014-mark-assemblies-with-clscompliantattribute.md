---
title: "CA1014: marcar assemblies com CLSCompliantAttribute | Microsoft Docs"
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
  - "CA1014"
  - "MarkAssembliesWithClsCompliant"
helpviewer_keywords: 
  - "CA1014"
  - "MarkAssembliesWithClsCompliant"
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1014: marcar assemblies com CLSCompliantAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAssembliesWithClsCompliant|  
|CheckId|CA1014|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um assembly não tenha um atributo de <xref:System.CLSCompliantAttribute?displayProperty=fullName> aplicado a ela.  
  
## Descrição da Regra  
 CLS \(CLS\) define a nomeação de restrições, os tipos de dados, e as regras para que os assemblies devem se conformar se serão usadas pelas linguagens de programação.  O bom design exige que todos os assemblies indica explicitamente a conformidade com CLS de <xref:System.CLSCompliantAttribute>.  Se o atributo não está presente em um assembly, o assembly não for compatível.  
  
 É possível que um assembly compatível com CLS conter tipos ou membros de tipo que não são compatíveis.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, adicione o atributo ao assembly.  Em vez de marcar o assembly como inteiro de não conformidade, você deve determinar qual o tipo ou membros de tipo não é compatível e marcar esses elementos como tal.  Se possível, você deve fornecer uma alternativa compatível com CLS para membros de não conformidade de forma que o público possível a mais larga pode acessar toda a funcionalidade do assembly.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  Se você não quiser que o assembly para ser compatível, aplicar o atributo e defina seu valor como `false`.  
  
## Exemplo  
 O exemplo a seguir mostra um assembly que tem o atributo de <xref:System.CLSCompliantAttribute?displayProperty=fullName> aplicado o que declara compatível com CLS.  
  
 [!code-cs[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
 [!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]  
  
## Consulte também  
 <xref:System.CLSCompliantAttribute?displayProperty=fullName>   
 [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)