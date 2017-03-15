---
title: "Atributo n&#227;o pode ser usado porque n&#227;o tem um construtor p&#250;blico | Microsoft Docs"
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
  - "vbc30758"
  - "bc30758"
helpviewer_keywords: 
  - "BC30758"
ms.assetid: b72d1ff2-f6b2-4a89-9ac2-8765f77bcc97
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Atributo n&#227;o pode ser usado porque n&#227;o tem um construtor p&#250;blico
O construtor para o atributo que está sendo usado é `Private`, e não pode ser usado.  
  
 **ID do erro:** BC30758  
  
### Para corrigir este erro  
  
1.  Se você vir esse erro com um atributo personalizado que você desenvolveu, altere sua `Sub``New` modificador de acesso do construtor para `Public`.  
  
## Consulte também  
 [NÃO está em compilação: Atributos no Visual Basic](http://msdn.microsoft.com/pt-br/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [Tempo de vida do objeto: como os objetos são criados e destruídos](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)