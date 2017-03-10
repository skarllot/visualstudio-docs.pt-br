---
title: "Relat&#243;rio de Rastreamento de Eventos para Windows (ETW) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "relatório de criação de perfil de ETW"
  - "Rastreamento de evento para relatório de criação de perfil do Windows"
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Relat&#243;rio de Rastreamento de Eventos para Windows (ETW)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O relatório lista de Rastreamento de Eventos do Windows \(ETW\) os eventos de ETW que foram gravados em uma sessão de desempenho de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Ferramentas de Criação de Perfil.  Os dados do ETW são coletados em um arquivo binário \(.etl\).  
  
> [!NOTE]
>  Você não pode exibir relatórios ETW na interface de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  
  
-   Para obter informações sobre como coletar ETW usando Ferramentas de Criação de Perfil da interface de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , consulte [Como coletar dados de Rastreamento de Eventos para Windows \(ETW\)](../Topic/How%20to:%20Collect%20Event%20Tracing%20for%20Windows%20\(ETW\)%20Data.md).  
  
-   Para obter informações sobre como coletar dados do ETW usando as ferramentas de linha de comando de [VSPerfCmd](../profiling/vsperfcmd.md) , consulte [Eventos](../profiling/events-vsperfcmd.md).  
  
-   Você gerencia o relatório ETW usando o comando de **VSReport\/Summary:ETW** .  Para obter mais informações, consulte [VSPerfReport](../profiling/vsperfreport.md).  
  
|Coluna|Descrição|  
|------------|---------------|  
|**Carimbo de data\/hora**|Identifica quando o evento ocorreu.|  
|**Identificação do Processo**|Identifica o processo que gerou o evento.|  
|**Identificação do Thread**|Identifica o thread que gerou o evento.|  
|**Descrição**|Identifica o provedor de eventos.|  
|**Tipo**|Identifica o tipo de evento.|  
|**Propriedades**|As propriedades do evento.  Cada evento é um separado por vírgulas, o par de nome\-valor que é colocado entre colchetes.|