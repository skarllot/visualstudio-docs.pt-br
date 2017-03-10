---
title: "Sintaxe do inicializador de objeto n&#227;o pode ser usado para inicializar uma inst&#226;ncia do tipo &#39;Object&#39; | Microsoft Docs"
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
  - "bc30994"
  - "vbc30994"
helpviewer_keywords: 
  - "BC30994"
ms.assetid: 2ef65965-f014-4fc1-8c7d-c603f0a764df
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Sintaxe do inicializador de objeto n&#227;o pode ser usado para inicializar uma inst&#226;ncia do tipo &#39;Object&#39;
Você não pode inicializar uma instância de `Object` usando a sintaxe do inicializador de objeto. Uma instância do `Object` não possui propriedades ou campos para designar um valor e objetos de sintaxe do inicializador requer pelo menos uma propriedade ou campo.  
  
```  
' Not valid. ' Dim obj1 = New Object With {} ' Dim obj2 = New Object With {.ToString = <some value>}  
```  
  
 **ID do erro:** BC30994  
  
### Para corrigir este erro  
  
1.  Declarar as instâncias do tipo `Object` sem usar uma lista de inicializadores:  
  
    ```  
    Dim obj3 as Object Dim obj4 as New Object()  
    ```  
  
## Consulte também  
 [Inicializadores de objeto: tipos nomeados e anônimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Tipo de dados Object](/dotnet/visual-basic/language-reference/data-types/object-data-type)