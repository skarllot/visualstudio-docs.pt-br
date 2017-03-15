---
title: "Nome do campo ou propriedade a ser inicializados deve come&#231;ar com &#39;.&#39; | Microsoft Docs"
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
  - "vbc30985"
  - "bc30985"
helpviewer_keywords: 
  - "BC30985"
ms.assetid: 4cb543e1-477c-429c-82df-541ebff08543
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Nome do campo ou propriedade a ser inicializados deve come&#231;ar com &#39;.&#39;
Cada inicializador de membro em uma lista de inicializadores de objeto Especifica o nome de um campo ou propriedade e seu valor inicial. O nome do campo ou propriedade deve ser precedido por um ponto. Por exemplo, a seguinte declaração determina "Microsoft" como o valor inicial para o `Name` propriedade `client`.  
  
```  
Dim client As New Customer() With { .Name = "Microsoft" }  
```  
  
 **ID do erro:** BC30985  
  
### Para corrigir este erro  
  
-   Prefixo de cada nome de membro com um ponto.  
  
## Consulte também  
 [Inicializadores de objeto: tipos nomeados e anônimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [NÃO na compilação: Procedimentos de propriedade vs. Campos](http://msdn.microsoft.com/pt-br/da1c05c1-87c7-40fa-b92c-e9c7e4d170f7)