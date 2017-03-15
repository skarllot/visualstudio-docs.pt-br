---
title: "Relatório de ETW (Rastreamento de Eventos para Windows) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 290b1ea1451181772cdff75ec890da913b6e13be
ms.lasthandoff: 02/22/2017

---
# <a name="event-tracing-for-windows-etw-report"></a>Relatório de Rastreamento de Eventos para Windows (ETW)
O Relatório de ETW (Rastreamento de Eventos para Windows) lista os eventos ETW que são registrados em uma sessão de desempenho das Ferramentas de Criação de Perfil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Dados de ETW são coletados em um arquivo binário (.etl).  
  
> [!NOTE]
>  Não é possível exibir relatórios ETW na interface [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Para obter informações sobre como coletar dados ETW usando as Ferramentas de Criação de Perfil na interface [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], consulte [Como coletar dados ETW (Rastreamento de Eventos para Windows)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
-   Para obter informações sobre como coletar dados ETW usando as ferramentas de linha de comando [VSPerfCmd](../profiling/vsperfcmd.md), consulte [Eventos](../profiling/events-vsperfcmd.md).  
  
-   O relatório de ETW é gerado usando o comando **VSReport/Summary:ETW**. Para obter mais informações, confira [VSPerfReport](../profiling/vsperfreport.md).  
  
|Column|Descrição|  
|------------|-----------------|  
|**Carimbo de data/hora**|Identifica quando o evento ocorreu.|  
|**ID do Processo**|Identifica o processo que gerou o evento.|  
|**ID do Thread**|Identifica o thread que gerou o evento.|  
|**Descrição**|Identifica o provedor de eventos.|  
|**Tipo**|Identifica o tipo de evento.|  
|**Propriedades**|As propriedades do evento. Cada evento é um par nome-valor separado por vírgulas e limitado entre colchetes.|
