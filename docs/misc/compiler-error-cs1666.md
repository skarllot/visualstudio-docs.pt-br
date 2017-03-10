---
title: "CS1666 de erro do compilador | Microsoft Docs"
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
  - "CS1666"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1666"
ms.assetid: 4d62aa9c-71b9-4c6e-8141-2426d20ac243
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1666 de erro do compilador
Você não pode usar buffers de tamanho fixo contidos em expressões não corrigidas. Tente usar a instrução fixed.  
  
 Esse erro ocorre se você usar o buffer de tamanho fixo em uma expressão que envolva uma classe que não está corrigido. O tempo de execução está livre para percorrer a classe não corrigida para otimizar o acesso à memória, que pode levar a erros quando usar fixo em tamanho de buffer. Para evitar esse erro, use o `fixed` palavra\-chave na instrução.  
  
## Exemplo  
 O exemplo a seguir gera CS1666.  
  
```  
// CS1666.cs // compile with: /unsafe /target:library unsafe struct S { public fixed int buffer[1]; } unsafe class Test { S field = new S(); private bool example1() { return (field.buffer[0] == 0);   // CS1666 error } private bool example2() { // OK fixed (S* p = &field) { return (p->buffer[0] == 0); } } private bool example3() { S local = new S(); return (local.buffer[0] == 0); } }  
```