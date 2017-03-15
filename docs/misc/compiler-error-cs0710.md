---
title: "CS0710 de erro do compilador | Microsoft Docs"
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
  - "CS0710"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0710"
ms.assetid: 753a1a87-f5e5-4758-a960-515069a6c7b0
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0710 de erro do compilador
Classes static não podem ter construtores de instância  
  
 Uma classe estática não pode ser instanciada, portanto, tem sem a necessidade de construtores. Para evitar esse erro, remova os construtores de classes estáticas ou se você realmente deseja construir instâncias, verifique a classe não estático.  
  
 O exemplo a seguir gera CS0710:  
  
```  
// CS0710.cs public static class C { public C()  // CS0710 { } public static void Main() { } }  
```