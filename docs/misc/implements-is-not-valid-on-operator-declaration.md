---
title: "&#39;Implements&#39; n&#227;o &#233; v&#225;lidos em declara&#231;&#227;o de operador | Microsoft Docs"
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
  - "vbc33004"
  - "bc33004"
helpviewer_keywords: 
  - "BC33004"
ms.assetid: 22f27f4d-4bbd-4f8f-a6e8-0fc10efb268d
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Implements&#39; n&#227;o &#233; v&#225;lidos em declara&#231;&#227;o de operador
Um [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement) Especifica o [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause) palavra\-chave.  
  
 Apenas um `Function` ou `Sub` procedimento, uma propriedade ou um evento pode implementar um membro de interface. Para obter mais informações sobre a implementação, consulte [não está em compilação: exemplos de implementação de Interface no Visual Basic](http://msdn.microsoft.com/pt-br/50bf2a30-73b6-4126-a921-075fd6eec278).  
  
 Uma `Operator` procedimento requer a `Public` e `Shared` palavras\-chave e um operador de conversão requer o `Widening` ou o `Narrowing` palavra\-chave. Para obter mais informações, consulte [Procedimentos do operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures).  
  
 **ID do erro:** BC33004  
  
### Para corrigir este erro  
  
-   Se você pretende que este procedimento para implementar um membro de interface, reescreva\-o como uma `Function` ou `Sub` procedimento, uma propriedade ou um evento.  
  
-   Se você pretende que este procedimento defina um operador, remova a `Implements` palavra\-chave da sua declaração.  
  
## Consulte também  
 [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Como definir um operador de conversão](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)