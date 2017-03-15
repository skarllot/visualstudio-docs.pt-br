---
title: "A vari&#225;vel de intervalo &lt; vari&#225;vel &gt; oculta uma vari&#225;vel em um bloco delimitador ou uma vari&#225;vel de intervalo definida anteriormente na express&#227;o de consulta. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30978"
  - "vbc30978"
helpviewer_keywords: 
  - "BC30978"
ms.assetid: 806d94c1-653f-40c0-b1c4-95661c76a392
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A vari&#225;vel de intervalo &lt; vari&#225;vel &gt; oculta uma vari&#225;vel em um bloco delimitador ou uma vari&#225;vel de intervalo definida anteriormente na express&#227;o de consulta.
Uma variável de intervalo em uma consulta tem o mesmo nome que uma variável anteriormente definida dentro do mesmo escopo, ou uma variável de intervalo definida anteriormente dentro da consulta.  
  
 **ID do erro:** BC30978  
  
### Para corrigir este erro  
  
-   Certifique\-se de que todas as variáveis de alcance na sua consulta tenham nomes exclusivos que não duplicam nomes de variável existentes no mesmo escopo.  
  
-   Envolva consultas aninhadas com nomes de variável de controle duplicados em parênteses, separando o escopo para cada variável de intervalo.  
  
## Consulte também  
 [Introdução a LINQ no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)