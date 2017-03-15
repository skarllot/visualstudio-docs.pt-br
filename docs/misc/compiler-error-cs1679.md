---
title: "CS1679 de erro do compilador | Microsoft Docs"
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
  - "CS1679"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1679"
ms.assetid: c42e9bca-212a-458e-88f8-b81c812436bb
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1679 de erro do compilador
Alias externo inválido para '\/Reference'; 'identifier' não é um identificador válido  
  
 Ao usar o recurso de alias de assembly externo das **\/reference** opção, o texto que segue **\/reference:** e que precede o '\=' deve ser um identificador c\# válido ou a palavra\-chave de acordo com a especificação da linguagem c\#.  
  
 Para corrigir esse erro, altere o texto antes do "\=" para um identificador c\# válido ou a palavra\-chave.  
  
## Exemplo  
 O exemplo a seguir gera CS1679.  
  
```  
// CS1679.cs // compile with: /reference:123$BadIdentifier%=System.dll class TestClass { static void Main() { } }  
```