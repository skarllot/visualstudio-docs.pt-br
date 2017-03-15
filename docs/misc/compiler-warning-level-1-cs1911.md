---
title: "Compilador CS1911 de aviso (n&#237;vel 1) | Microsoft Docs"
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
  - "CS1911"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1911"
ms.assetid: 95e8a7a0-1c19-4930-a7e9-3ae4060e97d3
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS1911 de aviso (n&#237;vel 1)
O acesso ao membro 'name' por meio de uma palavra\-chave 'base' de um método anônimo, expressão lambda, expressão de consulta ou iterador resulta em código não verificado. Considere mover o acesso para um método auxiliar no tipo recipiente.  
  
 Chamando funções virtuais com o `base` palavra\-chave dentro do corpo do método de um iterador ou métodos anônimos resulta em código não verificado. Código não funcionará em um ambiente de confiança parcial.  
  
 Uma resolução para CS1911 é mover a chamada de função virtual para uma função auxiliar.  
  
## Exemplo  
 O exemplo a seguir gera CS1911.  
  
```  
// CS1911.cs // compile with: /W:1 using System; delegate void D(); delegate D RetD(); class B { protected virtual void M() { Console.WriteLine("B.M"); } } class Der : B { protected override void M() { Console.WriteLine("D.M"); } void Test() { base.M(); } D Test2() { return new D(base.M); } public D CallBaseM() { return delegate () { base.M(); };   // CS1911 // try the following line instead // return delegate () { Test(); }; } public RetD DelToBaseM() { return delegate () { return new D(base.M); };   // CS1911 // try the following line instead // return delegate () { return Test2(); }; } } class Program { public static void Main() { Der der = new Der(); D d = der.CallBaseM(); d(); RetD rd = der.DelToBaseM(); rd()(); } }  
```