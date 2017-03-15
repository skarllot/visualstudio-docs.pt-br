---
title: "CS0455 de erro do compilador | Microsoft Docs"
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
  - "CS0455"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0455"
ms.assetid: a09840ac-ad8c-4c9c-868e-b83d937c7047
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0455 de erro do compilador
Parâmetro de tipo 'Nome do parâmetro de tipo' herda as restrições conflitantes '1 de nome de restrição' e '2 nome de restrição'  
  
 Duas maneiras de obter esse erro são configurar restrições para que o parâmetro de tipo derivado de duas classes não relacionadas ou para que ele deriva de uma restrição de tipo de referência ou de tipo de classe e um `struct` restrição de tipo de valor ou tipo. Para resolver esse erro, remova o conflito de sua hierarquia de herança.  
  
## Exemplo  
 O código a seguir gera erro CS0455.  
  
```  
// CS0455.cs using System; public class GenericsErrors { public class B { } public class B2 { } public class G6<T> where T : B { public class N<U> where U : B2, T { } } // CS0455 }  
```