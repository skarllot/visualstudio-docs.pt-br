---
title: "CA1819: as propriedades n&#227;o devem retornar matrizes | Microsoft Docs"
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
  - "PropertiesShouldNotReturnArrays"
  - "CA1819"
helpviewer_keywords: 
  - "PropertiesShouldNotReturnArrays"
  - "CA1819"
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1819: as propriedades n&#227;o devem retornar matrizes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PropertiesShouldNotReturnArrays|  
|CheckId|CA1819|  
|Categoria|Microsoft.Performance|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um público ou uma propriedade seguras em um tipo público retornam uma matriz.  
  
## Descrição da Regra  
 As matrizes retornadas por propriedades para gravação não são protegidas, mesmo se a propriedade é somente leitura.  Para manter a matriz inalterável, a propriedade deve retornar uma cópia da matriz.  Normalmente, os usuários não adversas integrarem as implicações de desempenho de chamar essas propriedades.  Especificamente, poderá usar a propriedade como uma propriedade indexada.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, faz à propriedade um método ou alterar a propriedade para retornar uma coleção.  
  
## Quando Suprimir Alertas  
 Os atributos podem conter as propriedades que as matrizes de retorno, mas não podem conter as propriedades que as coleções de retorno.  Você pode suprimir um aviso que é gerado para uma propriedade de um atributo que é derivado da classe de [System.Attribute](assetId:///System.Attribute?qualifyHint=False&autoUpgrade=True) .  Caso contrário, não suprima um aviso desta regra.  
  
## Violação de exemplo  
  
### Descrição  
 O exemplo a seguir mostra uma propriedade que viola esta regra.  
  
### Código  
 [!code-cs[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]  
  
### Comentários  
 Para corrigir uma violação desta regra, faz à propriedade um método ou alterar a propriedade para retornar uma coleção em vez de uma matriz.  
  
## Altere a propriedade para um método de exemplo  
  
### Descrição  
 O exemplo a seguir corrige a violação alterando a propriedade para um método.  
  
### Código  
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
 [!code-cs[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]  
  
## Retornar um exemplo de coleção  
  
### Descrição  
 O exemplo a seguir corrige a violação alterando a propriedade para retornar a  
  
 <xref:System.Collection.ObjectModel.ReadOnlyCollection?displayProperty=fullName>.  
  
### Código  
 [!code-cs[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]  
  
## Permitindo que os usuários possam modificar uma propriedade  
  
### Descrição  
 Talvez você queira permitir que o consumidor da classe modificar uma propriedade.  O exemplo a seguir mostra uma propriedade de leitura\/gravação que viola esta regra.  
  
### Código  
 [!code-cs[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]  
  
### Comentários  
 O exemplo a seguir corrige a violação alterando a propriedade para retornar <xref:System.Collection.ObjectModel.Collection?displayProperty=fullName>.  
  
### Código  
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
 [!code-cs[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]  
  
## Regras Relacionadas  
 [CA1024: usar propriedades quando apropriado](../code-quality/ca1024-use-properties-where-appropriate.md)