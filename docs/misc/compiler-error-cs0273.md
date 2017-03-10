---
title: "CS0273 de erro do compilador | Microsoft Docs"
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
  - "CS0273"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0273"
ms.assetid: 851ad056-feee-48fd-834c-578a1a13e926
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0273 de erro do compilador
O modificador de acessibilidade do acessador 'property\_accessor' deve ser mais restritivo que a propriedade ou indexador 'propriedade'  
  
 O modificador de acessibilidade do acessador get\/set deve ser mais restritivo que a propriedade ou o indexador 'propriedade\/indexador'  
  
 Esse erro ocorre quando você declarar uma propriedade ou indexador com um modificador de acesso que é menos restritivo que o modificador de acesso em um de seus acessadores. Para resolver esse erro, use o modificador de acesso apropriado a propriedade ou o acessador set. Para obter mais informações, consulte [acessibilidade do acessador](/dotnet/csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility).  
  
## Exemplo  
 Este exemplo contém uma propriedade interna com um método de conjunto interno. O exemplo a seguir gera CS0273.  
  
```  
// CS0273.cs // compile with: /target:library public class MyClass { internal int Property { get { return 0; } internal set {}   // CS0273 // try the following line instead // private set {} } }  
```