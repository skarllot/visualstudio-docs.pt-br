---
title: "CS0677 de erro do compilador | Microsoft Docs"
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
  - "CS0677"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0677"
ms.assetid: 6a4a3703-9b44-4c4f-a564-8b437b1cb6b8
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0677 de erro do compilador
'variável': um campo volátil não pode ser do tipo 'type'  
  
 Os campos declarados com o `volatile` palavra\-chave deve ser um dos seguintes tipos:  
  
-   Qualquer tipo de referência  
  
-   Qualquer tipo de ponteiro \(em um `unsafe` contexto\)  
  
-   The types `sbyte`, **byte**, **short**, `ushort`, `int`, `uint`, `char`, **float**, `bool`  
  
-   Tipos de enumeração com base em qualquer um dos tipos anteriores  
  
 O exemplo a seguir gera CS0677:  
  
```  
// CS0677.cs class TestClass { private volatile long i;   // CS0677 public static void Main() { } }  
```