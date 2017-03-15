---
title: "&#39;ReDim&#39; n&#227;o pode alterar o n&#250;mero de dimens&#245;es | Microsoft Docs"
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
  - "vbrArray_RankMismatch"
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ReDim&#39; n&#227;o pode alterar o n&#250;mero de dimens&#245;es
Uma operação tenta usar o `ReDim` instrução para alterar a classificação \(número de dimensões\) de uma matriz.`ReDim` pode alterar o tamanho de uma ou mais dimensões de um array que já foi formalmente declarado, mas ele não pode alterar o posto de um array.  
  
### Para corrigir este erro  
  
-   Certifique\-se de que você pretende alterar o posto do array e não os tamanhos das suas dimensões e se possível, use `Dim` para declarar um novo array com o posto desejado.  
  
## Consulte também  
 [Visão geral NOTINBUILD de matrizes no Visual Basic](http://msdn.microsoft.com/pt-br/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [NOTINBUILD matrizes multidimensionais no Visual Basic](http://msdn.microsoft.com/pt-br/d92cad25-07e2-4d79-8ea4-ab269700f5de)   
 [Instrução ReDim](/dotnet/visual-basic/language-reference/statements/redim-statement)   
 [Instrução Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)