---
title: "Tipo de restri&#231;&#227;o &#39;&lt; expression &gt;&#39; n&#227;o &#233; uma classe ou interface | Microsoft Docs"
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
  - "bc32048"
  - "vbc32048"
helpviewer_keywords: 
  - "BC32048"
ms.assetid: 68811886-44ac-43e1-9315-b39857310033
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipo de restri&#231;&#227;o &#39;&lt; expression &gt;&#39; n&#227;o &#233; uma classe ou interface
Uma lista de restrições inclui uma expressão que não representa uma restrição válida em um parâmetro de tipo.  
  
 Uma lista de restrições impõe exigências no tipo de argumento passado para o parâmetro de tipo. Você pode especificar os seguintes requisitos em qualquer combinação:  
  
-   O argumento de tipo deve implementar uma ou mais interfaces  
  
-   O argumento de tipo deve herdar de no máximo uma classe  
  
-   O argumento de tipo deve expor um construtor sem parâmetros que pode acessar o código de criação  
  
-   O argumento de tipo deve ser um tipo de referência, ou deve ser um tipo de valor  
  
 **ID do erro:** BC32048  
  
### Para corrigir este erro  
  
-   Verifique se a expressão e seus elementos estão escritos corretamente.  
  
-   Se a expressão não está qualificada para a lista anterior de requisitos, remova\-o da lista de restrições.  
  
-   Se a expressão fizer referência a uma interface ou classe, verifique se o compilador tem acesso a essa interface ou classe. Talvez você precise qualificar seu nome, e talvez seja necessário adicionar uma referência ao seu projeto. Para obter mais informações, consulte "Referências a projetos" [NOTINBUILD: Resolvendo uma referência quando várias variáveis têm o mesmo nome](http://msdn.microsoft.com/pt-br/9601e39f-1911-44e1-ace5-3f6e090408b9).  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Tipos de valor e referência](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)   
 [NOTINBUILD como: qualificar um nome de elemento declarado](http://msdn.microsoft.com/pt-br/6bd112f5-df6f-42b8-9427-a9225bfcbaab)   
 [How to: Add and Remove Project References](http://msdn.microsoft.com/pt-br/f51b784d-0bc8-4c19-a898-e560d5ed696b)