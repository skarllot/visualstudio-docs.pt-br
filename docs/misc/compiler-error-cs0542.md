---
title: "CS0542 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0542"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0542"
ms.assetid: 68a89948-8b56-4cd5-95e2-0df7fcad50ac
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0542 de erro do compilador
'tipo definido pelo usuário': nomes de membro não podem ser o mesmo que o tipo delimitador  
  
 Os membros de uma classe ou struct não podem ter o mesmo nome que a classe ou estrutura, a menos que o membro é um construtor.  
  
 O exemplo a seguir gera CS0542:  
  
```c#  
// CS0542.cs class C { public int C; }  
```  
  
 Esse erro pode ser causado se você acidentalmente colocar um tipo de retorno em um construtor, que torna em vigor em um método comum. O exemplo a seguir gera CS0542 porque `F` é um método, não é um construtor, porque ele tem um tipo de retorno:  
  
```c#  
// CS0542.cs class F { // Remove void from F() to resolve the problem. void F()   // CS0542, same name as the class { } } class MyClass { public static void Main() { } }  
```  
  
 Se sua classe será denominada 'Item' e declarou um indexador como `this`, você pode obter esse erro. Um indexador padrão é dado o nome 'Item' no código emitido, criando o conflito.  
  
```c#  
// CS0542b.cs class Item { public int this[int i]  // CS0542 { get { return 0; } } } class CMain { public static void Main() { } }  
```