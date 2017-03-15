---
title: "CS0459 de erro do compilador | Microsoft Docs"
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
  - "CS0459"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0459"
ms.assetid: 01b058dd-8d65-4e9d-9de1-d47f9488d22a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0459 de erro do compilador
Não é possível obter o endereço de uma variável local somente leitura  
  
 Há três cenários comuns na linguagem c\# que geram variáveis locais somente leitura: `foreach`, `using`, e `fixed`. Em cada um desses casos, você não tem permissão para gravar a variável local somente leitura ou para obter seu endereço. Esse erro é gerado quando o compilador percebe que você está tentando obter o endereço de uma variável local somente leitura.  
  
## Exemplo  
 O exemplo a seguir gera CS0459 quando é feita uma tentativa de obter o endereço de uma variável local somente leitura em um `foreach` loop e, em um `fixed` Bloco de instrução.  
  
```  
// CS0459.cs // compile with: /unsafe class A { public unsafe void M1() { int[] ints = new int[] { 1, 2, 3 }; foreach (int i in ints) { int *j = &i;  // CS0459 } fixed (int *i = &_i) { int **j = &i;  // CS0459 } } private int _i = 0; }  
```