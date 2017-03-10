---
title: "Argumentos nomeados n&#227;o s&#227;o v&#225;lidos como subscritos de matriz | Microsoft Docs"
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
  - "vbc30075"
  - "bc30075"
helpviewer_keywords: 
  - "BC30075"
ms.assetid: a25025c9-0763-4c19-9e9b-cffb9aacaa8a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Argumentos nomeados n&#227;o s&#227;o v&#225;lidos como subscritos de matriz
Um índice de matriz é especificado usando a sintaxe para passar um argumento de procedimento pelo nome, por exemplo `Array(Index := 10)`. Essa sintaxe não é válida para subscritos de matriz.  
  
 **ID do erro:** BC30075  
  
### Para corrigir este erro  
  
-   Use uma expressão comum de variável ou constante como o índice de matriz, por exemplo `Array(10)`.  
  
## Consulte também  
 [Visão geral NOTINBUILD de matrizes no Visual Basic](http://msdn.microsoft.com/pt-br/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [Passando argumentos por posição e nome](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)