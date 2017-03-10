---
title: "CS0126 de erro do compilador | Microsoft Docs"
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
  - "CS0126"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0126"
ms.assetid: 15fb0f38-ac9d-4c09-a69f-398a4903d790
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0126 de erro do compilador
Um objeto de tipo conversível em 'type' é necessário  
  
 Uma instrução de retorno está presente, mas a instrução não retorna um valor do tipo esperado. Para obter mais informações, consulte [Propriedades](/dotnet/csharp/programming-guide/classes-and-structs/properties).  
  
 O exemplo a seguir gera CS0126:  
  
```  
// CS0126.cs public class a { public int i { set { } get { return;   // CS0126, specify a value to return } } }  
```