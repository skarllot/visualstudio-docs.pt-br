---
title: "CS0641 de erro do compilador | Microsoft Docs"
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
  - "CS0641"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0641"
ms.assetid: 5bcdb11a-fefd-4c71-9b31-4c4f719633f3
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0641 de erro do compilador
'attribute': atributo só é válido em classes derivadas de System. Attribute  
  
 Foi usado um atributo que só pode ser usado em uma classe que deriva de **Attribute**.  
  
 O exemplo a seguir gera CS0641:  
  
```  
// CS0641.cs using System; [AttributeUsage(AttributeTargets.All)] public class NonAttrClass   // CS0641 // try the following line instead // public class NonAttrClass : Attribute { } class MyClass { public static void Main() { } }  
```