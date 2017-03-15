---
title: "CS1689 de erro do compilador | Microsoft Docs"
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
  - "CS1689"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1689"
ms.assetid: 5fa6e845-40ef-4451-81ee-acbe2665527a
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1689 de erro do compilador
O atributo 'Nome do atributo' só é válido em métodos ou classes de atributo  
  
 Esse erro ocorre apenas com o **ConditionalAttribute** atributo. Como a mensagem informa, esse atributo só pode ser usado em métodos ou classes de atributo. Por exemplo, tentar aplicar esse atributo a uma classe irá gerar esse erro.  
  
## Exemplo  
 O exemplo a seguir gera CS1689.  
  
```  
// CS1689.cs // compile with: /target:library [System.Diagnostics.Conditional("A")]   // CS1689 class MyClass {}  
```