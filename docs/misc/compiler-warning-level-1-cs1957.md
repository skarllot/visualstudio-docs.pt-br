---
title: "Compilador CS1957 de aviso (n&#237;vel 1) | Microsoft Docs"
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
  - "CS1957"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1957"
ms.assetid: a4823211-52ce-4ffa-b19b-ee874069409f
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS1957 de aviso (n&#237;vel 1)
Membro 'name' substitui 'method'. Há vários candidatos à substituição em tempo de execução. É o método será chamado depende da implementação.  
  
 Parâmetros de método que variam apenas pelo sejam `ref` ou `out` não podem ser diferenciados em tempo de execução.  
  
### Para evitar esse aviso  
  
1.  Dê um dos métodos a um nome diferente ou um número diferente de parâmetros.  
  
## Exemplo  
 O código a seguir gera CS1957:  
  
```  
// cs1957.cs class Base<T, S> { public virtual string Test(out T x) // CS1957 { x = default(T); return "Base.Test"; } public virtual void Test(ref S x) { } } class Derived : Base<int, int> { public override string Test(out int x) { x = 0; return "Derived.Test"; } static int Main() { int x; if (new Derived().Test(out x) == "Derived.Test") return 0; return 1; } }  
```