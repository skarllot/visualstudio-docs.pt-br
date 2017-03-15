---
title: "Atributos n&#227;o podem ser gen&#233;ricos ou tipos aninhados gen&#233;ricos | Microsoft Docs"
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
  - "bc32067"
  - "vbc32067"
helpviewer_keywords: 
  - "BC32067"
ms.assetid: 93ae2848-0a72-4ae5-82a3-32e0a49bb7cd
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Atributos n&#227;o podem ser gen&#233;ricos ou tipos aninhados gen&#233;ricos
Um atributo é declarado como um tipo genérico, ou em um tipo genérico.  
  
 Visual Basic e o .NET Framework atualmente não suportam qualquer combinação de atributos e tipos genéricos. Isso significa que as seguintes limitações se aplicam:  
  
-   Um atributo não pode ser um tipo genérico ou ser declarado em um tipo genérico.  
  
-   Um atributo não pode herdar de uma classe genérica, nem pode herdar de uma classe genérica de um atributo.  
  
-   Quando você aplica um atributo, você não pode fornecer um argumento que é o seguinte:  
  
    -   Um tipo genérico,  
  
    -   Um tipo construído de um tipo genérico,  
  
    -   Um parâmetro de tipo de um tipo de conteúdo, ou  
  
    -   Um tipo construído de um parâmetro de tipo de um tipo de contenção.  
  
 **ID do erro:** BC32067  
  
### Para corrigir este erro  
  
-   Se a declaração de atributo inclui a `Of` palavra\-chave e uma lista de parâmetros de tipo, em seguida, removê\-los.  
  
-   Se a declaração de atributo aparece dentro um tipo genérico, em seguida, movê\-lo para onde ele não está dentro de qualquer tipo genérico.  
  
## Consulte também  
 <xref:System.Attribute>   
 [NÃO está em compilação: Visão geral de atributos no Visual Basic](http://msdn.microsoft.com/pt-br/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)