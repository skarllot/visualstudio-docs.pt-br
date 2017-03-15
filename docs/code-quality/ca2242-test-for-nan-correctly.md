---
title: "CA2242: teste para NaN corretamente | Microsoft Docs"
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
  - "TestForNaNCorrectly"
  - "CA2242"
helpviewer_keywords: 
  - "CA2242"
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2242: teste para NaN corretamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TestForNaNCorrectly|  
|CheckId|CA2242|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Uma expressão testa um valor em <xref:System.Single.Nan?displayProperty=fullName> ou <xref:System.Double.Nan?displayProperty=fullName>.  
  
## Descrição da Regra  
 <xref:System.Double.NaN?displayProperty=fullName>, que representa o não é um número, os resultados quando uma operação aritmética for indefinida.  Qualquer expressão que testar a igualdade entre um valor e <xref:System.Double.NaN?displayProperty=fullName> sempre retorna `false`.  Qualquer expressão que testar a desigualdade entre um valor e <xref:System.Double.NaN?displayProperty=fullName> sempre retorna `true`.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra e determinar exatamente se um valor representa <xref:System.Double.NaN?displayProperty=fullName>, use <xref:System.Single.IsNan%2A?displayProperty=fullName> ou <xref:System.Double.IsNan%2A?displayProperty=fullName> para testar o valor.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 O exemplo a seguir mostra duas expressões que testam incorretamente um valor em <xref:System.Double.NaN?displayProperty=fullName> e uma expressão que usa corretamente <xref:System.Double.IsNaN%2A?displayProperty=fullName> para testar o valor.  
  
 [!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
 [!code-cs[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]