---
title: "CS0221 de erro do compilador | Microsoft Docs"
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
  - "CS0221"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0221"
ms.assetid: 97170b49-54f1-4dac-a865-2f9cc6bf55b1
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0221 de erro do compilador
Valor constante 'value' não pode ser convertido em um 'type' \(use a sintaxe 'unchecked' para substituir\)  
  
 Foi detectada uma operação de atribuição que resulte na perda de dados por [check](/dotnet/csharp/language-reference/keywords/checked), que é ativado por padrão. Corrija a atribuição ou use [desmarcada](/dotnet/csharp/language-reference/keywords/unchecked) para resolver esse erro. Para obter mais informações, consulte [Contexto verificado e não verificado](/dotnet/csharp/language-reference/keywords/checked-and-unchecked).  
  
 O exemplo a seguir gera CS0221:  
  
```  
// CS0221.cs public class MyClass { public static void Main() { // unchecked // { int a = (int)0xFFFFFFFF;   // CS0221 a++; // } } }  
```