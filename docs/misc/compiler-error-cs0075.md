---
title: "CS0075 de erro do compilador | Microsoft Docs"
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
  - "CS0075"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0075"
ms.assetid: 5084d260-705e-4ff5-8f7a-7f74052fcbbb
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0075 de erro do compilador
Para converter um valor negativo, você deve colocar o valor entre parênteses  
  
 Se você estiver convertendo usando uma palavra\-chave que identifica um tipo predefinido, você não precisa parênteses. Caso contrário, você deve colocar os parênteses porque \(x\) – y não será considerada uma expressão de conversão. Da especificação do c\#, seção 7.6.6:  
  
 *Da regra de Desambigüidade segue que, se x e y são identificadores, \(y x\) \(x\)\(y\), e \(x\)\(\-y\) são expressões de conversão, mas \(x\)\-y for não, mesmo se x identifica um tipo. No entanto, se x for uma palavra\-chave que identifica um tipo predefinido \(como int\), em seguida, todos os quatro formulários são expressões de conversão \(porque tal uma palavra\-chave pode não ser uma expressão por si só\).*  
  
 O código a seguir gera CS0075:  
  
```  
// CS0075 namespace MyNamespace { enum MyEnum { } public class MyClass { public static void Main() { // To fix the error, place the negative // values below in parentheses int i = (System.Int32) - 4; //CS0075 MyEnum e = (MyEnum) - 1;    //CS0075 System.Console.WriteLine(i); //to avoid warning System.Console.WriteLine(e); //to avoid warning } } }  
```  
  
## Consulte também  
 [Conversões cast e conversões de tipo](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)