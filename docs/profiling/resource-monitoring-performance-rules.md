---
title: "Regras de desempenho do monitoramento de recurso | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f0f77faf-0a05-4718-a2c5-47934be40868
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Regras de desempenho do monitoramento de recurso
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

As mensagens de desempenho na categoria de monitoramento de recursos fornecem dados adicionais sobre o desempenho de seu aplicativo.  Você pode usar esses dados para analisar problemas de desempenho.  Essas regras são informativas e relatadas para cada analisar executado.  
  
|||  
|-|-|  
|[DA0501: consumo de CPU médio pelo processo com perfil criado.](../Topic/DA0501:%20Average%20CPU%20consumption%20by%20the%20Process%20being%20profiled..md)|Esta mensagem reporta a porcentagem de tempo que um processador não ocupado executar instruções de aplicativo.  O valor relatado é a média de todos os intervalos da medida em que o processo que está sendo analisado ativo.|  
|[DA0502: consumo de CPU máximo pelo processo com perfil criado](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|Esta mensagem reporta a porcentagem máxima de tempo que um processador não ocupado executar instruções de aplicativo.  O valor relatado é o valor máximo indicado entre todos os intervalos da medida em que o processo que está sendo analisado ativo.|  
|[DA0503: conjunto de trabalho médio em bytes para o processo com criação de perfil](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|Esta mensagem reporta a quantidade média de memória física, em bytes, que o processo quando estava usando analisar ativo.  Essa medida de memória física é conhecida como o conjunto de trabalho.|  
|[DA0504: conjunto de trabalho máximo em bytes para o processo com criação de perfil](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|Esta mensagem reporta a quantidade máxima de memória física, em bytes, que o processo quando estava usando analisar ativo.|  
|[DA0505: média de bytes particulares alocados para o processo com criação de perfil](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|Esta mensagem reporta a quantidade média de memória virtual que o processo alocado em bytes quando analisar ativo.  Essa medida de memória virtual é conhecida como *bytes privados*.  Os bytes privados representam locais de memória virtual que foram atribuídos pelo processo que pode ser acessado somente por threads executados no processo.|  
|[DA0506: máximo de bytes particulares alocados para o processo com criação de perfil](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|Esta mensagem reporta a quantidade máxima de memória virtual que o processo alocado em particular bytes quando analisar ativo.|