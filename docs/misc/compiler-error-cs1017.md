---
title: "CS1017 de erro do compilador | Microsoft Docs"
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
  - "CS1017"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1017"
ms.assetid: e0902e8a-b042-4711-a8a6-83456a3f88cb
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1017 de erro do compilador
Cláusulas catch não podem seguir a cláusula catch geral de uma instrução try  
  
 Um `catch` bloco que não tem nenhum parâmetro deve ser o último de uma série de `catch` blocos. Para obter mais informações sobre exceções, consulte [Instruções para manipulação de exceções](/dotnet/csharp/language-reference/keywords/exception-handling-statements).  
  
## Exemplo  
 O exemplo a seguir gera CS1017:  
  
```  
// CS1017.cs using System; namespace x { public class b : Exception { } public class a { public static void Main() { try { } catch   // CS1017, must be last catch { } catch(b) { throw; } } } }  
```