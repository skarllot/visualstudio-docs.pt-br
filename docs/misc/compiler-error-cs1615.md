---
title: "CS1615 de erro do compilador | Microsoft Docs"
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
  - "CS1615"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1615"
ms.assetid: 518bb07f-0e3a-4761-9931-66845eb5df1a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1615 de erro do compilador
'Número de argumento' não deve ser transmitido com a palavra\-chave 'palavra\-chave'  
  
 Uma das palavras\-chave `ref` ou **out** foi usado quando a função não continha um `ref` ou **out** parâmetro para o argumento. Para resolver esse erro, remova a palavra\-chave incorreta e use a palavra\-chave apropriada que corresponda a declaração de função, se houver.  
  
 O exemplo a seguir gera CS1615:  
  
```  
// CS1615.cs class C { public void f(int i) {} public static void Main() { int i = 1; f(ref i);  // CS1615 } }  
```