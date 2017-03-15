---
title: "Compilador CS0105 de aviso (n&#237;vel 3) | Microsoft Docs"
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
  - "CS0105"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0105"
ms.assetid: 96d1d5d7-79e9-424f-bbde-f87e88b70003
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0105 de aviso (n&#237;vel 3)
O uso de diretiva para 'namespace' exibido anteriormente neste namespace  
  
 Um [namespace](/dotnet/csharp/language-reference/keywords/namespace), que deve ser declarado apenas uma vez, foi declarado mais de uma vez; remover todas as declarações de namespace duplicadas.  
  
 O exemplo a seguir gera CS0105:  
  
```  
// CS0105.cs // compile with: /W:3 using System; using System;   // CS0105 public class a { public static void Main() { } }  
```