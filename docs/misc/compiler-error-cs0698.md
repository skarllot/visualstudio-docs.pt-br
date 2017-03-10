---
title: "CS0698 de erro do compilador | Microsoft Docs"
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
  - "CS0698"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0698"
ms.assetid: 68211652-fdfa-4d37-9451-f0b4238f9fe6
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0698 de erro do compilador
Um tipo genérico não pode derivar de 'class' porque ele é uma classe de atributo  
  
 Qualquer classe que deriva de uma classe de atributo é um atributo. Atributos não são permitidos para tipos genéricos.  
  
 O exemplo a seguir gera CS0698:  
  
```  
// CS0698.cs class C<T> : System.Attribute  // CS0698 { }  
```