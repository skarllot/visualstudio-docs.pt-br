---
title: "CS2019 de erro do compilador | Microsoft Docs"
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
  - "CS2019"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2019"
ms.assetid: eafd2531-8b3a-499c-9e12-a605a011396f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS2019 de erro do compilador
Tipo de destino inválido para \/target: deve especificar 'exe', 'winexe', 'library' ou 'module'  
  
 O [\/destino](/dotnet/csharp/language-reference/compiler-options/target-compiler-option) opção de compilador foi usada, mas um parâmetro inválido foi passado. Para resolver esse erro, recompilar o programa usando a forma do **\/target** opção apropriada ao seu arquivo de saída.  
  
 O exemplo a seguir gera CS2017:  
  
```  
// CS2019.cs // compile with: /target:libra // CS2019 expected class MyClass { }  
```