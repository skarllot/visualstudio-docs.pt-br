---
title: "&#39;&lt; especificador &gt;&#39; n&#227;o &#233; v&#225;lido em uma declara&#231;&#227;o de vari&#225;vel de membro | Microsoft Docs"
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
  - "vbc30235"
  - "bc30235"
helpviewer_keywords: 
  - "BC30235"
ms.assetid: 8c5764e4-0096-4ca0-8656-05341a39833a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; especificador &gt;&#39; n&#227;o &#233; v&#225;lido em uma declara&#231;&#227;o de vari&#225;vel de membro
Um `Dim` instrução contém uma palavra\-chave inválida. Um `Dim` instrução pode incluir somente o `Friend`, `Private`, `Protected`, `Public`, `ReadOnly`, `Shadows`, `Shared`, ou `Static` palavras\-chave.  
  
 Essa mensagem também pode aparecer se você declarar um `Static` variável fora de um procedimento. Você pode usar `Static` somente no nível de procedimento.  
  
 Observe que, se você incluir uma palavra\-chave válida em uma `Dim` instrução, você pode opcionalmente omitir o `Dim` palavra\-chave.  
  
 **ID do erro:** BC30235  
  
### Para corrigir este erro  
  
1.  Remova a palavra\-chave inválida do `Dim` instrução.  
  
2.  Se você declarou um `Static` variável fora de um procedimento, mova a declaração dentro de um procedimento ou remova o `Static` palavra\-chave.  
  
## Consulte também  
 [Instrução Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)