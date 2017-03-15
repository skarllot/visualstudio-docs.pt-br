---
title: "CS0757 de erro do compilador | Microsoft Docs"
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
  - "CS0757"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0757"
ms.assetid: ba093570-306d-4b7b-aad5-1a3855ad6776
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0757 de erro do compilador
Um método parcial não pode ter várias declarações de implementação.  
  
 Um método parcial consiste em exatamente uma declaração de definição \(assinatura\) e um ou zero \(corpo\) do declarações de implementação. Não são permitidas várias declarações de implementação para as mesmo declarações de definição idênticas. Métodos parciais podem estar sobrecarregados, e cada versão sobrecarregada pode ter um ou zero declarações de implementação.  
  
### Para corrigir este erro  
  
1.  Remova todas exceto uma das declarações de implementação para o método parcial.  
  
## Exemplo  
 O exemplo a seguir gera CS0757:  
  
```  
// cs0757.cs using System; public partial class C { // Defining declaration. partial void Part(); // Implementing declaration. partial void Part() { //...Do something. } // Second implementing declaration. partial void Part() // CS0757 { //...Do something. } public static int Main() { return 1; } }  
```  
  
## Consulte também  
 [Classes e métodos partial](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)