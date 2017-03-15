---
title: "CS0694 de erro do compilador | Microsoft Docs"
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
  - "CS0694"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0694"
ms.assetid: 048615e4-4599-4726-b5db-55322ccc936f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0694 de erro do compilador
O parâmetro de tipo 'identifier' tem o mesmo nome do tipo recipiente ou do método  
  
 Você deve usar um nome diferente para o parâmetro de tipo como nome do parâmetro de tipo não pode ser idêntico ao nome do tipo ou método que contém o parâmetro de tipo.  
  
## Exemplo  
 O exemplo a seguir gera CS0694.  
  
```  
// CS0694.cs // compile with: /target:library class C<C> {}   // CS0694  
```  
  
## Exemplo  
 Além de caso acima que envolvem uma classe genérica, esse erro pode ocorrer com um método:  
  
```  
// CS0694_2.cs // compile with: /target:library class A { public void F<F>(F arg);   // CS0694 }  
```