---
title: "&#39;Sub New&#39; n&#227;o podem ser declarado &#39;Overrides&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30283"
  - "bc30283"
helpviewer_keywords: 
  - "BC30283"
ms.assetid: 0e71cdcb-b62e-4a36-8829-83de5c453c74
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Sub New&#39; n&#227;o podem ser declarado &#39;Overrides&#39;
Um construtor indica que ele substitui um construtor herdado. Construtores não podem ser substituídos.  
  
 **ID do erro:** BC30283  
  
### Para corrigir este erro  
  
-   Remover o `Overrides` palavra\-chave from a `Sub` declaração.  
  
## Consulte também  
 [NÃO está em compilação: Substituindo métodos e propriedades](http://msdn.microsoft.com/pt-br/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [NÃO está em compilação: Usando construtores e destruidores](http://msdn.microsoft.com/pt-br/548eebe1-86c4-4377-b2f5-447cb8be3d90)