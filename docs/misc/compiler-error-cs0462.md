---
title: "CS0462 de erro do compilador | Microsoft Docs"
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
  - "CS0462"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0462"
ms.assetid: 0732b12d-0f7a-47d5-bc54-8b6147d7249f
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0462 de erro do compilador
Os membros herdados 'member1' e 'member2' tem a mesma assinatura no tipo 'type', para que eles não podem ser substituídos  
  
 Este erro ocorre com a introdução de genéricos. Normalmente, você não pode ter duas versões de um método em uma classe com a mesma assinatura. Mas com genéricos, você pode especificar um método genérico que pode duplicar a outro método se ele é instanciado com um tipo específico.  
  
## Exemplo  
 Quando `C<int>` é instanciado, duas versões do método `F` são criadas com a mesma assinatura, então a substituição na classe `D` não é possível decidir qual deles deve aplicar a substituição.  
  
 O exemplo a seguir gera CS0462.  
  
```  
// CS0462.cs // compile with: /target:library class C<T> { public virtual void F(T t) {} public virtual void F(int t) {} } class D : C<int> { public override void F(int t) {}   // CS0462 }  
```