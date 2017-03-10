---
title: "&#39;&lt; method1 &gt;&#39; n&#227;o pode substituir &#39;&lt; method2 &gt;&#39; porque diferem pelos valores padr&#227;o de par&#226;metros opcionais | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30307"
  - "bc30307"
helpviewer_keywords: 
  - "BC30307"
ms.assetid: c4cf6040-41c3-4650-8eb9-bff063756599
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; method1 &gt;&#39; n&#227;o pode substituir &#39;&lt; method2 &gt;&#39; porque diferem pelos valores padr&#227;o de par&#226;metros opcionais
Você tentou substituir um método com outro método que difere do primeiro nos valores padrão de seus parâmetros opcionais, significando que suas assinaturas são diferentes. Um tipo pode substituir um método substituível herdado, declarando um método com o mesmo nome e assinatura e marcando a declaração com o `Overrides` modificador.  
  
 **ID do erro:** BC30307  
  
### Para corrigir este erro  
  
-   Verifique se que os dois métodos têm a mesma assinatura.  
  
## Consulte também  
 [NÃO está em compilação: Substituindo métodos e propriedades](http://msdn.microsoft.com/pt-br/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [NÃO está em compilação: Modificadores de substituição](http://msdn.microsoft.com/pt-br/18e8ef02-e79b-470e-837a-46a8f4163d32)