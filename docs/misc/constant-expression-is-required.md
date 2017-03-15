---
title: "Express&#227;o de constante &#233; necess&#225;ria | Microsoft Docs"
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
  - "bc30059"
  - "vbc30059"
helpviewer_keywords: 
  - "BC30059"
ms.assetid: fdd5e7bb-6370-4a63-bbb6-23b15badb4c8
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Express&#227;o de constante &#233; necess&#225;ria
Um `Const` instrução não inicializa corretamente uma constante ou uma declaração de matriz usa uma variável para especificar o número de elementos.  
  
 **ID do erro:** BC30059  
  
### Para corrigir este erro  
  
1.  Se a declaração é um `Const` instrução, verifique se a constante é inicializada com um literal, uma constante declarada anteriormente, um membro de enumeração ou uma combinação de literais, constantes e membros de enumeração combinados com operadores.  
  
2.  Se a declaração especifica uma matriz, verifique se uma variável está sendo usada para especificar o número de elementos. Nesse caso, substitua a variável com uma expressão constante.  
  
## Consulte também  
 [Instrução Const](/dotnet/visual-basic/language-reference/statements/const-statement)   
 [NOTINBUILD uma variável de matriz](http://msdn.microsoft.com/pt-br/c2da78bd-6928-46ba-805f-44f819dfaf93)