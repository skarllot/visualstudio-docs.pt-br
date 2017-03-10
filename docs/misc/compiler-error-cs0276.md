---
title: "CS0276 de erro do compilador | Microsoft Docs"
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
  - "CS0276"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0276"
ms.assetid: 0c49017f-c7a9-42a5-9d0a-6f1d82142bd7
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0276 de erro do compilador
' propriedade\/indexador': modificadores de acessibilidade nos acessadores só podem ser usados se a propriedade ou o indexador tiver um get e um acessador set  
  
 Esse erro ocorre quando você declara uma propriedade ou indexador com apenas um acessador e usa um modificador de acesso do acessador. Para resolver, remova o modificador de acesso ou adicione outro acessador.  
  
## Exemplo  
 O exemplo a seguir gera CS0276:  
  
```  
// CS0276.cs public class MyClass { public int Property { protected set { }   // CS0276 } public int Property2 { internal get { }   // CS0276 } }  
```