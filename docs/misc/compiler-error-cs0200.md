---
title: "CS0200 de erro do compilador | Microsoft Docs"
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
  - "CS0200"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0200"
ms.assetid: 1990704a-edfa-4dbd-8477-d9c7aae58c96
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0200 de erro do compilador
Propriedade ou indexador 'propriedade' não pode ser atribuída a — ele é somente leitura  
  
 Foi feita uma tentativa para atribuir um valor para um [propriedade](/dotnet/csharp/programming-guide/classes-and-structs/using-properties), mas a propriedade não tem um acessador set. Resolva o erro adicionando um acessador set. Para obter mais informações, consulte [Como: declarar e usar propriedades de gravação de leitura](../Topic/How%20to:%20Declare%20and%20Use%20Read%20Write%20Properties%20\(C%23%20Programming%20Guide\).md).  
  
## Exemplo  
 O exemplo a seguir gera CS0200:  
  
```  
// CS0200.cs public class MainClass { // private int _mi; int I { get { return 1; } // uncomment the set accessor and declaration for _mi /* set { _mi = value; } */ } public static void Main () { MainClass II = new MainClass(); II.I = 9;   // CS0200 } }  
```