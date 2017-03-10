---
title: "CS0418 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "10/01/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0418"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0418"
ms.assetid: b78fafde-428b-4fa2-a933-c4614760bb71
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0418 de erro do compilador
'nome da classe ': uma classe abstrata não pode ser sealed ou static  
  
 Uma classe abstrata não pode ser usada para criar objetos, a menos que ele é derivado, portanto não faz sentido para ser lacrado. Uma classe abstrata significativamente não pode mais ser estática. classes abstratas são projetadas para oferecer suporte a uma hierarquia de objetos que usará a classe abstrata como base.  
  
## Exemplo  
 O exemplo a seguir gera CS0418:  
  
```  
// CS0418.cs public abstract sealed class C  // CS0418 { } sealed static class S  // CS0418 { } public class MyClass { public static void Main() { } }  
```