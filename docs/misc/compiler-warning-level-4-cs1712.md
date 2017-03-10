---
title: "Compilador CS1712 de aviso (n&#237;vel 4) | Microsoft Docs"
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
  - "CS1712"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1712"
ms.assetid: d9a8be26-c0ba-41fa-b082-1ce4ba7724b7
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS1712 de aviso (n&#237;vel 4)
Parâmetro de tipo ' tipo ' não tem nenhuma marca typeparam correspondente no comentário XML em 'type' \(mas outros parâmetros de tipo têm\)  
  
 A documentação de um tipo genérico está falta um **typeparam** marca. Para obter mais informações, consulte [\<typeparam\>](../Topic/%3Ctypeparam%3E%20\(C%23%20Programming%20Guide\).md).  
  
## Exemplo  
 O código a seguir gera um aviso CS1712. Para resolver esse erro, adicione um **typeparam** marca para o parâmetro de tipo S.  
  
```  
// CS1712.cs // compile with: /doc:cs1712.xml using System; class Test { public static void Main() {} /// <param name="j"> This is the j parameter.</param> /// <typeparam name="T"> This is the T type parameter.</typeparam> public void bar<T,S>(int j) {}  // CS1712 }  
```