---
title: "Par&#226;metros de tipo ou tipos constru&#237;dos com par&#226;metros n&#227;o s&#227;o permitidos em argumentos de atributo de tipo | Microsoft Docs"
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
  - "BC32079"
  - "vbc32079"
helpviewer_keywords: 
  - "BC32079"
ms.assetid: 93eb59bd-e7db-4f73-a37f-405a83df48c1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Par&#226;metros de tipo ou tipos constru&#237;dos com par&#226;metros n&#227;o s&#227;o permitidos em argumentos de atributo de tipo
Um atributo é aplicado usando um argumento que é um parâmetro de tipo ou é construído usando um parâmetro de tipo.  
  
 Visual Basic e o .NET Framework atualmente não suportam qualquer combinação de atributos e tipos genéricos. Isso significa que as seguintes limitações se aplicam:  
  
-   Um atributo não pode ser um tipo genérico ou ser declarado em um tipo genérico.  
  
-   Um atributo não pode herdar de uma classe genérica, nem pode herdar de uma classe genérica de um atributo.  
  
-   Quando você aplica um atributo, você não pode fornecer um argumento que é o seguinte:  
  
    -   Um tipo genérico,  
  
    -   Um tipo construído de um tipo genérico,  
  
    -   Um parâmetro de tipo de um tipo de conteúdo, ou  
  
    -   Um tipo construído de um parâmetro de tipo de um tipo de contenção.  
  
 **ID do erro:** BC32079  
  
### Para corrigir este erro  
  
-   Reconstrua os argumentos fornecidos para o atributo para que elas não incluem os parâmetros de tipo ou qualquer tipo construído de um parâmetro de tipo.  
  
## Consulte também  
 <xref:System.Attribute>   
 [NÃO está em compilação: Visão geral de atributos no Visual Basic](http://msdn.microsoft.com/pt-br/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)