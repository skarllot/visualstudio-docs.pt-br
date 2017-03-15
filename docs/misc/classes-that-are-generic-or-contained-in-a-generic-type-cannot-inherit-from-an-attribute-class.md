---
title: "Classes gen&#233;ricas ou contidas em um tipo gen&#233;rico n&#227;o podem herdar de uma classe de atributo | Microsoft Docs"
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
  - "vbc32074"
  - "BC32074"
helpviewer_keywords: 
  - "BC32074"
ms.assetid: 3552ac98-d86a-4962-9d51-b9a8acc38ea1
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Classes gen&#233;ricas ou contidas em um tipo gen&#233;rico n&#227;o podem herdar de uma classe de atributo
Uma classe genérica ou aninhadas em um tipo genérico especifica que ela herda de uma classe de atributo.  
  
 Visual Basic e o .NET Framework atualmente não suportam qualquer combinação de atributos e tipos genéricos. Isso significa que as seguintes limitações se aplicam:  
  
-   Um atributo não pode ser um tipo genérico ou ser declarado em um tipo genérico.  
  
-   Um atributo não pode herdar de uma classe genérica, nem pode herdar de uma classe genérica de um atributo.  
  
-   Quando você aplica um atributo, você não pode fornecer um argumento que é o seguinte:  
  
    -   Um tipo genérico,  
  
    -   Um tipo construído de um tipo genérico,  
  
    -   Um parâmetro de tipo de um tipo de conteúdo, ou  
  
    -   Um tipo construído de um parâmetro de tipo de um tipo de contenção.  
  
 **ID do erro:** BC32074  
  
### Para corrigir este erro  
  
-   Alterar a classe base para algo diferente de uma classe de atributos, ou remova o `Inherits` instrução inteiramente.  
  
## Consulte também  
 <xref:System.Attribute>   
 [NÃO está em compilação: Visão geral de atributos no Visual Basic](http://msdn.microsoft.com/pt-br/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Noções básicas de herança](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Instrução Inherits](/dotnet/visual-basic/language-reference/statements/inherits-statement)