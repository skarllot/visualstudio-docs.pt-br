---
title: "Op&#231;&#227;o Strict On desabilita associa&#231;&#227;o tardia | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30574"
  - "vbc30574"
helpviewer_keywords: 
  - "BC30574"
ms.assetid: 9da4b826-2e12-4a5d-9e17-762b0b68fc9b
caps.latest.revision: 11
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Op&#231;&#227;o Strict On desabilita associa&#231;&#227;o tardia
[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] permite conversões implícitas de qualquer tipo de dados para qualquer outro tipo de dados. No entanto, pode ocorrer perda de dados se o valor de um tipo de dados é convertido em um tipo de dados com menor precisão ou menor capacidade.`Option Strict On` garante notificação em tempo de compilação desses tipos de conversões para que elas podem ser evitadas. Não é possível usar `Option Strict On` com associação tardia.  
  
 O exemplo de código a seguir utiliza a vinculação tardia e faz com que esse erro quando `Option Strict` está definido como `On`.  
  
 [!CODE [VbVbalrOptionStrictError#1](VbVbalrOptionStrictError#1)]  
  
 **ID do erro:** BC30574  
  
### Para corrigir este erro  
  
-   Modifique a declaração de objeto para usar um tipo explícito, conforme mostrado no exemplo a seguir:  
  
     [!CODE [VbVbalrOptionStrictError#2](VbVbalrOptionStrictError#2)]  
  
 \- ou \-  
  
-   Modifique a expressão de associação tardia para especificar um tipo explícito, conforme mostrado no exemplo a seguir:  
  
     [!CODE [VbVbalrOptionStrictError#3](VbVbalrOptionStrictError#3)]  
  
 \- ou \-  
  
-   Permitir que o compilador inferir um tipo específico, conforme mostrado no exemplo a seguir:  
  
     [!CODE [VbVbalrOptionStrictError#4](VbVbalrOptionStrictError#4)]  
  
 \- ou \-  
  
-   Ativar `Option Strict` desativado, removendo a palavra `On` ou especificando explicitamente `Off`.  
  
## Consulte também  
 [Funções de conversão do tipo](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)   
 [Instrução Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Conversões de Widening e Narrowing](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)