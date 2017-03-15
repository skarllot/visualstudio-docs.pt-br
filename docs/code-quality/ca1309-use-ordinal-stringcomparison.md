---
title: "CA1309: usar StringComparison ordinal | Microsoft Docs"
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
  - "UseOrdinalStringComparison"
  - "CA1309"
helpviewer_keywords: 
  - "UseOrdinalStringComparison"
  - "CA1309"
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1309: usar StringComparison ordinal
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseOrdinalStringComparison|  
|CheckId|CA1309|  
|Categoria|Microsoft.Globalization|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Uma operação de comparação de cadeia de caracteres que é nonlinguistic não define o parâmetro de <xref:System.StringComparison> a **Ordinal** ou a **OrdinalIgnoreCase**.  
  
## Descrição da Regra  
 Muitos operações de cadeia, a maioria de <xref:System.String.Compare%2A?displayProperty=fullName> importante e os métodos de <xref:System.String.Equals%2A?displayProperty=fullName> , fornecem agora uma sobrecarga que aceita um valor de enumeração <xref:System.StringComparision?displayProperty=fullName> como um parâmetro.  
  
 Quando você especifica **StringComparison.Ordinal** ou **StringComparison.OrdinalIgnoreCase**, a comparação de cadeia de caracteres será nonlinguistic.  Ou seja, os recursos que são específicos do idioma natural é ignorado quando as decisões de comparação são feitas.  Isso significa que as decisões são baseadas em comparações simples de byte e ignoram o uso de maiúsculas e minúsculas ou as tabelas da equivalência que são parametrizadas a cultura.  No resultado, definindo explicitamente o parâmetro a **StringComparison.Ordinal** ou a **StringComparison.OrdinalIgnoreCase**, seu código geralmente ganha a velocidade, aumenta a exatidão, e se torna mais confiável.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere o método de comparação de cadeia de caracteres a sobrecarga que aceita a enumeração de <xref:System.StringComparison?displayProperty=fullName> como um parâmetro, e especifique **Ordinal** ou **OrdinalIgnoreCase**.  Por exemplo, altere `String.Compare(str1, str2)` a `String.Compare(str1, str2, StringComparison.Ordinal)`.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso desta regra quando a biblioteca ou o aplicativo são destinados para um público local delimitada ou quando a semântica da cultura atual deve ser usada.  
  
## Consulte também  
 [Avisos de globalização](../code-quality/globalization-warnings.md)   
 [CA1307: especificar StringComparison](../code-quality/ca1307-specify-stringcomparison.md)