---
title: "&#39;&lt; elementname &gt;&#39; n&#227;o pode ser declarado &#39;Parcial&#39; porque m&#233;todos parciais devem ser rotinas | Microsoft Docs"
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
  - "vbc31437"
  - "bc31437"
helpviewer_keywords: 
  - "BC31437"
ms.assetid: 31ca12ab-2c26-4907-a253-e7c57bb4f34b
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; elementname &gt;&#39; n&#227;o pode ser declarado &#39;Parcial&#39; porque m&#233;todos parciais devem ser rotinas
Somente `Sub` procedimentos podem ser declarados para ser métodos parciais. Por exemplo, o código a seguir causa esse erro porque `partialMethod` é uma função.  
  
```  
' Partial Private Function partialMethod(ByVal n As Integer) As Integer ' End Function  
```  
  
 **ID do erro:** BC31437  
  
### Para corrigir este erro  
  
-   Converter o que você está declarando como um método parcial para um `Sub`.  
  
-   Não use um método parcial nesse caso.  
  
## Consulte também  
 [Métodos parciais](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)   
 [Subprocedimentos](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)