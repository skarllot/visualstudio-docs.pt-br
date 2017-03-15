---
title: "CS0441 de erro do compilador | Microsoft Docs"
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
  - "CS0441"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0441"
ms.assetid: 3f07500a-d479-424c-a0f4-c219be1b5a45
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0441 de erro do compilador
'class': uma classe não pode ser estático e sealed  
  
 Esse erro ocorre quando você declarar uma classe que é estático e sealed. Classes estáticas são inerentemente bloqueados, portanto o modificador lacrado não é necessário. Para resolver, use apenas um modificador.  
  
 O exemplo a seguir gera CS0441:  
  
```  
// CS0441.cs sealed static class MyClass { }   // CS0441  
```