---
title: "Classe base &#39;&lt; baseclassname1 &gt;&#39; especificada para a classe &#39;&lt; partialclassname &gt;&#39; n&#227;o pode ser diferente da classe base &#39;&lt; baseclassname2 &gt;&#39; de um de seus outros tipos parciais | Microsoft Docs"
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
  - "BC30928"
  - "vbc30928"
helpviewer_keywords: 
  - "BC30928"
ms.assetid: da464f09-1016-4dec-beb7-3202cacd8e1e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Classe base &#39;&lt; baseclassname1 &gt;&#39; especificada para a classe &#39;&lt; partialclassname &gt;&#39; n&#227;o pode ser diferente da classe base &#39;&lt; baseclassname2 &gt;&#39; de um de seus outros tipos parciais
Uma classe é definida em dois ou mais declarações parciais, que contêm mais de um [Instrução Inherits](/dotnet/visual-basic/language-reference/statements/inherits-statement) especificando mais de uma classe base.  
  
 Quando você divide a definição de uma classe entre várias declarações parciais, o compilador trata a classe como a união de todas as suas declarações parciais. Isso se aplica não apenas aos membros mas também para a implementação, herança e nível de acesso.  
  
 Uma classe pode implementar mais de uma interface, mas ele não pode herdar de mais de uma classe base. Portanto, todas as `Inherits` instruções devem especificar a mesma classe base.  
  
 **ID do erro:** BC30928  
  
### Para corrigir este erro  
  
-   Decidir qual classe deve ser a classe base de sua classe parcial e remova qualquer suas declarações parciais `Inherits` instrução que especifica uma classe base diferente.  
  
## Consulte também  
 [Parcial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Instrução Inherits](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Noções básicas de herança](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)