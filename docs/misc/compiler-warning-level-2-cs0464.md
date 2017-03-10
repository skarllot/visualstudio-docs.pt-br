---
title: "Compilador CS0464 de aviso (n&#237;vel 2) | Microsoft Docs"
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
  - "CS0464"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0464"
ms.assetid: 3dff97d4-e1f6-4a71-91e2-68cffc38d49a
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0464 de aviso (n&#237;vel 2)
Comparação com null do tipo 'type' sempre produz 'false'  
  
 Esse aviso é gerado quando você executa uma comparação entre uma variável anulável e null, e a comparação não é `==` ou `!=`. Para resolver esse erro, verifique se você realmente deseja verificar um valor para `null`. Uma comparação, como `i == null` pode ser verdadeiro falso. Uma comparação como `i > null` sempre é false.  
  
## Exemplo  
 O exemplo a seguir gera CS0464.  
  
```  
// CS0464.cs class MyClass { public static void Main() { int? i = 0; if (i < null) ;   // CS0464 i++; } }  
```