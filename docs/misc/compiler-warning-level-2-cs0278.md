---
title: "Compilador CS0278 de aviso (n&#237;vel 2) | Microsoft Docs"
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
  - "CS0278"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0278"
ms.assetid: 5418cbbe-bcec-4379-a6f6-410987beb96a
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0278 de aviso (n&#237;vel 2)
'type' não implementa o padrão de nome do padrão. 'nome do método ' é ambíguo com o nome do método.  
  
 Há várias instruções em c\# que se baseiam em padrões definidos, como `foreach` e `using`. Por exemplo, `foreach` depende da classe de coleção Implementando o padrão "enumerável".  
  
 CS0278 pode ocorrer se o compilador não puder fazer a correspondência devido a ambigüidades. Por exemplo, o padrão "enumerável" exige um método chamado `MoveNext`, e seu código pode conter dois métodos chamados `MoveNext`. O compilador tentará encontrar uma interface para usar, mas é recomendável que você determina e resolver a causa a ambigüidade.  
  
 Para obter mais informações, consulte [Como acessar uma classe de coleção com foreach](../Topic/How%20to:%20Access%20a%20Collection%20Class%20with%20foreach%20\(C%23%20Programming%20Guide\).md).  
  
## Exemplo  
 O exemplo a seguir gera CS0278.  
  
```  
// CS0278.cs using System.Collections.Generic; public class myTest { public static void TestForeach<W>(W w) where W: IEnumerable<int>, IEnumerable<string> { foreach (int i in w) {}   // CS0278 } }  
```