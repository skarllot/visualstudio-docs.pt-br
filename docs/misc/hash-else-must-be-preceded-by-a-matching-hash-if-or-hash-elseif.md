---
title: "&#39; #Else &#39; deve ser precedido por um &#39;#If&#39; ou &#39;#ElseIf&#39; correspondente | Microsoft Docs"
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
  - "vbc30028"
  - "bc30028"
helpviewer_keywords: 
  - "BC30028"
ms.assetid: c6ed34de-d6ed-4227-9880-538055aff20a
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39; #Else &#39; deve ser precedido por um &#39;#If&#39; ou &#39;#ElseIf&#39; correspondente
`#Else` é uma diretiva de compilação condicional. Um `#Else` diretiva não é precedida por uma `#If` ou `#ElseIf` diretiva.  
  
 **ID do erro:** BC30028  
  
### Para corrigir este erro  
  
1.  Verifique se precedidos `#If` ou `#ElseIf` não está separado disso `#Else` por um bloco de compilação condicional ou incorretamente localizado `#End If`.  
  
2.  Verifique se `#Else` é precedido por outro `#Else` diretiva. Se estiver, remova `#Else` ou alterá\-lo para um `#ElseIf`.  
  
3.  Se tudo estiver em ordem, adicione um `#If` diretiva para o início do bloco de compilação condicional.  
  
## Consulte também  
 [Diretivas \#If...Then...\#Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)