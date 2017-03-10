---
title: "CS0171 de erro do compilador | Microsoft Docs"
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
  - "CS0171"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0171"
ms.assetid: 8c1d76c9-1048-4579-9031-23e3566e6288
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0171 de erro do compilador
O campo existente para a propriedade implementada automaticamente 'name' deve ser totalmente atribuído antes que o controle é retornado ao chamador. Considere a possibilidade de chamar o construtor padrão de um inicializador de construtor.  
  
 Um construtor em um [struct](/dotnet/csharp/language-reference/keywords/struct) deve inicializar todos os campos na estrutura. Para obter mais informações, consulte [Construtores](/dotnet/csharp/programming-guide/classes-and-structs/constructors).  
  
 O exemplo a seguir gera CS0171:  
  
```  
// CS0171.cs struct MyStruct { MyStruct(int initField)   // CS0171 { // i = initField;      // uncomment this line to resolve this error } public int i; } class MyClass { public static void Main() { MyStruct aStruct = new MyStruct(); } }  
```