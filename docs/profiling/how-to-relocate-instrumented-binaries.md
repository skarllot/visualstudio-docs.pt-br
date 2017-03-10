---
title: "Como realocar bin&#225;rios instrumentados | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.binaries"
helpviewer_keywords: 
  - "binários instrumentados"
  - "Instrumentação de binários instrumentados"
  - "binários instrumentos e realocação"
  - "ferramentas de criação de perfil, instrumentado binários"
ms.assetid: 258f49e8-4b09-477e-a132-8fad685b66f4
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como realocar bin&#225;rios instrumentados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Durante a instrumentação, sondagem forem inseridas em binário para medir o desempenho do aplicativo.  Escolhendo para realocar binário provido, uma cópia do binário original é instrumentada e colocada no local especificado.  Essa opção será útil se você não quiser que o profiler para renomear o binário original.  Se binária não será realocado, a versão original do binário é substituída.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### Para realocar binário provido  
  
1.  Em **Desempenho Explorer**, clique com o botão direito do mouse na sessão de desempenho, e clique em **Propriedades**.  
  
2.  Em **Páginas de Propriedades**, clique nas propriedades de **Binário** .  
  
3.  Marque a caixa de seleção de **Realocar proveu binários** .  
  
4.  Especifique o local para binário provido.  
  
## Consulte também  
 [Configurando sessões de desempenho](../profiling/configuring-performance-sessions.md)   
 [VSInstr](../profiling/vsinstr.md)