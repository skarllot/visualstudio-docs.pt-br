---
title: "CS1917 de erro do compilador | Microsoft Docs"
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
  - "CS1917"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1917"
ms.assetid: 05688706-e4b4-4273-9244-48cce1f7f9b9
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1917 de erro do compilador
Membros do campo somente leitura 'name' do tipo 'struct name' não podem ser atribuídos a um inicializador de objeto porque ele é de um tipo de valor.  
  
 Campos somente leitura que são tipos de valor podem ser atribuídos apenas em um construtor.  
  
### Para corrigir este erro  
  
-   Altere a estrutura para um tipo de classe.  
  
-   Inicialize a estrutura com um construtor.  
  
## Exemplo  
 O código a seguir gera CS1917:  
  
```  
// cs1917.cs class CS1917 { public struct TestStruct { public int i; } public class C { public readonly TestStruct str = new TestStruct(); public static int Main() { C c = new C { str = { i = 1 } }; // CS1917 return 0; } } }  
```