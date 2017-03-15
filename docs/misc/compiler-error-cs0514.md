---
title: "CS0514 de erro do compilador | Microsoft Docs"
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
  - "CS0514"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0514"
ms.assetid: 74ce3010-f9e9-458c-8b68-cfb908a3e7a2
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0514 de erro do compilador
'construtor': construtor estático não pode ter uma explícita 'this' ou 'base' chamada de construtor  
  
 Chamando `this` no construtor estático não é permitida porque o construtor estático é chamado automaticamente antes de criar qualquer instância da classe. Além disso, os construtores estáticos não são herdados e não podem ser chamados diretamente.  
  
 Para obter mais informações, consulte [this](/dotnet/csharp/language-reference/keywords/this) e [base](/dotnet/csharp/language-reference/keywords/base).  
  
## Exemplo  
 O exemplo a seguir gera CS0514:  
  
```  
// CS0514.cs class A { static A() : base(0) // CS0514 { } public A(object o) { } } class B { static B() : this(null) // CS0514 { } public B(object o) { } }  
```