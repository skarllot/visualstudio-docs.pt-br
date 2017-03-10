---
title: "CS0625 de erro do compilador | Microsoft Docs"
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
  - "CS0625"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0625"
ms.assetid: 44091813-9988-436c-b35e-e24094793782
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0625 de erro do compilador
'field': tipos de campo de instância marcados com StructLayout\(LayoutKind.Explicit\) devem ter um atributo FieldOffset  
  
 Quando um struct é marcado com um explícito **StructLayout** atributo, todos os campos na estrutura devem ter o [FieldOffset](frlrfsystemruntimeinteropservicesfieldoffsetattributeclasstopic) atributo. Para obter mais informações, consulte [classe StructLayoutAttribute](frlrfSystemRuntimeInteropServicesStructLayoutAttributeClassTopic).  
  
 O exemplo a seguir gera CS0625:  
  
```  
// CS0625.cs // compile with: /target:library using System; using System.Runtime.InteropServices; [StructLayout(LayoutKind.Explicit)] struct A { public int i;   // CS0625 not static; an instance field } // OK [StructLayout(LayoutKind.Explicit)] struct B { [FieldOffset(5)] public int i; }  
```