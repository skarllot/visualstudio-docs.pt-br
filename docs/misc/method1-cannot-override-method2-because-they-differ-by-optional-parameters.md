---
title: "&#39;&lt; method1 &gt;&#39; n&#227;o pode substituir &#39;&lt; method2 &gt;&#39; porque diferem nos par&#226;metros opcionais | Microsoft Docs"
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
  - "vbc30308"
  - "bc30308"
helpviewer_keywords: 
  - "BC30308"
ms.assetid: 591dc351-4b87-4e92-81e1-2c1ff51da295
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; method1 &gt;&#39; n&#227;o pode substituir &#39;&lt; method2 &gt;&#39; porque diferem nos par&#226;metros opcionais
Você tentou substituir um método com outro método que difere do primeiro nos valores de seus parâmetros opcionais, significando que suas assinaturas são diferentes. Um tipo pode substituir um método substituível herdado, declarando um método com o mesmo nome e assinatura e marcando a declaração com o `Overrides` modificador.  
  
 **ID do erro:** BC30308  
  
### Para corrigir este erro  
  
-   Verifique se que os dois métodos têm a mesma assinatura.  
  
## Consulte também  
 [NÃO está em compilação: Substituindo métodos e propriedades](http://msdn.microsoft.com/pt-br/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Substituições](/dotnet/visual-basic/language-reference/modifiers/overrides)