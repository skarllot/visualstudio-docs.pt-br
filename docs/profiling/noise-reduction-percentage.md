---
title: "Porcentagem de redu&#231;&#227;o do ru&#237;do | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.filter"
helpviewer_keywords: 
  - "Visualizador de Simultaneidade, Porcentagem de redução do ruído"
ms.assetid: 1c10cd4c-2fdd-48c9-b562-a334b3b2df6c
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Porcentagem de redu&#231;&#227;o do ru&#237;do
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Por padrão, o valor da configuração percentual de redução de ruído é 2.  Somente as entradas que têm uma porcentagem de tempo inclusivos maior ou igual a essa configuração são mostradas na árvore de chamada.  Alterar a configuração, você pode controlar o número de entradas que são exibidos na árvore de chamada.  Por exemplo, alterando o valor como 10 mostrará apenas as entradas de árvore de chamada que têm uma hora inclusivas maior ou igual a 10%.  Aumentando o valor de configuração, poderá enfatizar as entradas que têm maior impacto no desempenho do processo.