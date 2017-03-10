---
title: "A vari&#225;vel &#39;ReadOnly&#39; n&#227;o pode ser o destino de uma atribui&#231;&#227;o | Microsoft Docs"
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
  - "vbc30064"
  - "bc30064"
helpviewer_keywords: 
  - "BC30064"
ms.assetid: 17e0751d-4c22-40b2-bb07-cb5c845dbc30
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A vari&#225;vel &#39;ReadOnly&#39; n&#227;o pode ser o destino de uma atribui&#231;&#227;o
Um `ReadOnly` propriedade foi encontrada em um contexto que atribui um valor a ela. Somente variáveis graváveis, propriedades e elementos de matriz podem ter valores atribuídos a eles durante a execução.  
  
 **ID do erro:** BC30064  
  
### Para corrigir este erro  
  
-   Remover o `ReadOnly` palavra\-chave from a `Dim` instrução declarando a variável, ou remova a instrução que atribui um valor a ela.  
  
## Consulte também  
 [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)   
 [Instrução Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)