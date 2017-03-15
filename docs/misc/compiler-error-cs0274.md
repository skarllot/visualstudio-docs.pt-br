---
title: "CS0274 de erro do compilador | Microsoft Docs"
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
  - "CS0274"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0274"
ms.assetid: bbd2d64e-a756-4713-b9ed-711d50b65e00
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0274 de erro do compilador
Não é possível especificar modificadores de acessibilidade para os acessadores da propriedade ou indexador 'propriedade\/indexador'  
  
 Esse erro ocorre quando você declara uma propriedade ou indexador com modificadores de acesso em ambos os seus acessadores. Para resolver esse erro, use um modificador de acesso em apenas um dos acessadores de dois. Para obter mais informações, consulte [acessibilidade do acessador](/dotnet/csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility).  
  
 O exemplo a seguir gera CS0274:  
  
```  
// CS0274.cs public class MyClass { public int Property   // CS0274 { public get { return 0; } protected set { } } }  
```