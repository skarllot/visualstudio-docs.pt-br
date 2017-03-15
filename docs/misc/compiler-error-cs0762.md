---
title: "CS0762 de erro do compilador | Microsoft Docs"
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
  - "CS0762"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0762"
ms.assetid: 7cedd1af-ffe6-4ca7-82fb-faa9e98014a4
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0762 de erro do compilador
Não é possível criar o representante do método 'method' porque ele é um método parcial sem uma declaração de implementação  
  
 Um método parcial não é necessário ter uma declaração de implementação. No entanto, um delegado requer que seu método encapsulado tenham uma implementação.  
  
### Para corrigir este erro  
  
1.  Fornece uma implementação para o método que é usado para inicializar o delegado.  
  
## Exemplo  
  
```  
public delegate void TestDel(); public partial class C { partial void Part(); public static int Main() { C c = new C(); TestDel td = new TestDel(c.Part); // CS0762 return 1; } }  
```