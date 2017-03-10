---
title: "Erro de sintaxe no operador cast; dois argumentos separados por v&#237;rgula s&#227;o necess&#225;rios | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30944"
  - "bc30944"
helpviewer_keywords: 
  - "BC30944"
ms.assetid: 1f7ed4a1-6ff5-4836-8424-21618c68ff45
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Erro de sintaxe no operador cast; dois argumentos separados por v&#237;rgula s&#227;o necess&#225;rios
Uma expressão usa a `CType` função de conversão ou `DirectCast` ou `TryCast` palavra\-chave conversão mas fornece somente um argumento.  
  
 `CType`, `DirectCast`, e `TryCast` exigem dois argumentos. A primeira é uma expressão a ser convertida e o segundo é o tipo de dados ou tipo de classe para qual converter.  
  
 **ID do erro:** BC30944  
  
### Para corrigir este erro  
  
-   Fornece os dois argumentos conforme necessário para a conversão.  
  
-   Se você pretende usar um específico [Funções de conversão do tipo](/dotnet/visual-basic/language-reference/functions/type-conversion-functions) como `CString`, você deve usar esse nome de função em vez de `CType`. Em seguida, apenas um argumento é necessário.  
  
## Consulte também  
 [Função CType](/dotnet/visual-basic/language-reference/functions/ctype-function)   
 [Operador DirectCast](/dotnet/visual-basic/language-reference/operators/directcast-operator)   
 [Operador TryCast](/dotnet/visual-basic/language-reference/operators/trycast-operator)   
 [Funções de conversão do tipo](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)