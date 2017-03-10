---
title: "CS0400 de erro do compilador | Microsoft Docs"
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
  - "CS0400"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0400"
ms.assetid: 58f91f3b-30f4-433b-9a13-0cff258a2630
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0400 de erro do compilador
O namespace ou tipo 'Identificador de nome' não foi encontrado no namespace global \(uma referência de assembly está faltando?\)  
  
 O identificador de escopo com o operador de escopo global \(`::`\) não foi encontrado no namespace global. Você pode estar faltando uma referência de assembly que contém o identificador ou o identificador pode ser declarado em uma classe ou namespace diferente do namespace global. Esse erro também pode ocorrer se um identificador com escopo definido globalmente não está declarado ou está incorreto.  
  
 Para evitar esse erro, localize a declaração do identificador, verifique a ortografia correta e se a declaração estiver em um assembly separado, certifique\-se de que você tenha a referência de assembly apropriado. Se o identificador é declarado dentro de outro namespace ou tipo, use o nome totalmente qualificado após o::. O exemplo a seguir gera CS0400:  
  
```  
// CS0400.cs class C { public static void Main() { // CS0400 - D could not be found // in the global namespace. global::D d = new global::D(); } }  
```