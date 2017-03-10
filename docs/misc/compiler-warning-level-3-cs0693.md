---
title: "Compilador CS0693 de aviso (n&#237;vel 3) | Microsoft Docs"
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
  - "CS0693"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0693"
ms.assetid: a3902336-49db-4808-b41f-8f0936bff53a
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0693 de aviso (n&#237;vel 3)
Parâmetro de tipo ' tipo ' tem o mesmo nome que o parâmetro de tipo do tipo externo 'type'  
  
 Esse erro ocorre quando você tem um membro genérico como um método dentro de uma classe genérica. Como o parâmetro de tipo do método não é necessariamente o mesmo parâmetro de tipo da classe, você não pode lhe fornecer o mesmo nome. Para obter mais informações, consulte [Métodos genéricos](/dotnet/csharp/programming-guide/generics/generic-methods).  
  
 Para evitar essa situação, use um nome diferente para um dos parâmetros de tipo.  
  
## Exemplo  
 O exemplo a seguir gera CS0693.  
  
```  
// CS0693.cs // compile with: /W:3 /target:library class Outer<T> { class Inner<T> {}   // CS0693 // try the following line instead // class Inner<U> {} }  
```