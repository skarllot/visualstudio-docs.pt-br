---
title: "CS0123 de erro do compilador | Microsoft Docs"
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
  - "CS0123"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0123"
ms.assetid: 57be2c58-6d87-40af-9376-cd7f91023044
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0123 de erro do compilador
Nenhuma sobrecarga para 'method' corresponde ao delegate 'delegate'  
  
 Falha ao tentar criar um delegado porque a assinatura correta não foi usada. Instâncias de um delegado devem ser declaradas com a mesma assinatura que a declaração do delegado.  
  
 Você pode resolver esse erro, ajustando o método ou delegar a assinatura. Para obter mais informações, consulte [Delegados](/dotnet/csharp/programming-guide/delegates/index).  
  
 O exemplo a seguir gera CS0123.  
  
```  
// CS0123.cs delegate void D(); delegate void D2(int i); public class C { public static void f(int i) {} public static void Main() { D d = new D(f);   // CS0123 D2 d2 = new D2(f);   // OK } }  
```