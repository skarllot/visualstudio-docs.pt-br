---
title: "&#39;&lt; declaration1 &gt;&#39; n&#227;o pode substituir &#39;&lt; declaration2 &gt;&#39; porque est&#225; declarado como &#39;NotOverridable&#39; | Microsoft Docs"
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
  - "bc30267"
  - "vbc30267"
helpviewer_keywords: 
  - "BC30267"
ms.assetid: fb1f6797-4e49-442e-a660-59d602132631
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; declaration1 &gt;&#39; n&#227;o pode substituir &#39;&lt; declaration2 &gt;&#39; porque est&#225; declarado como &#39;NotOverridable&#39;
Uma declaração de procedimento ou a propriedade tenta substituir um elemento herdado de mesmo nome, mas o elemento herdado é especificado como `NotOverridable`.  
  
 **ID do erro:** BC30267  
  
### Para corrigir este erro  
  
-   Remover o `NotOverridable` palavra\-chave da declaração do elemento herdado, ou remova a declaração de substituição.  
  
## Consulte também  
 [NÃO está em compilação: Substituindo métodos e propriedades](http://msdn.microsoft.com/pt-br/2167e8f5-1225-4b13-9ebd-02591ba90213)