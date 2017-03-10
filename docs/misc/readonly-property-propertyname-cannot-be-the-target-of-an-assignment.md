---
title: "A propriedade &#39;ReadOnly&#39; &#39;&lt; propertyname &gt;&#39; n&#227;o pode ser o destino de uma atribui&#231;&#227;o | Microsoft Docs"
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
  - "bc30098"
  - "vbc30098"
helpviewer_keywords: 
  - "BC30098"
ms.assetid: d0c6cdac-a49d-49d2-ba92-ddf01eed0620
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A propriedade &#39;ReadOnly&#39; &#39;&lt; propertyname &gt;&#39; n&#227;o pode ser o destino de uma atribui&#231;&#227;o
Um `ReadOnly` propriedade ocorre em um contexto que atribui um valor a ela. Somente variáveis graváveis, propriedades e elementos de matriz podem ter valores atribuídos a eles durante a execução.  
  
 **ID do erro:** BC30098  
  
### Para corrigir este erro  
  
-   Remover o `ReadOnly` palavra\-chave from a `Property` instrução declarando a variável, ou remova a instrução que atribui um valor a ela.  
  
## Consulte também  
 [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)   
 [Instrução Property](/dotnet/visual-basic/language-reference/statements/property-statement)