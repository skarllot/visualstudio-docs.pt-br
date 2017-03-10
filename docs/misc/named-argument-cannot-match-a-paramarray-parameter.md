---
title: "Argumento nomeado n&#227;o pode corresponder a um par&#226;metro ParamArray | Microsoft Docs"
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
  - "bc30587"
  - "vbc30587"
helpviewer_keywords: 
  - "BC30587"
ms.assetid: aff179af-96f2-4157-971e-881d8e08f5f2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Argumento nomeado n&#227;o pode corresponder a um par&#226;metro ParamArray
Você forneceu um argumento nomeado \(especificado com o nome declarado do argumento seguido por dois pontos e um sinal de igual, seguido do valor do argumento\); No entanto, você não pode passar uma matriz de parâmetros por nome. Quando você chama o procedimento, você fornece um número indefinido de argumentos separados por vírgula para a matriz de parâmetros e o compilador não pode associar mais de um argumento com um único nome.  
  
 **ID do erro:** BC30587  
  
### Para corrigir este erro  
  
-   Passe o argumento por posição, e não por nome.  
  
## Consulte também  
 [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray)   
 [Passando argumentos por posição e nome](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)