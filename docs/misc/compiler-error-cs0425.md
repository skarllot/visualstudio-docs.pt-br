---
title: "CS0425 de erro do compilador | Microsoft Docs"
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
  - "CS0425"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0425"
ms.assetid: cec0391c-a641-43bc-8557-92b23f6ca685
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0425 de erro do compilador
As restrições de parâmetro de tipo 'parâmetro do tipo' do método 'method' devem coincidir com as restrições de tipo 'tipo parâmetro' do método de interface 'method'. Considere usar uma implementação de interface explícita.  
  
 Esse erro ocorre se um método genérico virtual é substituído em uma classe derivada e as restrições no método na classe derivada não coincidem com as restrições no método na classe base. Para evitar esse erro, verifique se o `where` cláusula é idêntica em declarações ou implementar interface explicitamente.  
  
## Exemplo  
 O exemplo a seguir gera CS0425:  
  
```  
// CS0425.cs class C1 { } class C2 { } interface IBase { void F<ItemType>(ItemType item) where ItemType : C1; } class Derived : IBase { public void F<ItemType>(ItemType item) where ItemType : C2  // CS0425 { } } class CMain { public static void Main() { } }  
```  
  
## Exemplo  
 As restrições não têm uma correspondência literal, desde que o conjunto de restrições tem o mesmo significado. Por exemplo, o seguinte é bom:  
  
```  
// CS0425b.cs interface J<Z> { } interface I<S> { void F<T>(S s, T t) where T: J<S>, J<int>; } class C : I<int> { public void F<X>(int s, X x) where X : J<int> { } public static void Main() { } }  
```