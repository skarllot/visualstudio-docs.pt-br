---
title: "Coletando dados de tempo detalhados para um aplicativo Web do ASP.NET usando o m&#233;todo de instrumenta&#231;&#227;o do criador de perfil a partir da linha de comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "método de criação de perfil de instrumentação"
  - "ferramentas de criação de perfil, método de instrumentação"
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Coletando dados de tempo detalhados para um aplicativo Web do ASP.NET usando o m&#233;todo de instrumenta&#231;&#227;o do criador de perfil a partir da linha de comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta seção descreve os procedimentos e as opções para coletar dados de desempenho detalhados para um aplicativo Web de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] usando a ferramenta de linha de comando de**VSPerfCmd** e o método de gerenciamento.  
  
> [!NOTE]
>  A ferramenta de **VSPerfCmd** proporciona acesso completo à funcionalidade de Ferramentas de Criação de Perfil, inclusive pausar e retomar, analisar e colete dados adicionais contadores de processador e de desempenho do windows.  Você também pode usar a ferramenta de linha de comando **VSPerfASPNETCmd** quando não precisar essa funcionalidade.  Em comparação com a ferramenta de linha de comando [VSPerfCmd](../profiling/vsperfcmd.md) , nenhuma variável de ambiente precisa ser definido, e reinicialize o computador não é necessário.  Para obter mais informações, consulte [Criação de perfil do site rápida com VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## Tarefas comuns  
  
|Tarefa|Conteúdo relacionado|  
|------------|--------------------------|  
|**Perfil de binários compilados estaticamente**|-   [Como instrumentar um aplicativo do ASP.NET compilado estaticamente e coletar dados de tempo detalhados](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)|  
|**Criados dinamicamente binários de perfil**|-   [Como instrumentar um aplicativo do ASP.NET compilado dinamicamente e coletar dados de tempo detalhados](../Topic/How%20to:%20Instrument%20a%20Dynamically%20Compiled%20ASP.NET%20Web%20Application%20and%20Collect%20Detailed%20Timing%20Data%20with%20the%20Profiler%20by%20Using%20the%20Command%20Line.md)|  
  
## Tarefas Relacionadas  
  
### Analisando aplicativos Web ASP.NET  
  
|Tarefa|Conteúdo relacionado|  
|------------|--------------------------|  
|**Perfile usando o método de amostragem**|-   [Coletando estatísticas do aplicativo usando amostragem](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Alocação de memória e coleta de lixo de perfil**|-   [Coletando dados de memória](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Conflito de recurso de perfil e atividade de thread**|-   [Coletando dados de simultaneidade](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### Analisar usando o método de gerenciamento  
  
|Tarefa|Conteúdo relacionado|  
|------------|--------------------------|  
|**Aplicativos autônomos de perfil \(cliente\)**|-   [Coletando dados de tempo detalhados usando a instrumentação](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Serviços de perfil**|-   [Coletando dados de tempo detalhados usando a instrumentação](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
  
### Criando perfil dos dados da instrumentação exibe e relatórios  
 [Exibições de dados do método de instrumentação](../profiling/instrumentation-method-data-views.md)