---
title: "CA1307: especificar StringComparison | Microsoft Docs"
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
  - "CA1307"
  - "SpecifyStringComparison"
helpviewer_keywords: 
  - "CA1307"
  - "SpecifyStringComparison"
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1307: especificar StringComparison
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyStringComparison|  
|CheckId|CA1307|  
|Categoria|Microsoft.Globalization|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Uma operação de comparação de cadeia de caracteres usa uma sobrecarga do método que não definir um parâmetro de <xref:System.StringComparison> .  
  
## Descrição da Regra  
 Muitos operações de cadeia, a maioria de <xref:System.String.Compare%2A> importante e os métodos de <xref:System.String.Equals%2A> , fornecem uma sobrecarga que aceita um valor de enumeração <xref:System.StringComparison> como um parâmetro.  
  
 Sempre que uma sobrecarga existir que usa um parâmetro de <xref:System.StringComparison> , deverá ser usado em vez de uma sobrecarga que não faça esse parâmetro.  Definindo explicitamente esse parâmetro, o código é feito normalmente mais claro e fácil.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, métodos de comparação de cadeia de caracteres de alteração nas sobrecargas que aceitam a enumeração de <xref:System.StringComparison> como um parâmetro.  Por exemplo: alteração `String.Compare(str1, str2)` a `String.Compare(str1, str2, StringComparison.Ordinal)`.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso desta regra quando a biblioteca ou o aplicativo devem ser usados por um público local limitada e em virtude disso não serão localizados.  
  
## Consulte também  
 [Avisos de globalização](../code-quality/globalization-warnings.md)   
 [CA1309: usar StringComparison ordinal](../code-quality/ca1309-use-ordinal-stringcomparison.md)