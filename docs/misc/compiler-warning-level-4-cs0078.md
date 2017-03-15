---
title: "Compilador CS0078 de aviso (n&#237;vel 4) | Microsoft Docs"
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
  - "CS0078"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0078"
ms.assetid: 8d637be6-82bc-462c-bec5-217327bc8c40
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0078 de aviso (n&#237;vel 4)
O sufixo 'l'é facilmente confundido com o dígito '1' \- use 'l' para diferenciar  
  
 O compilador emitirá um aviso quando detecta uma conversão em tempo usando um l minúsculo, em vez de um maiúsculas. L.  
  
 O exemplo a seguir gera CS0078:  
  
```  
// CS0078.cs // compile with: /W:4 class test { public static void TestL(long i) { } public static void TestL(int i) { } public static void Main() { TestL(25l);   // CS0078 // try the following line instead // TestL(25L); } }  
```