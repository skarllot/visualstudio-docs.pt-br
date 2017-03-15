---
title: "VsgDbg::~VsgDbg (Destruidor) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VsgDbg::~VsgDbg (Destruidor)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Destrói uma instância da classe de `VsgDbg` .  Se as informações dos gráficos está sendo registrada ativamente, o arquivo de log dos gráficos é encerrada e fechado, e recursos que foram usados ativamente para capturar gráficos que as informações é liberada.  
  
## Sintaxe  
  
```cpp  
~VsgDbg();  
```  
  
## Consulte também  
 [VsgDbg::VsgDbg \(Construtor\)](../Topic/VsgDbg::VsgDbg%20\(Constructor\).md)