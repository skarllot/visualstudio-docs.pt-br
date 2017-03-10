---
title: "Identificador esperado, precedido por um per&#237;odo | Microsoft Docs"
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
  - "bc36576"
  - "vbc36576"
helpviewer_keywords: 
  - "BC36576"
ms.assetid: 02217cc4-8972-4a6d-97a6-4ecbb7399af2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Identificador esperado, precedido por um per&#237;odo
Um valor do qual um nome de propriedade não pode ser inferido foi incluído na lista de inicializadores de uma declaração de tipo anônimo sem que está sendo atribuído a um nome de propriedade.  
  
```  
' Not valid. ' Dim anon1 = New With {.grade = 100, 95}  
```  
  
 **ID do erro:** BC36576  
  
### Para corrigir este erro  
  
-   Forneça um nome de propriedade para cada valor na lista de inicializadores, conforme mostrado no código a seguir:  
  
    ```  
    Dim anon2 = New With {.grade1 = 100, .grade2 = 95}  
    ```  
  
## Consulte também  
 [Inicializadores de objeto: tipos nomeados e anônimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Como: declarar uma instância de um tipo anônimo \(Visual Basic\)](http://msdn.microsoft.com/pt-br/119f616c-9bcd-4731-ac00-4285be5959f7)   
 [Como inferir nomes e tipos de propriedade na declaração de tipo anônimo](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)