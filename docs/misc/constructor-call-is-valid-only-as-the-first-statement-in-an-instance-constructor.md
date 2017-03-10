---
title: "Chamada de construtor &#233; v&#225;lida somente como a primeira instru&#231;&#227;o em um construtor de inst&#226;ncia | Microsoft Docs"
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
  - "vbc30282"
  - "bc30282"
helpviewer_keywords: 
  - "BC30282"
ms.assetid: c51b172f-fbd7-4ef5-8276-01a4bf6ed35b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Chamada de construtor &#233; v&#225;lida somente como a primeira instru&#231;&#227;o em um construtor de inst&#226;ncia
Uma chamada para `New()` ocorre após a primeira instrução de um construtor. Se um construtor chama outro explicitamente, deverá fazê\-lo na seguinte instrução primeiro o `Sub New()` instrução.  
  
 **ID do erro:** BC30282  
  
### Para corrigir este erro  
  
-   Remover a chamada para `New()`, ou movê\-lo para o início do construtor.  
  
## Consulte também  
 [NÃO está em compilação: Usando construtores e destruidores](http://msdn.microsoft.com/pt-br/548eebe1-86c4-4377-b2f5-447cb8be3d90)