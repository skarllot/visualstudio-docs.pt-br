---
title: "&#39;Sub New&#39; n&#227;o pode ser declarado em uma interface | Microsoft Docs"
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
  - "bc30363"
  - "vbc30363"
helpviewer_keywords: 
  - "BC30363"
ms.assetid: 371d9aa8-a935-48ce-ada2-0a69ba20e070
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Sub New&#39; n&#227;o pode ser declarado em uma interface
Você tentou declarar `Sub New` dentro de uma interface. Como é um construtor, `Sub New` pode executar apenas uma vez quando uma classe é criada. Ele não pode ser chamado explicitamente de qualquer lugar que não seja a primeira linha do código em outro construtor na mesma classe ou uma classe derivada.  
  
 **ID do erro:** BC30363  
  
### Para corrigir este erro  
  
-   Remover o `Sub New` ou movê\-lo para um local mais adequado em seu código.  
  
## Consulte também  
 [NÃO está em compilação: Usando construtores e destruidores](http://msdn.microsoft.com/pt-br/548eebe1-86c4-4377-b2f5-447cb8be3d90)