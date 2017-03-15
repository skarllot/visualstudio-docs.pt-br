---
title: "CS0546 de erro do compilador | Microsoft Docs"
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
  - "CS0546"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0546"
ms.assetid: d259c86f-ee29-4e2d-b381-6ba7252af87e
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0546 de erro do compilador
'o acessador': não é possível substituir porque 'property' não tem um acessador set substituível  
  
 Falha ao tentar substituir um dos métodos de acessador para um propriedade porque o acessador não pode ser substituído. Esse erro pode ocorrer se:  
  
-   a propriedade de classe base não é declarada como [virtual](/dotnet/csharp/language-reference/keywords/virtual).  
  
-   a propriedade de classe base não declara o [obter](/dotnet/csharp/language-reference/keywords/get) ou [definir](/dotnet/csharp/language-reference/keywords/set) acessador que você está tentando substituir.  
  
 Se você não deseja substituir a propriedade de classe base, você pode usar o [novo](/dotnet/csharp/language-reference/keywords/new) palavra\-chave antes da propriedade na classe derivada.  
  
 Para obter mais informações, consulte [Usando propriedades](/dotnet/csharp/programming-guide/classes-and-structs/using-properties).  
  
## Exemplo  
 O exemplo a seguir gera CS0546 porque a classe base não declara um acessador set para a propriedade.  
  
```  
// CS0546.cs // compile with: /target:library public class a { public virtual int i { get { return 0; } } public virtual int i2 { get { return 0; } set {} } } public class b : a { public override int i { set {}   // CS0546 error no set } public override int i2 { set {}   // OK } }  
```  
  
## Consulte também  
 [Propriedades](/dotnet/csharp/programming-guide/classes-and-structs/properties)