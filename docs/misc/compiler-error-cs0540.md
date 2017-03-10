---
title: "CS0540 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0540"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0540"
ms.assetid: 2da2cd4a-0ff1-45ea-bb72-ea078bc95dea
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0540 de erro do compilador
'membro de interface ': contendo o tipo não implementa a interface 'interface'  
  
 Você tentou implementar um membro de interface em um [classe](/dotnet/csharp/language-reference/keywords/class) que derivam o [interface](/dotnet/csharp/language-reference/keywords/interface). Você deve excluir a implementação do membro da interface ou adicionar a interface para a lista de classe base da classe.  
  
## Exemplo  
 O exemplo a seguir gera CS0540.  
  
```  
// CS0540.cs interface I { void m(); } public class Clx { void I.m() {}   // CS0540 } // OK public class Cly : I { void I.m() {} public static void Main() {} }  
```  
  
## Exemplo  
 O exemplo a seguir gera CS0540.  
  
```  
// CS0540_b.cs using System; class C { void IDisposable.Dispose() {}   // CS0540 } class D : IDisposable { void IDisposable.Dispose() {} public void Dispose() {} static void Main() { using (D d = new D()) {} } }  
```