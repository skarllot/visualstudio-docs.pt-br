---
title: "CS0012 de erro do compilador | Microsoft Docs"
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
  - "CS0012"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0012"
ms.assetid: 5523e349-22f4-4b0b-b4b0-c4bf26c461f4
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0012 de erro do compilador
O tipo 'type' é definido em um assembly que não é referenciado. Você deve adicionar uma referência ao assembly 'assembly'.  
  
 A definição de um tipo referenciado não foi encontrada. Isso pode ocorrer se necessário. Arquivo DLL não está incluído na compilação. Para obter mais informações, consulte [Add Reference Dialog Box](http://msdn.microsoft.com/pt-br/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) e [\/reference \(Import Metadata\)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).  
  
 A seguinte sequência de compilações resultará em CS0012:  
  
```  
// cs0012a.cs // compile with: /target:library public class A {}  
```  
  
 Em seguida:  
  
```  
// cs0012b.cs // compile with: /target:library /reference:cs0012a.dll public class B { public static A f() { return new A(); } }  
```  
  
 Em seguida:  
  
```  
// cs0012c.cs // compile with: /reference:cs0012b.dll class C { public static void Main() { object o = B.f();   // CS0012 } }  
```  
  
 Você pode resolver essa CS0012 compilando com `/reference:cs0012b.dll;cs0012a.dll`, ou no Visual Studio usando o [Add Reference Dialog Box](http://msdn.microsoft.com/pt-br/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) para adicionar uma referência ao cs0012a.dll além dos cs0012b.dll.