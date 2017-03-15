---
title: "&#39;End Property&#39; deve ser precedido por &#39;Property&#39; correspondente | Microsoft Docs"
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
  - "vbc30431"
  - "bc30431"
helpviewer_keywords: 
  - "BC30431"
ms.assetid: b1e02d97-b38a-4acf-b351-1726f17a0051
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Property&#39; deve ser precedido por &#39;Property&#39; correspondente
Um `End Property` instrução aparece no seu código com nenhuma correspondência `Property` declaração anterior.  
  
 **ID do erro:** BC30431  
  
### Para corrigir este erro  
  
-   Remover o `End Property` instrução se ela é redundante.  
  
-   Forneça a `Property` procedimento se uma estiver ausente.  
  
-   Mova o `End Property` até o local apropriado no código.  
  
## Consulte também  
 [NÃO está em compilação: Propriedades e procedimentos de propriedade](http://msdn.microsoft.com/pt-br/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [Instrução End \<keyword\>](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)