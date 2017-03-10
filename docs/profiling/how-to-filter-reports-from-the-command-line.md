---
title: "Como filtrar relat&#243;rios a partir da linha de comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como filtrar relat&#243;rios a partir da linha de comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Usando opções para o comando de **VSPerfReport** , você pode filtrar relatórios a um segmento de tempo específico do arquivo de dados de perfil ou restringir os dados a um ou vários processos ou threads.  Para obter mais informações sobre esse comando, consulte [VSPerfReport](../profiling/vsperfreport.md).  
  
|Opções|Descrição|  
|------------|---------------|  
|**StartTime:**\[*Value*\]|Apenas dados de apresentação coletados depois do valor \(em milissegundos\).|  
|**EndTime:**\[*Value*\]|Apenas dados de apresentação coletados antes do valor \(em milissegundos\).|  
|**FilterFile:** `VSPFFile`|Especifica o local de um arquivo de filtro que foi gerado da janela de **Relatório de Desempenho do Visual Studio** .|  
|**MsFilter:**\[*StartTime,Duration*\]|Mostrar apenas dados de `StartTime` até o comprimento de `Duration` \(em milissegundos\).|  
|**Process:**\[*Pid*\]|Mostrar apenas dados de processo especificado.|  
|**Thread:**\[*ThreadID*\]|Mostrar apenas dados do thread especificado.|  
|**Thread:**\[*ThreadID,ProcessID*\]|Mostrar apenas dados especificado do thread associado ao processo especificado.|