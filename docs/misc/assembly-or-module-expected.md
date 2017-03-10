---
title: "&#39;Assembly&#39; ou &#39;Module&#39; esperado | Microsoft Docs"
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
  - "vbc32015"
  - "bc32015"
helpviewer_keywords: 
  - "BC32015"
ms.assetid: 6e62fe8d-a875-4995-b6b2-443e75c65e85
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Assembly&#39; ou &#39;Module&#39; esperado
Um atributo global é especificado sem indicar se ele se aplica ao conjunto inteiro ou apenas para o módulo atual. Atributos globais devem especificar um `Assembly` ou `Module`.  
  
 Um atributo global é aquele que aparece em uma linha de código\-fonte propriamente dito, em vez de sendo aplicado à declaração de um determinado elemento de programação.  
  
 **ID do erro:** BC32015  
  
### Para corrigir este erro  
  
1.  Se você pretender o atributo para ser global, adicione a `Assembly` ou `Module` palavra\-chave para o início do bloco de atributo, seguido por dois pontos \(:\).  
  
2.  Se você não pretender o atributo para ser global, exclua o atributo bloco ou movê\-lo para uma declaração de elemento de programação.  
  
## Consulte também  
 [Assembly](/dotnet/visual-basic/language-reference/modifiers/assembly)   
 [Módulo \<keyword\>](../Topic/Module%20%3Ckeyword%3E%20\(Visual%20Basic\).md)   
 [NÃO está em compilação: Aplicação de atributos](http://msdn.microsoft.com/pt-br/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [NÃO está em compilação: Atributos globais no Visual Basic](http://msdn.microsoft.com/pt-br/253a32d8-1531-4504-b687-088554ab71d2)