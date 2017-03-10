---
title: "Opera&#231;&#245;es de liga&#231;&#227;o tardia n&#227;o podem ser convertida em uma &#225;rvore de express&#227;o | Microsoft Docs"
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
  - "vbc36604"
  - "bc36604"
helpviewer_keywords: 
  - "BC36604"
ms.assetid: 6fd66d12-8c99-46e0-9095-fe1b29fd2692
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Opera&#231;&#245;es de liga&#231;&#227;o tardia n&#227;o podem ser convertida em uma &#225;rvore de express&#227;o
Foi feita uma tentativa para converter uma operação de ligação tardia em uma árvore de expressão. Isso não é válido. Por exemplo, o código a seguir causa esse erro.  
  
```vb#  
Option Strict Off Module Module1 Sub Main() '' Not valid. ' Test(Function(someInstance) someInstance.SomeProperty) End Sub Sub Test(ByVal ex As Expressions.Expression(Of Func(Of Object, Object))) End Sub End Module  
```  
  
 **ID do erro:** BC36604  
  
## Consulte também  
 [Associação antecipada e tardia](/dotnet/visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding)   
 [NÃO está em compilação: Árvores de expressão em LINQ](http://msdn.microsoft.com/pt-br/1a2e8e74-4bbc-45ab-9a46-2b6cfce3bcb2)