---
title: "V&#225;rias inicializa&#231;&#245;es de &#39;&lt; nome do membro &gt;&#39; | Microsoft Docs"
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
  - "vbc30989"
  - "bc30989"
helpviewer_keywords: 
  - "BC30989"
ms.assetid: 574b6398-1e9d-43e1-ac16-6fc8687f71d9
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# V&#225;rias inicializa&#231;&#245;es de &#39;&lt; nome do membro &gt;&#39;
Várias inicializações de '\< nome \>'. Campos e propriedades podem ser inicializadas somente uma vez em uma expressão de inicializador de objeto.  
  
 Você pode atribuir um valor inicial para cada campo e propriedade em uma lista de inicializadores de objeto apenas uma vez. A declaração a seguir não é válida.  
  
```  
' Dim cust = New Customer() With {.Name = "Bob", .Name = "Robert"}  
```  
  
> [!NOTE]
>  Você pode usar um campo ou propriedade como o valor inicial para outro membro, conforme mostrado na seguinte declaração.  
  
```  
Dim cust = New Customer() With {.First = "Mike", .Last = "Nash", _ .Full = .First & " " & .Last}  
```  
  
 **ID do erro:** BC30989  
  
### Para corrigir este erro  
  
-   Elimine todas exceto uma das inicializações para cada campo ou propriedade na lista de inicializadores de objeto.  
  
## Consulte também  
 [Inicializadores de objeto: tipos nomeados e anônimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [NÃO na compilação: Procedimentos de propriedade vs. Campos](http://msdn.microsoft.com/pt-br/da1c05c1-87c7-40fa-b92c-e9c7e4d170f7)