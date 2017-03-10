---
title: "CS0275 de erro do compilador | Microsoft Docs"
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
  - "CS0275"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0275"
ms.assetid: 4d59f11c-b0ea-4c91-b2cb-cbe3be9a9ba2
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0275 de erro do compilador
'o acessador': modificadores de acessibilidade não podem ser usados nos acessadores em uma interface  
  
 Esse erro ocorre quando você usa um modificador de acesso em qualquer um dos acessadores de uma propriedade ou indexador em uma interface. Para resolver, remova o modificador de acesso.  
  
## Exemplo  
 O exemplo a seguir gera CS0275:  
  
```  
// CS0275.cs public interface MyInterface { int Property { get; internal set;   // CS0275 } }  
```