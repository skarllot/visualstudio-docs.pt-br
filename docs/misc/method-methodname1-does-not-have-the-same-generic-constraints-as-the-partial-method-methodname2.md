---
title: "O m&#233;todo &#39;&lt; methodname1 &gt;&#39; n&#227;o tem as mesmas restri&#231;&#245;es gen&#233;ricas que o m&#233;todo parcial &#39;&lt; methodname2 &gt;&#39; | Microsoft Docs"
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
  - "bc31438"
  - "vbc31438"
helpviewer_keywords: 
  - "BC31438"
ms.assetid: ea092f0c-661b-49db-80c1-76401fc8bc0b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O m&#233;todo &#39;&lt; methodname1 &gt;&#39; n&#227;o tem as mesmas restri&#231;&#245;es gen&#233;ricas que o m&#233;todo parcial &#39;&lt; methodname2 &gt;&#39;
Você definiu uma implementação de método parcial com restrições genéricas que diferem das restrições na declaração de método parcial. O código a seguir ilustra o erro.  
  
```vb#  
Partial Class Class1 Partial Private Sub Test(Of T As Class)(ByVal arg As T) End Sub End Class Partial Class Class1 '' The error occurs here, for Test. 'Private Sub Test(Of T As Structure)(ByVal arg As T) 'End Sub End Class  
```  
  
 **ID do erro:** BC31438  
  
## Consulte também  
 [Métodos parciais](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)   
 [Parcial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Procedimentos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)