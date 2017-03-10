---
title: "CS0746 de erro do compilador | Microsoft Docs"
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
  - "CS0746"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0746"
ms.assetid: 36baf7f2-b092-422c-ab53-95154bfceb0a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0746 de erro do compilador
Declarador de membro de tipo anônimo inválido. Membros de tipo anônimo devem ser declarados com uma atribuição de membro, nome simples ou acesso de membro.  
  
 Um tipo anônimo deve ser declarado com uma atribuição de membro, nome simples ou acesso de membro.  
  
### Para corrigir este erro  
  
1.  Certifique\-se de que sua declaração usa apenas atribuição de membro, os nomes simples ou expressões de acesso de membro.  
  
## Exemplo  
 O código a seguir gera CS0746 na declaração de `incorrect_1` e `incorrect_2`. As declarações a seguir mostram duas maneiras para declarar um tipo anônimo corretas.  
  
```  
// cs0746.cs public class C { public static int Main() { int i = 100; string s = "Bottles of beer."; var incorrect_1 = new { a.b = 1 }; // CS0746 var incorrect_2 = new {100, "Bottles of beer."}; // CS0746 var correct_1 = new { i, s }; //OK var correct_2 = new {num = i, message = s}; // OK return 1; } }  
  
```  
  
## Consulte também  
 [Tipos anônimos](/dotnet/csharp/programming-guide/classes-and-structs/anonymous-types)