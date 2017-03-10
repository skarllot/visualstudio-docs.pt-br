---
title: "Compilador CS0402 de aviso (n&#237;vel 4) | Microsoft Docs"
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
  - "CS0402"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0402"
ms.assetid: 5a252c95-18c7-4569-bae0-e1f7b582cf6a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0402 de aviso (n&#237;vel 4)
'identifier': um ponto de entrada não pode ser genérico ou em um tipo genérico  
  
 O ponto de entrada foi encontrado em um tipo genérico. Para remover esse aviso, implemente principal em uma classe não\-genérica ou estrutura.  
  
```  
// CS0402.cs // compile with: /W:4 class C<T> { public static void Main()  // CS0402 { } } class CMain { public static void Main() {} }  
```