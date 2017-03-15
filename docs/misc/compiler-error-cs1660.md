---
title: "CS1660 de erro do compilador | Microsoft Docs"
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
  - "CS1660"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1660"
ms.assetid: ae7fede3-471b-4e20-97a7-b80fdc2bb080
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1660 de erro do compilador
Não é possível converter bloco de métodos anônimo para o tipo 'type' porque ele não é um tipo delegado  
  
 Esse erro ocorre se você tentar atribuir ou caso contrário, converta um bloco de método anônimo para um tipo que não é um tipo delegado.  
  
 O exemplo a seguir gera CS1660:  
  
```  
// CS1660.cs delegate int MyDelegate(); class C { static void Main() { int i = delegate { return 1; };  // CS1660 // Try this instead: // MyDelegate myDelegate = delegate { return 1; }; // int i = myDelegate(); } }  
```