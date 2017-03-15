---
title: "&#39;#ElseIf&#39; n&#227;o podem seguir #Else como parte de um bloco &#39;#If&#39; | Microsoft Docs"
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
  - "bc32030"
  - "vbc32030"
helpviewer_keywords: 
  - "BC32030"
ms.assetid: 248d6464-3019-4753-8a33-7070bbe5d2a6
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#ElseIf&#39; n&#227;o podem seguir #Else como parte de um bloco &#39;#If&#39;
Um `#ElseIf` diretiva de compilação condicional segue um `#Else` diretiva.`#Else` deve ser a última diretiva no bloco condicional antes do `#End If` diretiva.  
  
 **ID do erro:** BC32030  
  
### Para corrigir este erro  
  
1.  Verifique se o anterior `#Else` deve ser um `#ElseIf`.  
  
2.  Verifique se precedidos `#If` bloco é encerrado corretamente e que um novo `#If` bloco é iniciado.  
  
3.  Se tudo estiver correto, mova essa `#ElseIf` bloqueiam de diretiva e sua instrução correspondente para preceder o `#Else` bloco.  
  
## Consulte também  
 [Diretivas \#If...Then...\#Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)