---
title: "CS0131 de erro do compilador | Microsoft Docs"
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
  - "CS0131"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0131"
ms.assetid: 822852cc-a426-4b7d-b2ff-0026a0c0a0e7
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0131 de erro do compilador
O lado esquerdo de uma atribuição deve ser uma variável, propriedade ou indexador  
  
 Em uma instrução de atribuição, o valor do lado direito é atribuído para a esquerda. O lado esquerdo deve ser uma variável, propriedade ou indexador.  
  
 Para corrigir esse erro, certifique\-se de que todos os operadores estão no lado direito e que o lado esquerdo é uma variável, propriedade ou indexador. Para obter mais informações, consulte [Instruções, expressões e operadores](/dotnet/csharp/programming-guide/statements-expressions-operators/index).  
  
## Exemplo  
 O exemplo a seguir gera CS0131.  
  
```  
// CS0131.cs public class MyClass { public int i = 0; public void MyMethod() { i++ = 1;   // CS0131 // try the following line instead // i = 1; } public static void Main() { } }  
```  
  
## Exemplo  
 Esse erro também pode ocorrer se você tentar executar operações aritméticas no lado esquerdo de um operador de atribuição, como no exemplo a seguir.  
  
```  
// CS0131b.cs public class C { public static int Main() { int a = 1, b = 2, c = 3; if (a + b = c) // CS0131 // try this instead // if (a + b == c) return 0; return 1; } }  
```