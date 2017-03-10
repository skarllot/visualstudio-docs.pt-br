---
title: "CS1688 de erro do compilador | Microsoft Docs"
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
  - "CS1688"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1688"
ms.assetid: e15672a1-2570-4e65-99fc-7acc190ae643
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1688 de erro do compilador
Não é possível converter bloco de métodos anônimo sem uma lista de parâmetros para delegar o tipo 'delegate' porque ele tem um ou mais parâmetros de saída  
  
 O compilador permite que os parâmetros a serem omitidos de um bloco de métodos anônimo na maioria dos casos. Este erro ocorre quando o bloco de método anônimo não tem uma lista de parâmetros, mas o representante tem uma `out` parâmetro. O compilador não permite essa situação porque precisaria para ignorar a presença de `out` parâmetro, que é improvável de ser o comportamento correto.  
  
## Exemplo  
 O código a seguir gera erro CS1688.  
  
```  
// CS1688.cs using System; delegate void OutParam(out int i); class ErrorCS1676 { static void Main() { OutParam o; o = delegate  // CS1688 // Try this instead: // o = delegate(out int i) { Console.WriteLine(""); }; } }  
```