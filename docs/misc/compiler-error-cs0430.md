---
title: "CS0430 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "09/30/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0430"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0430"
ms.assetid: b63c4f9a-b1cd-41d2-a02e-2ed0f177450f
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0430 de erro do compilador
O alias extern 'alias' não foi especificado em uma opção \/reference  
  
 Esse erro ocorre quando o Alias extern for encontrado, mas não foi especificado um Alias como referência na linha de comando. Para resolver CS0430, compilar com **\/reference**.  
  
## Exemplo  
  
```  
// CS0430_a.cs // compile with: /target:library public class MyClass {}  
```  
  
## Exemplo  
 Compilando com **\/reference:MyType\=cs0430\_a.dll** para referir\-se a DLL criada no exemplo anterior resolve esse erro. O exemplo a seguir gera CS0430.  
  
```  
// CS0430_b.cs extern alias MyType;   // CS0430 public class Test { public static void Main() {} }  
  
```