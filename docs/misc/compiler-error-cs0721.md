---
title: "CS0721 de erro do compilador | Microsoft Docs"
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
  - "CS0721"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0721"
ms.assetid: 7ab8591d-df8a-440c-80d6-61b438a935fd
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0721 de erro do compilador
'type': tipos static não podem ser usados como parâmetros  
  
 Um tipo estático não faz sentido como um parâmetro. Uma vez que não há instâncias de tipos estáticos podem ser criadas, nenhuma instância nunca pode ser passada como um parâmetro.  
  
 O exemplo a seguir gera CS0721:  
  
```  
// CS0721.cs public static class SC { } public class CMain { public void F(SC sc)  // CS0721 { } public static void Main() { } }  
```