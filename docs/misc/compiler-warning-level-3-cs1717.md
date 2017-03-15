---
title: "Compilador CS1717 de aviso (n&#237;vel 3) | Microsoft Docs"
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
  - "CS1717"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1717"
ms.assetid: 5b150a2c-5d61-4cd8-b4d4-e6c2b93b52c6
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS1717 de aviso (n&#237;vel 3)
Atribuição feita à mesma variável. Você pretendia atribuir outro elemento?  
  
 Este aviso ocorre quando você atribuir uma variável a mesmo, como `a = a`.  
  
 Vários erros comuns podem gerar esse aviso:  
  
-   Gravando `a = a` como a condição de uma **if** instrução, como `if (a = a)`. Provavelmente você queria dizer `if (a == a)`, que é sempre verdadeiro, portanto você pode escrever isso mais forma concisa como `if (true)`.  
  
-   Erros de digitação. Provavelmente você queria dizer `a = b`.  
  
-   Em um construtor onde o parâmetro tem o mesmo nome do campo, não usando o **this** palavra\-chave: provavelmente você queria dizer `this.a = a`.  
  
## Exemplo  
 O exemplo a seguir gera CS1717.  
  
```  
// CS1717.cs // compile with: /W:3 public class Test { public static void Main() { int x = 0; x = x;   // CS1717 } }  
```