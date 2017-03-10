---
title: "CS1032 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1032"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1032"
ms.assetid: fe318a6c-4403-4b9b-b3d8-753ec31c00ff
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1032 de erro do compilador
Não é possível definir ou remover a definição símbolos de pré\-processamento após o primeiro token no arquivo  
  
 O `#define` e `#undef` [diretivas de pré\-processador](/dotnet/csharp/language-reference/preprocessor-directives/index) deve ser usado no início de um programa, antes de quaisquer outras palavras\-chave, como aqueles usados na declaração de namespace.  
  
 O exemplo a seguir gera CS1032:  
  
```  
// CS1032.cs namespace x { public class clx { #define a   // CS1032, put before namespace public static void Main() { } } }  
```