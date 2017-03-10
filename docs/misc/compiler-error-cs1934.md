---
title: "CS1934 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1934"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1934"
ms.assetid: 18624be3-d534-4695-bafd-cc664fcde15e
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1934 de erro do compilador
Não foi possível localizar uma implementação do padrão de consulta para o tipo de fonte 'type'. 'method' não encontrado. Considere especificar explicitamente o tipo da variável de intervalo 'name'.  
  
 Esse erro é gerado se uma expressão de consulta especifica uma fonte de dados para o qual não há operadores de consulta padrão são implementadas. Uma maneira de produzir esse erro é especificar um `ArrayList` sem fornecer um tipo explícito para a variável de intervalo.  
  
### Para corrigir este erro  
  
1.  No exemplo a seguir, a solução é especificar apenas o tipo da variável de intervalo:  
  
    ```  
    var q = from int x in list  
    ```  
  
## Exemplo  
 O exemplo a seguir mostra uma maneira de produzir CS1934:  
  
```  
// cs1934.cs using System.Linq; using System.Collections; static class Test { public static void Main() { var list = new ArrayList { 0, 1, 2, 3, 4, 5 }; var q = from x in list // CS1934 select x + 1; } }  
```  
  
## Consulte também  
 [Como consultar um ArrayList com LINQ](../Topic/How%20to:%20Query%20an%20ArrayList%20with%20LINQ.md)