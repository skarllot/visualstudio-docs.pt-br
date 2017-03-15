---
title: "CS1110 de erro do compilador | Microsoft Docs"
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
  - "CS1110"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1110"
ms.assetid: 5b571a76-1891-4f33-b23d-7c4cc654a05f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1110 de erro do compilador
Não é possível usar o modificador 'this' no primeiro parâmetro da declaração de método sem uma referência a System.Core.dll. Adicione uma referência a System.Core.dll ou remova o modificador 'this' da declaração de método.  
  
 Métodos de extensão têm suporte na versão 3.5 e versões posterior do .NET Framework. Métodos de extensão geram metadados que marca o método com um atributo. A classe de atributo está em system.core.dll.  
  
### Para corrigir este erro  
  
1.  Como a mensagem informa, adicione uma referência a System.Core.dll ou remover o `this` modificador da declaração de método.  
  
## Exemplo  
 O exemplo a seguir gera CS1110 se o arquivo não é compilado com uma referência a System.Core.dll:  
  
```  
// cs1110.cs // CS1110 // Compile with: /target:library public static class Extensions { public static bool Test(this bool b) { return b; } }  
```  
  
## Consulte também  
 [Métodos de extensão](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)