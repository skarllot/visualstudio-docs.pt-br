---
title: "Compilador CS0197 de aviso (n&#237;vel 1) | Microsoft Docs"
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
  - "CS0197"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0197"
ms.assetid: 2b5b1b8d-ce13-4bd7-b80a-abb80e9f79ad
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0197 de aviso (n&#237;vel 1)
Passando 'argumento' como ref ou out ou a obtenção de seu endereço pode gerar uma exceção de tempo de execução porque ele é um campo de uma classe de marshaling por referência  
  
 Qualquer classe derivada, direta ou indiretamente, de <xref:System.MarshalByRefObject> é uma classe de marshaling por referência. Essa classe pode ser empacotada por referência entre limites de processo e de máquina. Portanto, as instâncias dessa classe pode ser proxies para objetos remotos. Você não pode passar um campo de um objeto proxy como [ref](/dotnet/csharp/language-reference/keywords/ref) ou [out](/dotnet/csharp/language-reference/keywords/out). Portanto, não é possível passar campos dessa classe como `ref` ou `out`, a menos que a instância é [isso](/dotnet/csharp/language-reference/keywords/this), que não pode ser um objeto proxy.  
  
## Exemplo  
 O exemplo a seguir gera CS0197.  
  
```  
// CS0197.cs // compile with: /W:1 class X : System.MarshalByRefObject { public int i; } class M { public int i; static void AddSeventeen(ref int i) { i += 17; } static void Main() { X x = new X(); x.i = 12; AddSeventeen(ref x.i);   // CS0197 // OK M m = new M(); m.i = 12; AddSeventeen(ref m.i); } }  
```