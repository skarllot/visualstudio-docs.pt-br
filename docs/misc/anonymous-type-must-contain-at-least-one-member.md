---
title: "Tipo an&#244;nimo deve conter pelo menos um membro | Microsoft Docs"
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
  - "bc36574"
  - "vbc36574"
helpviewer_keywords: 
  - "BC36574"
ms.assetid: fdc8dd47-ea38-49e8-8dd5-676f726cd101
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipo an&#244;nimo deve conter pelo menos um membro
A lista do inicializador em uma declaração de tipo anônimo não pode ficar vazia.  
  
```  
' Not valid. ' Dim anonInstance = New With {}  
```  
  
 **ID do erro:** BC36574  
  
### Para corrigir este erro  
  
-   Declare um membro dentro dos colchetes, conforme mostrado no código a seguir.  
  
    ```  
    Dim anonInstance = New With {.MemberName = "value"}  
    ```  
  
## Consulte também  
 [Tipos anônimos](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)