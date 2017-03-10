---
title: "CS0759 de erro do compilador | Microsoft Docs"
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
  - "CS0759"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0759"
ms.assetid: 96f0e178-adbf-4327-8934-ac282c428184
caps.latest.revision: 4
caps.handback.revision: 4
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0759 de erro do compilador
Nenhuma declaração de definição encontrada para implementar a declaração de método parcial 'method'.  
  
 Um método parcial deve ter uma declaração de definição que define a assinatura \(nome, tipo de retorno e parâmetros\) do método. O corpo de implementação ou método é opcional.  
  
### Para corrigir este erro  
  
1.  Fornece uma declaração de definição do método parcial na parte de uma classe ou struct.  
  
## Exemplo  
 O exemplo a seguir gera CS0759:  
  
```  
// cs0759.cs using System; public partial class C { partial void Part() // CS0759 { } public static int Main() { return 1; } }  
```  
  
## Consulte também  
 [Classes e métodos partial](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)