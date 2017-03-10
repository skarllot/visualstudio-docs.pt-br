---
title: "Compilador CS1720 de aviso (n&#237;vel 1) | Microsoft Docs"
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
  - "CS1720"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1720"
ms.assetid: 97adc294-3a4c-4418-a4ed-ccff43125b62
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS1720 de aviso (n&#237;vel 1)
Expressão sempre causa uma System. NullReferenceException porque o valor padrão de 'tipo genérico' é nulo  
  
 Se você escrever uma expressão que envolva o padrão de uma variável de tipo genérico que é um tipo de referência \(por exemplo, uma classe\), este erro ocorrerá. Considere a seguinte expressão:  
  
```  
default(T).ToString()  
```  
  
 Uma vez que `T` é um tipo de referência, seu valor padrão é null e então tentar aplicar o <xref:System.Object.ToString%2A> método para ele gerará um <xref:System.NullReferenceException>.  
  
## Exemplo  
 Restrição de referência de classe no tipo `T` garante que `T` é um tipo de referência.  
  
 O exemplo a seguir gera CS1720.  
  
```  
// CS1720.cs using System; public class Tester { public static void GenericClass<T>(T t1) where T : class { Console.WriteLine(default(T).ToString());  // CS1720 } public static void Main() {} }  
```