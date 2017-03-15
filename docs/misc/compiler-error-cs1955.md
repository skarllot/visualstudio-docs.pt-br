---
title: "CS1955 de erro do compilador | Microsoft Docs"
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
  - "CS1955"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1955"
ms.assetid: 38a8542d-da53-4739-b807-46c8c077363c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1955 de erro do compilador
O membro não invocável 'name' não pode ser usado como um método.  
  
 Apenas delegados e métodos podem ser chamados. Esse erro é gerado quando você tenta usar parênteses vazios para chamar algo diferente de um método ou delegar.  
  
### Para corrigir este erro  
  
1.  Remova os parênteses da expressão.  
  
## Exemplo  
 O código a seguir gera CS1955 porque o código está tentando invocar um campo e uma propriedade usando o operador de chamada de método [\(\)](/dotnet/csharp/language-reference/operators/invocation-operator). Você não pode chamar uma propriedade ou campo, mas você pode acessar o valor que ele armazena usando o operador de acesso de membro \( [.](/dotnet/csharp/language-reference/operators/member-access-operator) \).  
  
```  
// cs1955.cs class A { public int x = 0; public int X { get { return x; } set { x = value; } } } class Test { static int Main() { A a = new A(); a.x(); // CS1955 a.X(); // CS1955 // Try this line instead: // int num = a.x; } }  
```