---
title: "CS1667 de erro do compilador | Microsoft Docs"
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
  - "CS1667"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1667"
ms.assetid: 59f64828-58bc-487c-862a-75537e21d4ea
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1667 de erro do compilador
O atributo 'attribute' não é válido em acessadores de propriedade ou evento. É válido em declarações de 'tipo de declaração' somente.  
  
 Esse erro ocorre se você usar um atributo em um acessador de propriedade ou evento, quando deveria estar na propriedade ou evento propriamente dito. Esse erro pode ocorrer com os atributos <xref:System.CLSCompliantAttribute>, <xref:System.Diagnostics.ConditionalAttribute>, e <xref:System.ObsoleteAttribute>.  
  
## Exemplo  
 O exemplo a seguir gera CS1670:  
  
```  
// CS1667.cs using System; public class C { private int i; //Try this instead: //[Obsolete] public int ObsoleteProperty { [Obsolete]  // CS1667 get { return i; } set { i = value; } } public static void Main() { } }  
```