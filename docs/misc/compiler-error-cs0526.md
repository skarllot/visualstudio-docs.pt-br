---
title: "CS0526 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0526"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0526"
ms.assetid: befc46b4-28ea-40d3-89ac-132b92455772
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0526 de erro do compilador
Interfaces não podem conter construtores  
  
 Construtores não podem ser definidos para [interfaces](/dotnet/csharp/language-reference/keywords/interface). Um método é considerado um construtor se ele tem o mesmo nome que a classe e nenhum tipo de retorno.  
  
 O exemplo a seguir gera CS0526:  
  
```  
// CS0526.cs namespace x { public interface clx { public clx()   // CS0526 { } } public class cly { public static void Main() { } } }  
```