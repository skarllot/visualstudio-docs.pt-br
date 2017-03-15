---
title: "&#39;(&#39; Unexpected | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32095"
  - "bc32095"
helpviewer_keywords: 
  - "BC32095"
ms.assetid: a47ad15a-2cfc-4d17-9012-27ba85b7d783
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;(&#39; Unexpected
'\(' Unexpected. Matrizes de tipos genéricos sem instâncias não são permitidas.  
  
 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] não é possível compilar uma matriz, a menos que se trata de um tipo de dados específico. Você não pode usar um parâmetro de tipo de dados de um tipo genérico como o tipo de dados de uma matriz.  
  
 **ID do erro:** BC32095  
  
### Para corrigir este erro  
  
-   Se você precisar usar uma matriz, você deve declará\-la para ser de um tipo de dados específico. Você não pode usar um parâmetro de tipo de dados.  
  
-   Se você precisar de um grupo de elementos do tipo de dados que deve ser fornecido para um parâmetro de tipo de dados, você deve usar uma coleção em vez de uma matriz.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Coleções de PONTA em Visual Basic](http://msdn.microsoft.com/pt-br/8b2b7845-2251-4573-8dd3-c9f9c0a66a21)   
 [Gerenciando grupos de objetos no Visual Basic](http://msdn.microsoft.com/pt-br/50be4910-4732-4d5f-a18a-055a162e9037)