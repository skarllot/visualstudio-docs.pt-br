---
title: "O inicializador de matriz n&#227;o pode ser especificado para uma dimens&#227;o n&#227;o constante; Use o inicializador vazio &#39;{}&#39; | Microsoft Docs"
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
  - "vbc30949"
  - "bc30949"
helpviewer_keywords: 
  - "BC30949"
ms.assetid: b3d27d9c-7a1f-4bac-ad71-388b24b807b3
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O inicializador de matriz n&#227;o pode ser especificado para uma dimens&#227;o n&#227;o constante; Use o inicializador vazio &#39;{}&#39;
Uma matriz inicializa uma dimensão que não é conhecida em tempo de compilação.  
  
 O código a seguir gera este erro.  
  
```  
Dim j As Integer Dim intArray As Integer = New Integer(1, j) {{0, 100}, {1,101}}  
```  
  
 O código a seguir evita o erro.  
  
```  
Dim intArray As Integer = New Integer(1, j) {} For i As Integer = 0 To j intArray(0, i) = i intArray(1, i) = 100 + i Next i  
```  
  
 **ID do erro:** BC30949  
  
### Para corrigir este erro  
  
-   Se possível, especifique uma dimensão constante na declaração de matriz.  
  
-   Se você não pode especificar uma constante dimensão, você deve inicializar a matriz usando um loop quando a dimensão não constante torna\-se conhecido.  
  
## Consulte também  
 [Instrução For Each...Next](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)   
 [Visão geral NOTINBUILD de matrizes no Visual Basic](http://msdn.microsoft.com/pt-br/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [Como inicializar uma variável de matriz no Visual Basic](../Topic/How%20to:%20Initialize%20an%20Array%20Variable%20in%20Visual%20Basic.md)   
 [NOTINBUILD como: inicializar uma matriz Multidimensional](http://msdn.microsoft.com/pt-br/502dcf8b-d86c-46f1-ad7d-3ce809645774)