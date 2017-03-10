---
title: "&#39;ReDim&#39; n&#227;o pode alterar o n&#250;mero de dimens&#245;es de uma matriz | Microsoft Docs"
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
  - "vbc30415"
  - "bc30415"
helpviewer_keywords: 
  - "BC30415"
ms.assetid: 8ce97188-ff96-4e8c-917c-efc2f94173a3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ReDim&#39; n&#227;o pode alterar o n&#250;mero de dimens&#245;es de uma matriz
Você tentou usar `ReDim` para alterar a classificação \(número de dimensões\) de uma matriz. O `ReDim` instrução pode ser usada para alterar o tamanho de uma ou mais dimensões de um array que já foi formalmente declarado, mas ele não pode alterar a posição de uma matriz.  
  
 **ID do erro:** BC30415  
  
### Para corrigir este erro  
  
-   Certifique\-se de que você quer o grau ao invés dos tamanhos da matriz e, se possível, use `Dim` para declarar um novo array com o posto desejado.  
  
## Consulte também  
 [Instrução ReDim](/dotnet/visual-basic/language-reference/statements/redim-statement)   
 [Instrução Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Visão geral NOTINBUILD de matrizes no Visual Basic](http://msdn.microsoft.com/pt-br/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)