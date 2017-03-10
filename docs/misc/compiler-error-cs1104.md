---
title: "CS1104 de erro do compilador | Microsoft Docs"
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
  - "CS1104"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1104"
ms.assetid: 65bfe85f-8dd1-4aed-bcd1-1f7e0635868c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1104 de erro do compilador
Uma matriz de parâmetros não pode ser usada com o modificador 'this' em um método de extensão.  
  
 O primeiro parâmetro de um método de extensão não pode ser uma matriz de parâmetros.  
  
### Para corrigir este erro  
  
1.  Lembre\-se de que o primeiro parâmetro de uma definição de método de extensão especifica que tipo o método será "estender". Não é um parâmetro de entrada. Portanto, faz sentido ter uma matriz de parâmetros neste local. Se você precisar passar uma matriz de parâmetros, torne\-o segundo parâmetro.  
  
## Exemplo  
 O exemplo a seguir gera CS1104:  
  
```  
// cs1104.cs // Compile with: /target:library public static class Extensions { public static void Test<T>(this params T[] tArr) {} // CS1104 }   
```  
  
## Consulte também  
 [Métodos de extensão](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)   
 [params](/dotnet/csharp/language-reference/keywords/params)