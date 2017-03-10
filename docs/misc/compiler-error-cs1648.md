---
title: "CS1648 de erro do compilador | Microsoft Docs"
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
  - "CS1648"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1648"
ms.assetid: 5cf1bc84-cd18-4df2-942f-1cc17eabacd6
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1648 de erro do compilador
Membros de somente leitura 'Identificador de campo' não podem ser modificados \(exceto em um construtor ou um inicializador de variável\)  
  
 Esse erro ocorre quando você tenta modificar um membro de um campo que é somente leitura em que não é permitido a ser modificado. Para resolver esse erro, limite atribuições aos campos de somente leitura para o construtor ou um inicializador de variável, ou remova a palavra\-chave readonly da declaração do campo.  
  
 O exemplo a seguir gera CS1648:  
  
```  
// CS1648.cs public struct Inner { public int i; } class Outer { public readonly Inner inner = new Inner(); } class D { static void Main() { Outer outer = new Outer(); outer.inner.i = 1;  // CS1648 } }  
```