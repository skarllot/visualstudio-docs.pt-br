---
title: "CS0138 de erro do compilador | Microsoft Docs"
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
  - "CS0138"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0138"
ms.assetid: 970545f8-5ee5-428e-921a-3aa29f68d16d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0138 de erro do compilador
Uso de uma diretiva de namespace só pode ser aplicada a namespaces. 'type' é um tipo não é um namespace  
  
 Um [usando](/dotnet/csharp/language-reference/keywords/using) diretiva só pode ter o nome de um namespace como um parâmetro. Para obter mais informações, consulte [Namespaces](/dotnet/csharp/programming-guide/namespaces/index).  
  
 O exemplo a seguir gera CS0138:  
  
```  
// CS0138.cs using System.Object;   // CS0138  
```