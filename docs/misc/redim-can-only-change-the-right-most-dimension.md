---
title: "&#39;ReDim&#39; s&#243; pode alterar a dimens&#227;o mais &#224; direita | Microsoft Docs"
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
  - "vbrArray_TypeMismatch"
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ReDim&#39; s&#243; pode alterar a dimens&#227;o mais &#224; direita
Um `ReDim` instrução tentou usar o `Preserve` palavra\-chave para alterar uma dimensão de uma matriz que não seja a última dimensão. Ao usar `Preserve`, você pode redimensionar a última dimensão de uma matriz. Para todas as outras dimensões, você deve especificar o mesmo tamanho de matriz existente.  
  
### Para corrigir este erro  
  
-   Remover o `Preserve` palavra\-chave.  
  
## Consulte também  
 [Visão geral NOTINBUILD de matrizes no Visual Basic](http://msdn.microsoft.com/pt-br/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [NOTINBUILD matrizes multidimensionais no Visual Basic](http://msdn.microsoft.com/pt-br/d92cad25-07e2-4d79-8ea4-ab269700f5de)   
 [Instrução ReDim](/dotnet/visual-basic/language-reference/statements/redim-statement)   
 [Instrução Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Preservar \- excluir](http://msdn.microsoft.com/pt-br/91badeab-b4e0-48b6-92c9-9f0c8f995d81)