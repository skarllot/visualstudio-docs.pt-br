---
title: "CS0711 de erro do compilador | Microsoft Docs"
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
  - "CS0711"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0711"
ms.assetid: 3a5a6d90-e15d-4808-a7a6-c85fd011a0d0
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0711 de erro do compilador
Classes static não podem conter destruidores  
  
 Uma classe estática não pode ser instanciada, portanto, ele tem sem necessidade de construtores ou destruidores. Para evitar esse erro, remova qualquer destruidores de classes estáticas ou, se você realmente deseja construir e destruir instâncias, tornar a classe não estático.  
  
 O exemplo a seguir gera CS0711:  
  
```  
// CS0711.cs public static class C { ~C()  // CS0711 { } public static void Main() { } }  
```