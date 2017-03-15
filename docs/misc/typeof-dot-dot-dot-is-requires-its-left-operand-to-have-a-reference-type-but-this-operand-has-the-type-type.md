---
title: "&#39; TypeOf... &#201; &#39; exige que seu operando esquerdo tenha um tipo de refer&#234;ncia, mas este operando tem o tipo &#39;&lt; type &gt;&#39; | Microsoft Docs"
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
  - "bc30021"
  - "vbc30021"
helpviewer_keywords: 
  - "BC30021"
ms.assetid: a6e76fc8-9c7f-4e55-8b68-e6e7b03a6737
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39; TypeOf... &#201; &#39; exige que seu operando esquerdo tenha um tipo de refer&#234;ncia, mas este operando tem o tipo &#39;&lt; type &gt;&#39;
O `TypeOf...Is` expressão verifica a compatibilidade de tipo de tempo de execução de uma variável de objeto. Essa compatibilidade não está definida para tipos de valor.  
  
 **ID do erro:** BC30021  
  
### Para corrigir este erro  
  
-   Se `Option Strict` for `Off`, use o `TypeName` ou `VarType` função para obter informações de tipo de dados da variável.  
  
-   Se `Option Strict` for `On`, a declaração de variável determina o tipo de dados.  
  
## Consulte também  
 [Operadores de comparação no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)   
 [NÃO está em compilação: TypeName Function \(Visual Basic\)](http://msdn.microsoft.com/pt-br/6197bc6c-e8a6-4711-883c-0c95e94e272c)   
 [NÃO está em compilação: VarType Function \(Visual Basic\)](http://msdn.microsoft.com/pt-br/e820b6fc-faa6-4de4-836a-0466032dc190)   
 [Instrução Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)