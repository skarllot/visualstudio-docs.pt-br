---
title: "Argumentos inesperados de tipo como atributos n&#227;o podem ser gen&#233;ricos | Microsoft Docs"
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
  - "bc32066"
  - "vbc32066"
helpviewer_keywords: 
  - "BC32066"
ms.assetid: cd43a92c-33fb-4def-bbf7-527d21bff93c
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Argumentos inesperados de tipo como atributos n&#227;o podem ser gen&#233;ricos
Um atributo é aplicado usando uma lista de argumentos de tipo.  
  
 Visual Basic e o .NET Framework atualmente não suportam qualquer combinação de atributos e tipos genéricos. Isso significa que as seguintes limitações se aplicam:  
  
-   Um atributo não pode ser um tipo genérico ou ser declarado em um tipo genérico.  
  
-   Um atributo não pode herdar de uma classe genérica, nem pode herdar de uma classe genérica de um atributo.  
  
-   Quando você aplica um atributo, você não pode fornecer um argumento que é o seguinte:  
  
    -   Um tipo genérico,  
  
    -   Um tipo construído de um tipo genérico,  
  
    -   Um parâmetro de tipo de um tipo de conteúdo, ou  
  
    -   Um tipo construído de um parâmetro de tipo de um tipo de contenção.  
  
 **ID do erro:** BC32066  
  
### Para corrigir este erro  
  
-   Se os argumentos de tipo devem ser argumentos normais, remova o `Of` palavra\-chave. Isso transforma a lista de argumentos de tipo em uma lista de argumentos normal.  
  
-   Se os argumentos de tipo devem ser fornecidos para parâmetros de tipo e, em seguida, remover o `Of` palavra\-chave e todos os argumentos de tipo. Um atributo não pode aceitar argumentos de tipo.  
  
## Consulte também  
 <xref:System.Attribute>   
 [NÃO está em compilação: Visão geral de atributos no Visual Basic](http://msdn.microsoft.com/pt-br/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)