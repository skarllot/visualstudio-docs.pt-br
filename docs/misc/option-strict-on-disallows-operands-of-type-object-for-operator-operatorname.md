---
title: "Option Strict On n&#227;o permite operandos do tipo objeto para o operador &#39;&lt; operatorname &gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32013"
  - "vbc32013"
helpviewer_keywords: 
  - "BC32013"
ms.assetid: cd197da8-2676-453b-884b-3231fb6f909d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On n&#227;o permite operandos do tipo objeto para o operador &#39;&lt; operatorname &gt;&#39;
Option Strict On não permite operandos do tipo objeto para o operador '\< operatorname \>'. Use o operador is para testar a identidade do objeto.  
  
 Um operador de comparação aritmética como `=` é usado com uma ou mais variáveis de objeto quando `Option Strict` é `On`.  
  
 **ID do erro:** BC32013  
  
### Para corrigir este erro  
  
1.  Ativar `Option Strict Off` se as variáveis de objeto contêm valores numéricos e você pretende uma comparação aritmética.  
  
2.  Use o `Is` operador para comparar a identidade do objeto.  
  
## Consulte também  
 [Operadores de comparação](/dotnet/visual-basic/language-reference/operators/comparison-operators)   
 [Operador Is](/dotnet/visual-basic/language-reference/operators/is-operator)   
 [Instrução Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)