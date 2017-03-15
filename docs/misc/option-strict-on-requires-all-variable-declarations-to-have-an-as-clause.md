---
title: "Option Strict On exige todas as declara&#231;&#245;es de vari&#225;vel para ter uma cl&#225;usula &#39;As&#39; | Microsoft Docs"
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
  - "bc30209"
  - "vbc30209"
helpviewer_keywords: 
  - "BC30209"
ms.assetid: 69c2e32a-86aa-4075-a142-440605a7063a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On exige todas as declara&#231;&#245;es de vari&#225;vel para ter uma cl&#225;usula &#39;As&#39;
A declaração contém uma variável declarada sem uma `As` cláusula. Quando `Option Strict` é `On`, cada variável, propriedade, argumento de procedimento e retorno de função devem ser declarado com um `As` cláusula para especificar seu tipo de dados; por exemplo, `Dim MyNum As Short`.  
  
 **ID do erro:** BC30209  
  
### Para corrigir este erro  
  
1.  Verifique se o `As` palavra\-chave está incorreto.  
  
2.  Forneça um `As` cláusula para a variável declarada, ou ative `Option Strict Off`.  
  
## Consulte também  
 [Instrução Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Declaração de variável](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)