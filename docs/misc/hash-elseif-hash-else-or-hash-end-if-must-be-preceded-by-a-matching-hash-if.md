---
title: "&#39;#ElseIf&#39;, &#39;#Else&#39; ou &#39;#End If&#39; deve ser precedido por um &#39;#If&#39; correspondente | Microsoft Docs"
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
  - "vbc30013"
  - "bc30013"
helpviewer_keywords: 
  - "BC30013"
ms.assetid: 8fe2d23c-8b8f-46d8-90f2-7f8857ea43bb
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#ElseIf&#39;, &#39;#Else&#39; ou &#39;#End If&#39; deve ser precedido por um &#39;#If&#39; correspondente
`#ElseIf`, `#Else`, e `#End If` são diretivas de compilação condicional. O `#ElseIf`, `#Else`, ou `#End If` não é precedida por uma `#If` diretiva.  
  
 **ID do erro:** BC30013  
  
### Para corrigir este erro  
  
1.  Verifique se o pai pretendido `#If` não está separado da cláusula em questão por um bloco de compilação condicional ou incorretamente localizado `#End If`.  
  
    > [!NOTE]
    >  Apenas um `#Else` é permitido para cada `#If` Bloquear, então duas sucessivas `#Else` diretivas causam esse erro.  
  
2.  Verifique se os principais `#` não está ausente na anterior `#If` diretiva.  
  
3.  Se tudo estiver em ordem, adicione um `#If` diretiva para o início do bloco de compilação condicional.  
  
## Consulte também  
 [Diretivas \#If...Then...\#Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)