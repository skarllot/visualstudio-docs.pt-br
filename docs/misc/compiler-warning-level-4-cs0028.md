---
title: "Compilador CS0028 de aviso (n&#237;vel 4) | Microsoft Docs"
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
  - "CS0028"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0028"
ms.assetid: 47df919f-01fa-45ae-a4b7-912445e679e2
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0028 de aviso (n&#237;vel 4)
'declaração de função ' tem a assinatura incorreta para um ponto de entrada  
  
 A declaração de método para `Main` era inválido: foi declarado com uma assinatura inválida.`Main` deve ser declarado como static e ele devem retornar [int](/dotnet/csharp/language-reference/keywords/int) ou [void](/dotnet/csharp/language-reference/keywords/void). Para obter mais informações, consulte [Main\(\) e argumentos de linha de comando](/dotnet/csharp/programming-guide/main-and-command-args/main-and-command-line-arguments).  
  
 O exemplo a seguir gera CS0028:  
  
```  
// CS0028.cs // compile with: /W:4 /warnaserror public class a { public static double Main(int i)   // CS0028 // Try the following line instead: // public static void Main() { } }  
```