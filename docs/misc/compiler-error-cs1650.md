---
title: "CS1650 de erro do compilador | Microsoft Docs"
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
  - "CS1650"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1650"
ms.assetid: 251a3a67-6e56-4795-874a-d54610c70595
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1650 de erro do compilador
Campos de somente leitura e estático 'Identificador de campo' não podem ser atribuídos a \(exceto em um construtor estático ou um inicializador de variável\)  
  
 Esse erro ocorre quando você tenta modificar um membro de um campo que é somente leitura e estática onde não é permitida a ser modificado. Para resolver esse erro, limite atribuições aos campos de somente leitura para o construtor ou um inicializador de variável, ou remova o `readonly` palavra\-chave da declaração do campo.  
  
```  
// CS1650.cs public struct Inner { public int i; } class Outer { public static readonly Inner inner = new Inner(); } class D { static void Main() { Outer.inner.i = 1;  // CS1650 } }  
```