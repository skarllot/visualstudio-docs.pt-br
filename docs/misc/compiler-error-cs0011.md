---
title: "CS0011 de erro do compilador | Microsoft Docs"
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
  - "CS0011"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0011"
ms.assetid: 892553d7-a516-4631-84cd-94db5722c90d
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0011 de erro do compilador
A classe base ou interface 'class' no assembly 'assembly' referenciado pelo tipo 'tipo' não pôde ser resolvido  
  
 Uma classe que foi importada de um arquivo com **\/reference**, derivada de uma classe ou implementa uma interface que não foi encontrada. Isso pode ocorrer se uma DLL necessária também não está incluída na compilação com **\/reference**.  
  
 Para obter mais informações, consulte [Add Reference Dialog Box](http://msdn.microsoft.com/pt-br/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) e [\/reference \(Import Metadata\)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).  
  
## Exemplo  
  
```  
// CS0011_1.cs // compile with: /target:library public class Outer { public class B { } }  
```  
  
## Exemplo  
 O segundo arquivo cria uma DLL que define uma classe `C` que é derivada da classe `B` que foi criado no exemplo anterior.  
  
```  
// CS0011_2.cs // compile with: /target:library /reference:CS0011_1.dll // post-build command: del /f CS0011_1.dll public class C : Outer.B {}  
```  
  
## Exemplo  
 O terceiro arquivo substitui a DLL criada pela primeira etapa e omite a definição da classe interna `B`.  
  
```  
// CS0011_3.cs // compile with: /target:library /out:cs0011_1.dll public class Outer {}  
```  
  
## Exemplo  
 Finalmente, o quarto arquivo faz referência à classe `C` definido no segundo exemplo, que é derivado da classe `B`, e que está faltando.  
  
 O exemplo a seguir gera CS0011.  
  
```  
// CS0011_4.cs // compile with: /reference:CS0011_1.dll /reference:CS0011_2.dll // CS0011 expected class M { public static void Main() { C c = new C(); } }  
```  
  
## Consulte também  
 [Add Reference Dialog Box](http://msdn.microsoft.com/pt-br/2feb0fe2-0805-4cc9-8cba-b0315849dfb7)   
 [\/reference \(Import Metadata\)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option)