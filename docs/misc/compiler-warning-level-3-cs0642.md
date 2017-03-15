---
title: "Compilador CS0642 de aviso (n&#237;vel 3) | Microsoft Docs"
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
  - "CS0642"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0642"
ms.assetid: e2df58c0-9b7e-4e50-8e31-e0134955f62c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0642 de aviso (n&#237;vel 3)
Instrução empty possivelmente incorreta  
  
 Um ponto e vírgula após uma instrução condicional pode fazer com que seu código seja executado de forma diferente do pretendido.  
  
 Você pode usar **\/nowarn** opção de compilador ou `#pragmas warning` para desabilitar o aviso; consulte [\/nowarn \(Suppress Specified Warnings\)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option) ou [\#pragma warning](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) para obter mais informações.  
  
 O exemplo a seguir gera CS0642:  
  
```  
// CS0642.cs // compile with: /W:3 class MyClass { public static void Main() { int i; for (i = 0; i < 10; i += 1);   // CS0642 semicolon intentional? { System.Console.WriteLine (i); } } }  
```