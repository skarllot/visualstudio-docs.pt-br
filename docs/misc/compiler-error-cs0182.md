---
title: "CS0182 de erro do compilador | Microsoft Docs"
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
  - "CS0182"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0182"
ms.assetid: a9e97bb8-f06e-499f-aadf-26abc2082f98
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0182 de erro do compilador
Um argumento de atributo deve ser uma expressão constante, a expressão typeof ou a expressão de criação de matriz de um tipo de parâmetro de atributo  
  
 Determinadas restrições para os tipos de argumentos podem ser usados com atributos. Observe que além das restrições especificadas na mensagem de erro, os seguintes tipos não são permitidos como argumentos de atributo:  
  
-   [sbyte](/dotnet/csharp/language-reference/keywords/sbyte)  
  
-   [ushort](/dotnet/csharp/language-reference/keywords/ushort)  
  
-   [uint](/dotnet/csharp/language-reference/keywords/uint)  
  
-   [ulong](/dotnet/csharp/language-reference/keywords/ulong)  
  
-   [decimal](/dotnet/csharp/language-reference/keywords/decimal)  
  
 Para obter mais informações, consulte [não está em compilação: atributos globais \(c\# Programming Guide\)](http://msdn.microsoft.com/pt-br/7c6c41f8-f0d5-4345-8987-3d91f9bae136).  
  
## Exemplo  
 O exemplo a seguir gera CS0182:  
  
```  
// CS0182.cs public class MyClass { static string s = "Test"; [System.Diagnostics.ConditionalAttribute(s)]   // CS0182 // try the following line instead // [System.Diagnostics.ConditionalAttribute("Test")] void NonConstantArgumentToConditional() { } public static void Main() { } }  
```