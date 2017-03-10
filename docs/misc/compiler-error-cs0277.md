---
title: "CS0277 de erro do compilador | Microsoft Docs"
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
  - "CS0277"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0277"
ms.assetid: 8abec3eb-4d4c-4aab-87cc-d0444ab23535
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0277 de erro do compilador
'class' não implementa o acessador' membro de interface'. 'classe acessador' não é público  
  
 Esse erro ocorre quando você tenta implementar uma propriedade de uma interface, mas a implementação do acessador de propriedade na classe não é pública. Métodos que implementam membros de interface precisam ter acessibilidade pública. Para resolver, remova o modificador de acesso no acessador de propriedade.  
  
## Exemplo  
 O exemplo a seguir gera CS0277:  
  
```  
// CS0277.cs public interface MyInterface { int Property { get; set; } } public class MyClass : MyInterface   // CS0277 { public int Property { get { return 0; } // Try this instead: //set { } protected set { } } }  
```