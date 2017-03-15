---
title: "&#39;Handles&#39; n&#227;o &#233; v&#225;lido em declara&#231;&#227;o de operador | Microsoft Docs"
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
  - "bc33003"
  - "vbc33003"
helpviewer_keywords: 
  - "BC33003"
ms.assetid: 8336402c-9393-4e8e-834d-55c2268f24f6
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Handles&#39; n&#227;o &#233; v&#225;lido em declara&#231;&#227;o de operador
Um [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement) Especifica o [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause) palavra\-chave.  
  
 Somente uma `Sub` procedimento pode manipular eventos. Uma `Operator` procedimento não é possível. Para obter mais informações sobre manipuladores de eventos, consulte [Como chamar um manipulador de eventos no Visual Basic](../Topic/How%20to:%20Call%20an%20Event%20Handler%20in%20Visual%20Basic.md).  
  
 Uma `Operator` procedimento requer a `Public` e `Shared` palavras\-chave e um operador de conversão requer o `Widening` ou o `Narrowing` palavra\-chave. Para obter mais informações, consulte [Procedimentos do operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures).  
  
 **ID do erro:** BC33003  
  
### Para corrigir este erro  
  
-   Se você pretende que este procedimento para manipular eventos, reescreva\-o como uma `Sub` procedimento.  
  
-   Se você pretende que este procedimento defina um operador, remova a `Handles` palavra\-chave da sua declaração.  
  
## Consulte também  
 [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Como definir um operador de conversão](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)