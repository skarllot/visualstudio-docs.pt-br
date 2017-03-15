---
title: "Caracteres de tipo n&#227;o podem ser usados em declara&#231;&#245;es de tipo an&#244;nimo | Microsoft Docs"
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
  - "bc36560"
  - "vbc36560"
helpviewer_keywords: 
  - "BC36560"
ms.assetid: 70eee559-d6fc-409b-b835-2c84511b160e
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Caracteres de tipo n&#227;o podem ser usados em declara&#231;&#245;es de tipo an&#244;nimo
Você não pode usar um caractere de tipo em um nome de propriedade quando você declara uma instância de um tipo anônimo. O tipo de dados da propriedade é inferido do valor atribuído a ele. Por exemplo, as seguintes declarações não são válidas.  
  
```vb#  
'' Not valid. 'Dim anon1 = New With {.ID$ = "abc"} 'Dim anon2 = New With {.ID$ = 42}  
```  
  
 **ID do erro:** BC36560  
  
### Para corrigir este erro  
  
-   Remova o caractere de tipo de lista de inicializadores. Você pode converter explicitamente o valor atribuído, se isso for necessário para estabelecer o tipo de dados que você deseja para a propriedade.  
  
    ```vb#  
    ' Valid. Dim anon1 = New With {.ID = "abc"} Dim anon2 = New With {.ID = CStr(42)}  
    ```  
  
## Consulte também  
 [Tipos anônimos](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [Como inferir nomes e tipos de propriedade na declaração de tipo anônimo](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)   
 [Conversões implícitas e explícitas](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)