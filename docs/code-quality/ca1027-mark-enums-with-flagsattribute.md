---
title: "CA1027: marcar enums com FlagsAttribute | Microsoft Docs"
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
  - "MarkEnumsWithFlags"
  - "CA1027"
helpviewer_keywords: 
  - "CA1027"
  - "MarkEnumsWithFlags"
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1027: marcar enums com FlagsAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkEnumsWithFlags|  
|CheckId|CA1027|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Os valores de uma enumeração pública são a potência de dois ou são combinações de outros valores que estão definidos na enumeração, e o atributo de <xref:System.FlagsAttribute?displayProperty=fullName> não está presente.  Para reduzir falsos positivos, esta regra não informa uma violação para enumerações que têm valores contíguas.  
  
## Descrição da Regra  
 Uma enumeração é um tipo de valor que define um conjunto de constantes nomeadas relacionadas.  Aplicar <xref:System.FlagsAttribute> a uma enumeração quando as constantes nomeadas podem ser combinadas significativa.  Por exemplo, considere uma enumeração dos dias da semana em um aplicativo que se manter o controle dos recursos do dia estão disponíveis.  Se a disponibilidade de cada recurso é codificada usando a enumeração que tem <xref:System.FlagsAttribute> atual, qualquer combinação de dias pode ser representada.  Sem o atributo, apenas um dia da semana pode ser representado.  
  
 Para os campos que armazenam enumerações combináveis, os valores de enumeração individuais são tratados como grupos de bit no campo.  Consequentemente, esses campos são referidos às vezes como *campos de bit*.  Para combinar os valores de enumeração para armazenamento em um bit campo, use os operadores boolianos condicionais.  Para testar um bit coloque para determinar se um valor de enumeração específica estiver presente, usam os operadores lógicos boolianos.  Para colocar um bit para armazenar e recuperar corretamente valores de enumeração combinados, cada valor que é definido na enumeração deve ser uma potência de dois.  A menos que isso seja isso, os operadores lógicos boolianos não poderão extrair os valores de enumeração individuais que são armazenados no campo.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, adicione <xref:System.FlagsAttribute> a enumeração.  
  
## Quando Suprimir Alertas  
 Suprima um aviso dessa regra se você não quiser que os valores de enumeração para ser combinável.  
  
## Exemplo  
 No exemplo a seguir, `DaysEnumNeedsFlags` é uma enumeração que atenda aos requisitos para usar <xref:System.FlagsAttribute>, mas não tem o.  A enumeração de `ColorEnumShouldNotHaveFlag` não tem valores que são a potência de dois, mas especifica <xref:System.FlagsAttribute>incorretamente.  Isso violará a regra [CA2217: não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).  
  
 [!CODE [FxCop.Design.EnumFlags#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.EnumFlags#1)]  
  
## Regras Relacionadas  
 [CA2217: não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## Consulte também  
 <xref:System.FlagsAttribute?displayProperty=fullName>