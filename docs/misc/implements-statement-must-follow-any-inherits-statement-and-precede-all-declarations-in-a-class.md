---
title: "Declara&#231;&#227;o &#39;Implements&#39; deve seguir qualquer declara&#231;&#227;o &#39;Inherits&#39; e preceder todas as declara&#231;&#245;es em uma classe | Microsoft Docs"
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
  - "bc31053"
  - "vbc31053"
helpviewer_keywords: 
  - "BC31053"
ms.assetid: 8036a1a1-7e31-4c49-b74b-01601a548f3e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Declara&#231;&#227;o &#39;Implements&#39; deve seguir qualquer declara&#231;&#227;o &#39;Inherits&#39; e preceder todas as declara&#231;&#245;es em uma classe
Um `Implements` instrução foi encontrada em um local inválido.  
  
 **ID do erro:** BC31053  
  
### Para corrigir este erro  
  
-   Local `Implements` instruções imediatamente após quaisquer `Inherits` instruções, mas antes de quaisquer declarações. Por exemplo:  
  
    ```  
    Class Derived Inherits Base Implements One Sub SubOne() Implements One.Method1 ' Add code to implement the method. End Sub End Class  
    ```  
  
## Consulte também  
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)