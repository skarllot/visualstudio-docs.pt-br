---
title: "Compilador CS0109 de aviso (n&#237;vel 4) | Microsoft Docs"
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
  - "CS0109"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0109"
ms.assetid: 42ac72e5-5081-4e8b-b2cf-5e10c1606676
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0109 de aviso (n&#237;vel 4)
O membro 'member' não oculta um membro herdado. A palavra\-chave new não é necessária  
  
 Uma declaração de classe incluída o [novo](/dotnet/csharp/language-reference/keywords/new) palavra\-chave mesmo que a declaração não substitui uma declaração existente em uma classe base. Você pode excluir o **novo** palavra\-chave.  
  
 O exemplo a seguir gera CS0109:  
  
```  
// CS0109.cs // compile with: /W:4 namespace x { public class a { public int i; } public class b : a { public new int i; public new int j;   // CS0109 public static void Main() { } } }  
```