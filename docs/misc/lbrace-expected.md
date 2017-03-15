---
title: "&#39; {&#39; esperado | Microsoft Docs"
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
  - "vbc30987"
  - "bc30987"
helpviewer_keywords: 
  - "BC30987"
ms.assetid: 3d1552b6-338a-47cf-84d5-77b59209e0d3
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39; {&#39; esperado
Para declarar uma instância de um tipo nomeado ou anônimo usando um inicializador de objeto, você deve colocar a lista de campos ou propriedades e seus valores iniciais em chaves \({e}\).  
  
```  
Dim client As New Customer() With {.Name = "Microsoft", .City = "Seattle"}  
Dim emp = New Employee() With {.Name = "Rob Young", .ID = 55555}  
Dim anon = New With {.ID = 123456}  
```  
  
 **ID do erro:** BC30987  
  
### Para corrigir este erro  
  
-   Inclua uma lista de inicialização após `With`, entre chaves.  
  
## Consulte também  
 [Inicializadores de objeto: tipos nomeados e anônimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [NÃO na compilação: Procedimentos de propriedade vs. Campos](http://msdn.microsoft.com/pt-br/da1c05c1-87c7-40fa-b92c-e9c7e4d170f7)   
 [Tipos anônimos](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)