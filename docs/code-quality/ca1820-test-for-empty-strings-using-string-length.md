---
title: "CA1820: teste para cadeias de caracteres vazias usando o comprimento da cadeia de caracteres | Microsoft Docs"
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
  - "TestForEmptyStringsUsingStringLength"
  - "CA1820"
helpviewer_keywords: 
  - "TestForEmptyStringsUsingStringLength"
  - "CA1820"
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1820: teste para cadeias de caracteres vazias usando o comprimento da cadeia de caracteres
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TestForEmptyStringsUsingStringLength|  
|CheckId|CA1820|  
|Categoria|Microsoft.Performance|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Uma cadeia de caracteres é comparada à cadeia de caracteres vazia usando <xref:System.Object.Equals%2A?displayProperty=fullName>.  
  
## Descrição da Regra  
 Comparar que usam usando a propriedade de <xref:System.String.Length%2A?displayProperty=fullName> ou o método de <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> é muito mais rápido do que usando <xref:System.Object.Equals%2A>.  Isso ocorre porque <xref:System.Object.Equals%2A> executa significativamente mais instruções de MSIL do que <xref:System.String.IsNullOrEmpty%2A> ou o número de instruções executadas para recuperar o valor da propriedade de <xref:System.String.Length%2A> e para o comparar a zero.  
  
 Lembre\-se de que <xref:System.Object.Equals%2A> e \=\= 0 de <xref:System.String.Length%2A> se comportam diferentemente das cadeias de caracteres nulas.  Se você tenta obter o valor da propriedade de <xref:System.String.Length%2A> em uma cadeia de caracteres nula, Common Language Runtime gerencie <xref:System.NullReferenceException?displayProperty=fullName>.  Se você executa uma comparação entre uma cadeia de caracteres nula e a cadeia de caracteres vazia, Common Language Runtime não gerará uma exceção; a comparação retorna `false`.  Os testes para nulo não afetam significativamente o desempenho em relação dessas duas abordagens.  O destino [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], use o método de <xref:System.String.IsNullOrEmpty%2A> .  Se não, use a comparação \=\= de <xref:System.String.Length%2A> sempre que possível.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere a comparação para usar a propriedade e o teste de <xref:System.String.Length%2A> para a cadeia de caracteres nula.  Se [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]destino, use o método de <xref:System.String.IsNullOrEmpty%2A> .  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso dessa regra se o desempenho não é um problema.  
  
## Exemplo  
 O exemplo a seguir ilustra as técnicas diferentes que são usadas para procurar uma cadeia de caracteres vazia.  
  
 [!CODE [FxCop.Performance.StringTest#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Performance.StringTest#1)]