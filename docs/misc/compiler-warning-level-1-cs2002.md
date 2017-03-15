---
title: "Compilador CS2002 de aviso (n&#237;vel 1) | Microsoft Docs"
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
  - "CS2002"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2002"
ms.assetid: 4acd054e-d3fe-4be6-a660-53a0a5e8c6a4
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS2002 de aviso (n&#237;vel 1)
Arquivo de origem 'arquivo' especificado várias vezes  
  
 Um nome de arquivo de origem foi passado para o compilador mais de uma vez. Você só pode especificar um arquivo de uma vez para o compilador para criar um arquivo de saída.  
  
 Esse aviso não pode ser suprimido pelo [\/nowarn](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option) opção.  
  
 O exemplo a seguir gera CS2002:  
  
```  
// CS2002.cs // compile with: CS2002.cs public class A { public static void Main(){} }  
```  
  
 Para gerar o erro, compile o exemplo com a linha de comando:  
  
```  
csc CS2002.cs CS2002.cs  
```