---
title: "CS0617 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0617"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0617"
ms.assetid: a4363709-9846-4cb8-8772-f5a3ea8555ca
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0617 de erro do compilador
'referência' não é um argumento de atributo nomeado válido porque não é um tipo de parâmetro de atributo válido  
  
 Foi feita uma tentativa para acessar um [particular](/dotnet/csharp/language-reference/keywords/private) membro de uma classe de atributo.  
  
## Exemplo  
 O exemplo a seguir gera CS0617.  
  
```  
// CS0617.cs using System; [AttributeUsage(AttributeTargets.Struct | AttributeTargets.Class | AttributeTargets.Interface)] public class MyClass : Attribute { public int Name; public MyClass (int sName) { Name = sName; Bad = -1; Bad2 = -1; } public readonly int Bad; public int Bad2; } [MyClass(5, Bad=0)] class Class1 {}   // CS0617 [MyClass(5, Bad2=0)] class Class2 {}  
```