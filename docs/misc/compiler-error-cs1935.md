---
title: "CS1935 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1935"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1935"
ms.assetid: d5dda801-fbf3-4340-bfe1-f9409f2d344d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1935 de erro do compilador
Não foi possível localizar uma implementação do padrão de consulta para o tipo de fonte 'type'. 'method' não encontrado. Está faltando uma referência a 'System.Core.dll' ou o uso de uma diretiva para 'System. Linq'?  
  
 O tipo de fonte em uma consulta deve ser `IEnumerable`, `IEnumerable<T>`, ou um tipo derivado, ou um tipo para o qual você ou outra pessoa tenha implementado os operadores de consulta padrão. Se o tipo de origem for um `IEnumerable` ou `IEnumerable<T>`, você deve adicionar uma referência a system.core.dll e uma `using` diretiva para o namespace System. LINQ para trazer métodos de extensão do operador de consulta padrão para o escopo. Implementações personalizadas dos operadores de consulta padrão devem ser colocadas no escopo da mesma forma, com um `using` diretiva e, se necessário, uma referência ao assembly.  
  
### Para corrigir este erro  
  
1.  Adicionar as diretivas de uso e referências ao projeto.  
  
## Exemplo  
 O código a seguir gera CS1935 porque o `using` diretiva para System. LINQ é comentada:  
  
```  
// cs1935.cs // CS1935 using System; using System.Collections.Generic; // using System.Linq; class Test { static int Main() { int[] nums = {0,1,2,3,4,5}; IEnumerable<int> e = from n in nums where n > 3 select n; return 0; } }  
```  
  
## Consulte também  
 [Visão geral de operadores de consulta padrão](../Topic/Standard%20Query%20Operators%20Overview.md)