---
title: "&#39;&lt; declaration1 &gt;&#39; n&#227;o pode substituir &#39;&lt; declaration2 &gt;&#39; porque est&#225; declarado como &#39;Shared&#39; | Microsoft Docs"
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
  - "vbc30268"
  - "bc30268"
helpviewer_keywords: 
  - "BC30268"
ms.assetid: d011fb26-6236-462e-9173-622f8bbeb536
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; declaration1 &gt;&#39; n&#227;o pode substituir &#39;&lt; declaration2 &gt;&#39; porque est&#225; declarado como &#39;Shared&#39;
Uma declaração de procedimento ou a propriedade tenta substituir um elemento herdado de mesmo nome, mas o elemento herdado é especificado como `Shared`. Elementos compartilhados não são associados a qualquer instância da classe, para que eles não podem ser substituídos.  
  
 **ID do erro:** BC30268  
  
### Para corrigir este erro  
  
-   Remover o `Shared` palavra\-chave do elemento herdado, ou remova a declaração de substituição.  
  
## Consulte também  
 [NÃO está em compilação: Substituindo métodos e propriedades](http://msdn.microsoft.com/pt-br/2167e8f5-1225-4b13-9ebd-02591ba90213)