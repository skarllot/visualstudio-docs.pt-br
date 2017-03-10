---
title: "Compilador CS0419 de aviso (n&#237;vel 3) | Microsoft Docs"
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
  - "CS0419"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0419"
ms.assetid: de439ad5-422f-4ed6-96d6-69dade29c7b2
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0419 de aviso (n&#237;vel 3)
Referência ambígua no atributo cref: 'Método Nome1'.  Supondo que 'Método nome2', mas poderia também coincida com outras sobrecargas incluindo 'Método nome3'.  
  
 Em um comentário de documentação XML no código, uma referência não pôde ser resolvida. Isso pode ocorrer se o método está sobrecarregado ou se encontram\-se dois identificadores diferentes com o mesmo nome. Para resolver o aviso, use um nome qualificado para resolver a ambiguidade de referência ou incluir sobrecarga específica entre parênteses.  
  
 O exemplo a seguir gera CS0419.  
  
```  
// cs0419.cs // compile with: /doc:x.xml /W:3 interface I { /// text for F(void) void F(); /// text for F(int) void F(int i); } /// text for class MyClass public class MyClass { /// <see cref="I.F"/> public static void MyMethod(int i) { } /* Try this instead: /// <see cref="I.F(int)"/> public static void MyMethod(int i) { } */ /// text for Main public static void Main () { } }  
```