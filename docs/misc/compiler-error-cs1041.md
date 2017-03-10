---
title: "CS1041 de erro do compilador | Microsoft Docs"
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
  - "CS1041"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1041"
ms.assetid: 9f62c058-cd28-4cb5-835c-d0f25f4fd08e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1041 de erro do compilador
Identificador esperado 'palavra\-chave' é uma palavra\-chave  
  
 Uma palavra reservada para a linguagem c\# foi encontrada onde era esperado um identificador. Substitua o [palavra\-chave](/dotnet/csharp/language-reference/keywords/index) com um identificador especificado pelo usuário.  
  
## Exemplo  
 O exemplo a seguir gera CS1041:  
  
```  
// CS1041a.cs class MyClass { public void f(int long)   // CS1041 // Try the following instead: // public void f(int i) { } public static void Main() { } }  
```  
  
## Exemplo  
 Quando você estiver importando de outra linguagem de programação que não tem o mesmo conjunto de palavras reservadas, você pode modificar o identificador reservado com o prefixo @, como demonstrado no exemplo a seguir.  
  
 Um identificador com um `@` prefixo é chamado um identificador textual.  
  
```  
// CS1041b.cs class MyClass { public void f(int long)   // CS1041 // Try the following instead: // public void f(int @long) { } public static void Main() { } }  
```