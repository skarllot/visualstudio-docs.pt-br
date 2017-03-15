---
title: "Acesso de propriedade deve ser atribu&#237;do &#224; propriedade ou usar seu valor | Microsoft Docs"
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
  - "bc30545"
  - "vbc30545"
helpviewer_keywords: 
  - "BC30545"
ms.assetid: df271c05-1e7a-44e8-bf53-79f06ef916ab
caps.latest.revision: 11
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Acesso de propriedade deve ser atribu&#237;do &#224; propriedade ou usar seu valor
Você tentou acessar uma propriedade sem atribuí\-lo ou usar seu valor. O código a seguir fornece um exemplo:  
  
 [!CODE [VbVbalrErrorSamples#1](VbVbalrErrorSamples#1)]  
  
 **ID do erro:** BC30545  
  
### Para corrigir este erro  
  
-   Atribua um valor à propriedade, conforme mostrado no exemplo a seguir:  
  
     [!CODE [VbVbalrErrorSamples#3](VbVbalrErrorSamples#3)]  
  
     \- ou \-  
  
-   Use o valor da propriedade, conforme mostrado no exemplo a seguir:  
  
     [!CODE [VbVbalrErrorSamples#2](VbVbalrErrorSamples#2)]  
  
## Consulte também  
 [Procedimentos de propriedade](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Operadores de atribuição](/dotnet/visual-basic/language-reference/operators/assignment-operators)