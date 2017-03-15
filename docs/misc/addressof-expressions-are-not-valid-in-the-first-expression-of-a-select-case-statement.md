---
title: "Express&#245;es &#39;AddressOf&#39; n&#227;o s&#227;o v&#225;lidas na primeira express&#227;o de uma instru&#231;&#227;o &#39;Select Case&#39; | Microsoft Docs"
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
  - "bc36636"
  - "vbc36636"
helpviewer_keywords: 
  - "BC36636"
ms.assetid: 2ccc0ccc-d4d0-4910-8859-dedfa57c8126
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Express&#245;es &#39;AddressOf&#39; n&#227;o s&#227;o v&#225;lidas na primeira express&#227;o de uma instru&#231;&#227;o &#39;Select Case&#39;
Não é possível usar um `AddressOf` expressão para a expressão de teste em um `Select Case` instrução.`AddressOf` expressões retornam delegados de funções e a expressão de teste de um `Select Case` instrução deve ser um tipo de dados elementar.  
  
 **ID do erro:** BC36636  
  
### Para corrigir este erro  
  
-   Examine seu código para determinar se uma construção condicional diferente, como um `If...Then...Else` instrução, funcionaria para você.  
  
## Consulte também  
 [Operador AddressOf](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [Instrução If...Then...Else](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)   
 [Instrução Select...Case](/dotnet/visual-basic/language-reference/statements/select-case-statement)