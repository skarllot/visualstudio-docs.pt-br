---
title: "CS1715 de erro do compilador | Microsoft Docs"
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
  - "CS1715"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1715"
ms.assetid: 740044d1-a61c-4156-bc6a-adf26c7499ec
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1715 de erro do compilador
'Type1': o tipo deve ser 'Type2' para coincidir com o membro substituído 'MemberName'  
  
 Esse erro é o mesmo que [CS0508 de erro do compilador](../misc/compiler-error-cs0508.md), exceto que CS0508 agora se aplica apenas aos métodos que têm tipos de retorno, enquanto CS1715 aplica\-se a propriedades e indexadores que têm apenas 'tipos' em vez de 'tipos de retorno'.  
  
## Exemplo  
 O código a seguir gera CS1715.  
  
```  
// CS1715.cs abstract public class Base { abstract public int myProperty { get; set; } } public class Derived : Base { int myField; public override double myProperty  // CS1715 // try the following line instead // public override int myProperty { get { return myField; } set { myField;= value; } } public static void Main() { Derived d = new Derived(); d.myProperty = 5; } }  
```