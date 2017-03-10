---
title: "CS0061 de erro do compilador | Microsoft Docs"
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
  - "CS0061"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0061"
ms.assetid: 8dfc57a9-653d-4902-a88c-92032ba64024
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0061 de erro do compilador
Acessibilidade inconsistente: interface de base 1 de interface é menos acessível que interface 'interface 2'  
  
 Um [pública](/dotnet/csharp/language-reference/keywords/public) construção deve retornar um objeto acessível publicamente.  
  
 Acessibilidade de interface não pode ser limitada em uma interface derivada. Para obter mais informações, consulte [Interfaces](/dotnet/csharp/programming-guide/interfaces/index) e [Modificadores de acesso](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers).  
  
 O exemplo a seguir gera CS0061.  
  
```  
// CS0061.cs // compile with: /target:library internal interface A {} public interface AA : A {}  // CS0061 // OK public interface B {} internal interface BB : B {} internal interface C {} internal interface CC : C {}  
```