---
title: "Restri&#231;&#245;es para este par&#226;metro de tipo n&#227;o coincidem com as restri&#231;&#245;es no par&#226;metro de tipo correspondente definido em um dos outros tipos parciais de &#39;| 1&#39; | Microsoft Docs"
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
  - "vbc30932"
  - "bc30932"
helpviewer_keywords: 
  - "BC30932"
ms.assetid: a38ca4ad-6bbf-421e-a0d7-c5e0a9029160
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Restri&#231;&#245;es para este par&#226;metro de tipo n&#227;o coincidem com as restri&#231;&#245;es no par&#226;metro de tipo correspondente definido em um dos outros tipos parciais de &#39;| 1&#39;
Quando você divide a definição de uma classe ou estrutura entre várias declarações, o compilador trata a classe ou estrutura como a união de todas as suas declarações parciais. Por isso, você não pode definir quaisquer modificadores conflitantes ou digite listas de parâmetros em várias declarações parciais.  
  
 **ID do erro:** BC30932  
  
### Para corrigir este erro  
  
1.  Determine qual lista de parâmetros de tipo é o desejado para sua classe ou estrutura. Isso inclui os parâmetros, a ordem e suas listas de restrição.  
  
2.  Verifique se que cada definição parcial usa a lista de parâmetros de tipo idêntico.  
  
## Consulte também  
 [Parcial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)