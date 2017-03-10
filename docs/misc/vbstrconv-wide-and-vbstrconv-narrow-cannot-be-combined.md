---
title: "VbStrConv. Wide e VbStrConv n&#227;o podem ser combinados | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrArgument_IllegalWideNarrow"
ms.assetid: a53b4e6a-36b1-4e36-b2c5-8196313ec599
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# VbStrConv. Wide e VbStrConv n&#227;o podem ser combinados
Seu aplicativo está tentando combinar o `VbStrConv` membros de enumeração `Wide` e `Narrow`, que são mutuamente exclusivos.  
  
### Para corrigir este erro  
  
1.  Remova `VbStrConv.Wide` ou `VbStrConv.Narrow`.  
  
## Consulte também  
 <xref:System.Globalization>   
 [NOTINBUILD VbStrConv Enumeration](http://msdn.microsoft.com/pt-br/59f83dd9-6361-47df-a836-02ba9d4cb936)   
 [Introdução a aplicativos internacionais com base no .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)