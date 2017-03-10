---
title: "CS0081 de erro do compilador | Microsoft Docs"
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
  - "CS0081"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0081"
ms.assetid: a5649abc-89ea-4f64-8c3c-eb36df926561
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0081 de erro do compilador
Declaração de parâmetro de tipo deve ser um identificador, não um tipo  
  
 Quando você declarar um método genérico ou tipo, especifique o parâmetro de tipo como um identificador, por exemplo, "T" ou "inputType". Quando o código do cliente chama o método, ele fornece o tipo, que substitui cada ocorrência do identificador no corpo do método ou classe. Para obter mais informações, consulte [Parâmetros de tipo genérico](/dotnet/csharp/programming-guide/generics/generic-type-parameters).  
  
```  
// CS0081.cs class MyClass { public void F<int>() {}   // CS0081 public void F<T>(T input) {}   // OK public static void Main() { MyClass a = new MyClass(); a.F<int>(2); a.F<double>(.05); } }  
```  
  
## Consulte também  
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)