---
title: "CS0717 de erro do compilador | Microsoft Docs"
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
  - "CS0717"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0717"
ms.assetid: 1976e82a-d048-4f13-a95a-a7f4e3cd7038
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0717 de erro do compilador
'classe estática': classes estáticas não podem ser usados como restrições  
  
 Classes static não podem ser estendidas como conter apenas membros estáticos e não os membros de instância. Porque eles não podem ser estendidos, isso os torna inútil como parâmetros de tipo e restrições, pois nenhum tipo pode existir é uma especialização de uma classe estática.  
  
## Exemplo  
 O exemplo a seguir gera CS0717:  
  
```  
// CS0717.cs public static class SC { public static void F() { } } public class G<T> where T : SC  // CS0717 { public static void Main() { } }  
```