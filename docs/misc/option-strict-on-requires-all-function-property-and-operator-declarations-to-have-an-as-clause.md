---
title: "Option Strict On exige todas as declara&#231;&#245;es de fun&#231;&#227;o, propriedade e operador tenham uma cl&#225;usula &#39;As&#39; | Microsoft Docs"
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
  - "vbc30210"
  - "bc30210"
helpviewer_keywords: 
  - "BC30210"
ms.assetid: 4d217e56-0eac-4834-bcad-234a69809390
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On exige todas as declara&#231;&#245;es de fun&#231;&#227;o, propriedade e operador tenham uma cl&#225;usula &#39;As&#39;
A declaração contém uma propriedade declarada ou retorno de função sem um `As` cláusula. Quando `Option Strict` é `On`, cada variável, propriedade, argumento de procedimento e retorno de função devem ser declarado com um `As` cláusula para especificar seu tipo de dados; por exemplo, `Dim MyNum As Short`.  
  
 **ID do erro:** BC30210  
  
### Para corrigir este erro  
  
1.  Verifique se o `As` palavra\-chave está incorreto.  
  
2.  Forneça um `As` cláusula para a propriedade declarada ou retorno de função ou ative `Option Strict Off`.  
  
## Consulte também  
 [Instrução Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Procedimentos de propriedade](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Procedimentos de função](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)