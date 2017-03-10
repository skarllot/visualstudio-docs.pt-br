---
title: "CS1725 de erro do compilador | Microsoft Docs"
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
  - "cs1725"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1725"
ms.assetid: baef9ae3-b036-41d6-972c-9f3cdae1e8bd
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1725 de erro do compilador
Referência de assembly Friend 'referência' é inválida. Declarações InternalsVisibleTo não podem ter uma versão, cultura, token de chave pública ou arquitetura de processador especificada.  
  
 Você não pode adicionar uma cultura de versão em uma referência de assembly friend. Classes parciais devem ser visíveis aos assemblies amigáveis.  
  
## Exemplo  
 O exemplo a seguir gera CS1725.  
  
```  
// CS1725.cs // compile with: /target:library using System.Runtime.CompilerServices; [assembly:InternalsVisibleTo("partial01,version=1.1.0.0")]   // CS1725 // try the following line instead // [assembly:InternalsVisibleTo("partial01")] partial class TestClass { public static string strBar = "my string"; }  
```  
  
## Consulte também  
 [Como criar assemblies amigáveis assinados](../Topic/How%20to:%20Create%20Signed%20Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)