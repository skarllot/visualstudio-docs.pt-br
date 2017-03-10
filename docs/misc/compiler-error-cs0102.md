---
title: "CS0102 de erro do compilador | Microsoft Docs"
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
  - "CS0102"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0102"
ms.assetid: c9419779-649f-4c24-b0f3-f0a1be46659e
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0102 de erro do compilador
O tipo 'type name' já contém uma definição para 'Identificador'  
  
 Uma classe contém várias declarações de identificadores com o mesmo nome no mesmo escopo. Para corrigir o erro, renomeie os identificadores duplicados.  
  
## Exemplo  
 O exemplo a seguir gera CS0102.  
  
```  
// CS0102.cs // compile with: /target:library namespace MyApp { public class MyClass { string s = "Hello"; string s = "Goodbye";   // CS0102 public void GetString() { string s = "Hello again";   // method scope, no error } } }  
  
```