---
title: "Inicializadores de matriz s&#243; s&#227;o v&#225;lidos para matrizes, mas o tipo de &#39;&lt; variablename &gt;&#39; &#233; &#39;&lt; typename &gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30679"
  - "vbc30679"
helpviewer_keywords: 
  - "BC30679"
ms.assetid: 3cf34882-7a58-4074-8ebb-52e58199a506
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Inicializadores de matriz s&#243; s&#227;o v&#225;lidos para matrizes, mas o tipo de &#39;&lt; variablename &gt;&#39; &#233; &#39;&lt; typename &gt;&#39;
Foi feita uma tentativa para inicializar uma variável de matriz não com uma lista de valores.  
  
 **ID do erro:** BC30679  
  
### Para corrigir este erro  
  
-   Declarar e inicializar a variável como uma matriz; Por exemplo:  
  
     `Dim intarray As Integer() = {1, 5, 9}`  
  
-   Inicialize a variável como um valor único. Por exemplo:  
  
     `Dim intvalue As Integer = 1`  
  
## Consulte também  
 [Instrução Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Declaração de variável](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)   
 [Matrizes](/dotnet/visual-basic/programming-guide/language-features/arrays/index)