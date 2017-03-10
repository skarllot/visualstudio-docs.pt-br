---
title: "Inicializa&#231;&#227;o expl&#237;cita n&#227;o &#233; permitida para matrizes declaradas com limites expl&#237;citos | Microsoft Docs"
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
  - "bc30672"
  - "vbc30672"
helpviewer_keywords: 
  - "BC30672"
ms.assetid: 4b525e8d-bde5-4408-8c10-7605ca039f0e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Inicializa&#231;&#227;o expl&#237;cita n&#227;o &#233; permitida para matrizes declaradas com limites expl&#237;citos
Não não possível inicializar matrizes se elas são declaradas para um tamanho específico.  
  
 **ID do erro:** BC30672  
  
### Para corrigir este erro  
  
-   Declare a matriz e inicializá\-lo separadamente.  
  
-   Declare e inicialize como uma matriz dinâmica e usar `ReDim` se necessário; por exemplo:  
  
    ```  
    Dim A() As Integer = {0, 1, 2, 3} ReDim Preserve A(3)  
    ```  
  
## Consulte também  
 [Matrizes](/dotnet/visual-basic/programming-guide/language-features/arrays/index)