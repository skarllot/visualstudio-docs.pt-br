---
title: "CS0550 de erro do compilador | Microsoft Docs"
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
  - "CS0550"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0550"
ms.assetid: 57278c17-443c-40f2-9ebd-853558743564
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0550 de erro do compilador
'o acessador' adiciona um acessador não encontrado no membro de interface 'property'  
  
 A implementação de uma propriedade em uma classe derivada contém um acessador que não foi especificado na interface base.  
  
 Para obter mais informações, consulte [Usando propriedades](/dotnet/csharp/programming-guide/classes-and-structs/using-properties).  
  
## Exemplo  
 O exemplo a seguir gera CS0550.  
  
```  
// CS0550.cs namespace x { interface ii { int i { get; // add the following accessor to resolve this CS0550 // set; } } public class a : ii { int ii.i { get { return 0; } set {}   // CS0550  no set in interface } public static void Main() {} } }  
```