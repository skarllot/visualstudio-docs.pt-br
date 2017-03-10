---
title: "Compilador CS1573 de aviso (n&#237;vel 4) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1573"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1573"
ms.assetid: 1b68cb1a-9bfd-4343-b9b6-8ce195af5e23
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS1573 de aviso (n&#237;vel 4)
Parâmetro '' não tem nenhuma marca param correspondente no comentário XML para 'parameter' \(mas outros parâmetros têm\)  
  
 Ao usar o [\/doc](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option) opção de compilador, um comentário foi especificado para alguns, mas nem todos os parâmetros em um método. Você pode ter esquecido de digitar um comentário para esses parâmetros.  
  
 O exemplo a seguir gera CS1573:  
  
```  
// CS1573.cs // compile with: /W:4 public class MyClass { /// <param name='Int1'>Used to indicate status.</param> // enter a comment for Char1? public static void MyMethod(int Int1, char Char1) { } public static void Main () { } }  
```