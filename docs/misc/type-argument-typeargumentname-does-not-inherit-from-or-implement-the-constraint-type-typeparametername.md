---
title: "O argumento de tipo &#39;&lt; typeargumentname &gt;&#39; n&#227;o herdar de ou implementa o tipo de restri&#231;&#227;o &#39;&lt; typeparametername &gt;&#39; | Microsoft Docs"
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
  - "bc32044"
  - "vbc32044"
helpviewer_keywords: 
  - "BC32044"
ms.assetid: be91f648-c07d-4991-8ed1-28b1327619c4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O argumento de tipo &#39;&lt; typeargumentname &gt;&#39; n&#227;o herdar de ou implementa o tipo de restri&#231;&#227;o &#39;&lt; typeparametername &gt;&#39;
Um argumento de tipo fornecido para um tipo genérico não satisfaz a restrição de herança ou implementação no seu parâmetro de tipo correspondente.  
  
 Uma lista de restrições impõe exigências no tipo de argumento passado para o parâmetro de tipo. Os requisitos possíveis incluem o seguinte:  
  
-   O argumento de tipo deve implementar uma ou mais interfaces  
  
-   O argumento de tipo deve herdar de no máximo uma classe  
  
 Você pode combinar os requisitos acima para um parâmetro de tipo único.[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] não é possível construir o tipo, a menos que o código fornece argumentos de tipo que atendem a cada restrição em cada parâmetro de tipo definido no tipo genérico.  
  
 **ID do erro:** BC32044  
  
### Para corrigir este erro  
  
-   Selecione um argumento de tipo de um tipo que implementa todas as interfaces especificada para o parâmetro de tipo, e que herda da classe especificada, se houver um.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Como usar uma classe genérica](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)