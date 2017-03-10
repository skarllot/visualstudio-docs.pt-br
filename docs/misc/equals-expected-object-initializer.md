---
title: "&#39;=&#39; esperado (inicializador de objeto) | Microsoft Docs"
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
  - "vbc30984"
  - "bc30984"
helpviewer_keywords: 
  - "BC30984"
ms.assetid: 9cae8d32-775a-414f-9e51-0469974b6aab
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;=&#39; esperado (inicializador de objeto)
Para estabelecer o valor inicial de um campo ou propriedade em uma declaração de inicializador de objeto, você deve usar um sinal de igual. Por exemplo, a seguinte declaração determina "Microsoft" como o valor inicial para o `Name` propriedade `client`.  
  
```  
Dim client As New Customer { .Name = "Microsoft" }  
```  
  
 **ID do erro:** BC30984  
  
### Para corrigir este erro  
  
-   Adicione um sinal de igual na posição mostrada no exemplo anterior.  
  
## Consulte também  
 [Inicializadores de objeto: tipos nomeados e anônimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [NÃO está em compilação: Propriedades e procedimentos de propriedade](http://msdn.microsoft.com/pt-br/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [NÃO na compilação: Procedimentos de propriedade vs. Campos](http://msdn.microsoft.com/pt-br/da1c05c1-87c7-40fa-b92c-e9c7e4d170f7)