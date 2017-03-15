---
title: "CA1813: evitar atributos n&#227;o lacrados | Microsoft Docs"
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
  - "CA1813"
  - "AvoidUnsealedAttributes"
helpviewer_keywords: 
  - "AvoidUnsealedAttributes"
  - "CA1813"
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1813: evitar atributos n&#227;o lacrados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidUnsealedAttributes|  
|CheckId|CA1813|  
|Categoria|Microsoft.Performance|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um tipo público herda de <xref:System.Attribute?displayProperty=fullName>, não é abstrato, e não é selado \(`NotInheritable` no Visual Basic\).  
  
## Descrição da Regra  
 A biblioteca de classes de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] fornece métodos para recuperar atributos personalizados.  Por padrão, esses métodos da hierarquia de herança de atributos; por exemplo <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> pesquisas de para o tipo de atributo especificado, ou qualquer tipo de atributo que estende o tipo de atributo especificado.  Selar o atributo elimina a pesquisa pela hierarquia de herança, e pode melhorar o desempenho.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, selar o tipo de atributo ou deixá\-lo abstrair.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso desta regra.  Faça isso apenas se você estiver definindo uma hierarquia de atributo e não pode selar o atributo ou deixá\-lo abstrair.  
  
## Exemplo  
 O exemplo a seguir mostra um atributo personalizado que satisfaça esta regra.  
  
 [!code-cs[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]  
  
## Regras Relacionadas  
 [CA1019: definir acessadores para argumentos de atributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1018: marcar atributos com AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)  
  
## Consulte também  
 [Atributos](../Topic/Attributes1.md)