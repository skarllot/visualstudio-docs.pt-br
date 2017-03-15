---
title: "&#39;Exit Operator&#39; n&#227;o &#233; v&#225;lido. Use &#39;Return&#39; para sair de um operador | Microsoft Docs"
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
  - "bc33008"
  - "vbc33008"
helpviewer_keywords: 
  - "BC33008"
ms.assetid: 8c44456b-8fd2-4168-ad8c-b6da129242ba
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit Operator&#39; n&#227;o &#233; v&#225;lido. Use &#39;Return&#39; para sair de um operador
Um `Exit Operator` instrução aparece em uma `Operator` procedimento.  
  
 Você deve usar um [Instrução Return](/dotnet/visual-basic/language-reference/statements/return-statement) para retornar de uma `Operator` procedimento. O [Instrução Exit](/dotnet/visual-basic/language-reference/statements/exit-statement) não aceita o `Operator` palavra\-chave e o `End Operator` instrução retorna o controle para o código de chamada.  
  
 **ID do erro:** BC33008  
  
### Para corrigir este erro  
  
-   Substitua o `Exit Operator` instrução com um `Return` instrução.  
  
## Consulte também  
 [Procedimentos do operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Como definir um operador de conversão](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)