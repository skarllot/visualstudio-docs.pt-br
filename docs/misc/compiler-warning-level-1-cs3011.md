---
title: "Compilador CS3011 de aviso (n&#237;vel 1) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3011"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3011"
ms.assetid: e27ce521-0147-488b-b4a1-1b6fb5168661
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS3011 de aviso (n&#237;vel 1)
'member': somente membros compatíveis com CLS podem ser abstratos  
  
 Um membro de classe não pode ser [abstrato](/dotnet/csharp/language-reference/keywords/abstract) e não compatíveis com o Common Language Specification \(CLS\). A CLS Especifica que todos os membros de classe devem ser implementados. Para obter mais informações sobre compatibilidade CLS, consulte [Escrevendo código compatível com CLS](http://msdn.microsoft.com/pt-br/4c705105-69a2-4e5e-b24e-0633bc32c7f3) e [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Exemplo  
 O exemplo a seguir gera CS3011:  
  
```  
// CS3011.cs using System; [assembly:CLSCompliant(true)] public abstract class I { [CLSCompliant(false)] public abstract int M();   // CS3011 // OK [CLSCompliant(false)] public void M2() { } } public class C : I { public override int M() { return 1; } public static void Main() { } }  
```