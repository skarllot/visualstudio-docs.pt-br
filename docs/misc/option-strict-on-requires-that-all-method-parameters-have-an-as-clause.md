---
title: "Option Strict On requer que todos os par&#226;metros de m&#233;todo tenham uma cl&#225;usula &#39;As&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30211"
  - "bc30211"
helpviewer_keywords: 
  - "BC30211"
ms.assetid: 855795ce-8499-4525-a1de-cbb8ba364cd7
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On requer que todos os par&#226;metros de m&#233;todo tenham uma cl&#225;usula &#39;As&#39;
Um método contém um parâmetro sem um `As` cláusula. Quando `Option Strict` estiver ativado, cada variável, propriedade, argumento de procedimento e retorno de função devem ser declarado com um `As` cláusula para especificar seu tipo de dados; por exemplo, `Sub GetData(ByVal filter As String)`.  
  
 **ID do erro:** BC30211  
  
### Para corrigir este erro  
  
-   Verifique se o `As` palavra\-chave está incorreto.  
  
-   Forneça um `As` cláusula para a variável declarada, ou ative `Option Strict` off.  
  
## Consulte também  
 [Instrução Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Instrução Sub](/dotnet/visual-basic/language-reference/statements/sub-statement)   
 [Instrução Function](/dotnet/visual-basic/language-reference/statements/function-statement)