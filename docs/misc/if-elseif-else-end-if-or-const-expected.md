---
title: "&#39;If&#39;, &#39;ElseIf&#39;, &#39;Else&#39;, &#39;End If&#39; ou &#39;Const&#39; esperado | Microsoft Docs"
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
  - "vbc30248"
  - "bc30248"
helpviewer_keywords: 
  - "BC30248"
ms.assetid: fa3bf591-8036-459c-8c29-ed7784e444f6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;If&#39;, &#39;ElseIf&#39;, &#39;Else&#39;, &#39;End If&#39; ou &#39;Const&#39; esperado
Uma linha de origem começa com um `#` caracteres, mas uma diretiva de compilação condicional válido não seguem imediatamente o `#`. Diretivas válidas incluem `#Const`, `#ExternalSource`, `#If`, `#Else`, `#ElseIf`, `#End If`, e `#Region`.  
  
 **ID do erro:** BC30248  
  
### Para corrigir este erro  
  
1.  Verifique se que a diretiva de compilação condicional está escrita corretamente.  
  
2.  Verifique se não há nenhum espaço intermediário entre o `#` caractere e a diretiva.  
  
3.  Remover o `#` caractere ou adicione uma diretiva válida imediatamente após ele.  
  
## Consulte também  
 [Diretivas \(\)](/dotnet/visual-basic/language-reference/directives/directives)