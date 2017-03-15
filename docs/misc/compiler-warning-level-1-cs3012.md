---
title: "Compilador CS3012 de aviso (n&#237;vel 1) | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3012"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3012"
ms.assetid: 1f7555b4-61e4-4821-85c9-586301df4c5c
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS3012 de aviso (n&#237;vel 1)
Não é possível especificar o atributo CLSCompliant em um módulo que difira do atributo CLSCompliant no assembly  
  
 Para que um módulo para ser compatível com o Common Language Specification \(CLS\) por meio de `[module:System.CLCSompliant(true)]`, que deve ser criado com o [\/target: Module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md) opção de compilador. Para obter mais informações sobre a CLS, consulte [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Exemplo  
 O exemplo a seguir, quando compilado sem `/target:module`, gera CS3012:  
  
```  
// CS3012.cs // compile with: /W:1 [module:System.CLSCompliant(true)]   // CS3012 public class C { public static void Main() { } }  
```