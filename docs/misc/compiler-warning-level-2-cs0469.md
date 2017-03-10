---
title: "Compilador CS0469 de aviso (n&#237;vel 2) | Microsoft Docs"
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
  - "CS0469"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0469"
ms.assetid: 773925ce-a8b2-4098-9ead-b96197442848
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0469 de aviso (n&#237;vel 2)
O valor 'goto case' não é implicitamente conversível no tipo 'type'  
  
 Quando você usa `goto case`, deve haver uma conversão implícita do valor do caso goto para o tipo de comutador.  
  
## Exemplo  
 O exemplo a seguir gera CS0469.  
  
```  
// CS0469.cs // compile with: /W:2 class Test { static void Main() { char c = (char)180; switch (c) { case (char)127: break; case (char)180: goto case 127;   // CS0469 // try the following line instead // goto case (char) 127; } } }  
```