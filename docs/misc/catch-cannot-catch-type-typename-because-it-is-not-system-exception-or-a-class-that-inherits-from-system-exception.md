---
title: "&#39;Catch&#39; n&#227;o pode capturar o tipo &#39;&lt; typename &gt;&#39; porque ele n&#227;o &#233; &#39;System. Exception&#39; ou uma classe que herda de &#39;System. Exception&#39; | Microsoft Docs"
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
  - "vbc30392"
  - "bc30392"
helpviewer_keywords: 
  - "BC30392"
ms.assetid: 1d513d1d-38f5-4b4e-95bb-9f1209553803
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Catch&#39; n&#227;o pode capturar o tipo &#39;&lt; typename &gt;&#39; porque ele n&#227;o &#233; &#39;System. Exception&#39; ou uma classe que herda de &#39;System. Exception&#39;
`Catch` só pode interceptar exceções, e você tentou capturar algo que não é derivado de uma exceção.  
  
 **ID do erro:** BC30392  
  
### Para corrigir este erro  
  
1.  Remover o `Catch` declaração, ou alterar o destino do `Catch` para uma exceção real.  
  
## Consulte também  
 [Instrução Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Tratamento de visão geral do Visual Basic de exceções estruturado](http://msdn.microsoft.com/pt-br/bb81af80-a735-4873-9711-6151a48e418a)