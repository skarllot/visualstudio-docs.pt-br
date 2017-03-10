---
title: "CS0842 de erro do compilador | Microsoft Docs"
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
  - "CS0842"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0842"
ms.assetid: 93a8b333-efc4-40c7-ae53-5264f721a74f
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0842 de erro do compilador
Propriedades implementadas automaticamente não podem ser usadas dentro de um tipo marcado com StructLayout\(LayoutKind.Explicit\).  
  
 Propriedades autoimplementadas tem seus campos de backup fornecidos pelo compilador e o campo não está acessível ao código\-fonte. Portanto, eles não são compatíveis com <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>.  
  
### Para corrigir este erro  
  
1.  Verifique a propriedade de uma propriedade comum em que você fornecer os corpos de acessador.  
  
## Exemplo  
 O exemplo a seguir gera CS0842:  
  
```  
// cs0842.cs using System; using System.Runtime.InteropServices; namespace TestNamespace { [StructLayout(LayoutKind.Explicit)] struct Str { public int Num // CS0842 { get; set; } static int Main() { return 1; } } }  
```