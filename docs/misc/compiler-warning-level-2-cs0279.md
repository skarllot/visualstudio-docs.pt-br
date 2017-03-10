---
title: "Compilador CS0279 de aviso (n&#237;vel 2) | Microsoft Docs"
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
  - "CS0279"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0279"
ms.assetid: 5e5faa8f-3d5b-4999-aa62-ff7f131a3e04
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0279 de aviso (n&#237;vel 2)
'type name' não implementa o padrão de nome do padrão. nome do método é estático ou não é público.  
  
 Há várias instruções em c\# que se baseiam em padrões definidos, como `foreach` e `using`. Por exemplo, `foreach` depende da classe de coleção Implementando o padrão de enumerable. Esse erro ocorre quando o compilador é capaz de fazer a correspondência devido a um método que está sendo declarado `static` ou não `public`. Métodos em padrões são necessários para instâncias de classes e público.  
  
## Exemplo  
 O exemplo a seguir gera CS0279:  
  
```  
// CS0279.cs using System; using System.Collections; public class myTest : IEnumerable { IEnumerator IEnumerable.GetEnumerator() { yield return 0; } internal IEnumerator GetEnumerator() { yield return 0; } public static void Main() { foreach (int i in new myTest()) {}  // CS0279 } }  
```