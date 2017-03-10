---
title: "&#39;GoTo &lt; labelname &gt;&#39; n&#227;o &#233; v&#225;lido porque &#39;&lt; labelname &gt;&#39; est&#225; dentro de um bloco &#39;Try&#39;, &#39;Catch&#39; ou &#39;Finally&#39; que n&#227;o cont&#233;m essa declara&#231;&#227;o | Microsoft Docs"
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
  - "bc30754"
  - "vbc30754"
helpviewer_keywords: 
  - "BC30754"
ms.assetid: 2eefc7fb-fdf0-41e9-bf60-c3bc93580e14
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;GoTo &lt; labelname &gt;&#39; n&#227;o &#233; v&#225;lido porque &#39;&lt; labelname &gt;&#39; est&#225; dentro de um bloco &#39;Try&#39;, &#39;Catch&#39; ou &#39;Finally&#39; que n&#227;o cont&#233;m essa declara&#231;&#227;o
Você não pode ramificar em um `Try...Catch...Finally` bloco.  
  
 **ID do erro:** BC30754  
  
### Para corrigir este erro  
  
-   Reestruturar o código para que o rótulo preceda o `Try...Catch...Finally` bloco.  
  
## Consulte também  
 [Instrução Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)