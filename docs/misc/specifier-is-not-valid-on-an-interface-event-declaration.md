---
title: "&#39;&lt; especificador &gt;&#39; n&#227;o &#233; v&#225;lido em uma declara&#231;&#227;o de evento de interface | Microsoft Docs"
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
  - "bc30275"
  - "vbc30275"
helpviewer_keywords: 
  - "BC30275"
ms.assetid: bd12c952-c619-4753-8d6d-90ef4086fdc2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; especificador &gt;&#39; n&#227;o &#233; v&#225;lido em uma declara&#231;&#227;o de evento de interface
Um `Event` instrução dentro de uma interface contém uma palavra\-chave que não é permitida, como `Implements`. Uma interface pode apenas definir membros, não implementá\-los.  
  
 **ID do erro:** BC30275  
  
### Para corrigir este erro  
  
1.  Remova a palavra\-chave da instrução de declaração.  
  
2.  Mova a implementação dos membros de interface para uma classe que implementa a interface.  
  
## Consulte também  
 [Instrução Interface](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Instrução Implements](/dotnet/visual-basic/language-reference/statements/implements-statement)