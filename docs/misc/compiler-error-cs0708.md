---
title: "CS0708 de erro do compilador | Microsoft Docs"
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
  - "CS0708"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0708"
ms.assetid: 19e1907f-b78c-4c8b-b78c-eedfd57115f2
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0708 de erro do compilador
'field': não é possível declarar membros de instância em uma classe estática  
  
 Esse erro ocorre se você declarar um membro não estático em uma classe que é declarado estático. Não é possível criar instâncias de classes estáticas, variáveis de instância não seria significativas. O **estático** palavra\-chave deve ser aplicada a todos os membros de classes estáticas.  
  
 O exemplo a seguir gera CS0708:  
  
```  
// CS0708.cs // compile with: /target:library public static class C { int i;  // CS0708 static int j;  // OK }  
```