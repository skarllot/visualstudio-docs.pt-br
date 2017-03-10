---
title: "CS0689 de erro do compilador | Microsoft Docs"
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
  - "CS0689"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0689"
ms.assetid: 5c555c2e-8e71-4097-8dbf-52dbafe7bf57
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0689 de erro do compilador
Não é possível derivar de 'identifier' porque ele é um parâmetro de tipo  
  
 Classes base ou interfaces para classes genéricas não podem ser especificados por um parâmetro de tipo. Derivar de uma classe específica ou interface ou uma classe genérica específica em vez disso, ou incluir o tipo como um membro desconhecido.  
  
 O exemplo a seguir gera CS0689:  
  
```  
// CS0689.cs class A<T> : T   // CS0689 { }  
```