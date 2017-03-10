---
title: "Coletando dados de mem&#243;ria a partir de um aplicativo Web do ASP.NET usando a linha de comando do criador de perfil | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "método de criação de perfil de memória do .NET"
  - "ferramentas de criação de perfil, método de memória do .NET"
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Coletando dados de mem&#243;ria a partir de um aplicativo Web do ASP.NET usando a linha de comando do criador de perfil
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta seção descreve os procedimentos e as opções para coletar dados de tempo de vida de alocação de memória e de objeto para um aplicativo Web ASP.NET usando a ferramenta de linha de comando **VSPerfCmd** .  
  
> [!NOTE]
>  A ferramenta de **VSPerfCmd** proporciona acesso completo à funcionalidade de Ferramentas de Criação de Perfil, inclusive pausar e retomar, analisar e colete dados adicionais contadores de processador e de desempenho do windows.  Você também pode usar a ferramenta de linha de comando **VSPerfASPNETCmd** quando não precisar essa funcionalidade.  Em comparação com a ferramenta de linha de comando de [VSPerfCmd](../profiling/vsperfcmd.md) , nenhuma variável de ambiente precisa ser definido, e reinicialize o computador não é necessário.  Para obter mais informações, consulte [Criação de perfil do site rápida com VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## Tarefas comuns  
  
|Tarefa|Conteúdo relacionado|  
|------------|--------------------------|  
|**Anexe o profiler para um aplicativo em execução do ASP.NET**|-   [Como anexar o criador de perfil a um aplicativo Web do ASP.NET para coletar dados de memória](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|  
|**De ferramentas binários compilados estaticamente**|-   [Como instrumentar um aplicativo do ASP.NET compilado estaticamente e coletar dados de memória](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
|**Criados dinamicamente binários de ferramentas**|-   [Como instrumentar um aplicativo do ASP.NET compilado dinamicamente e coletar dados de memória](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## Tarefas Relacionadas  
  
### Analisando aplicativos Web ASP.NET  
  
|Tarefa|Conteúdo relacionado|  
|------------|--------------------------|  
|**Perfile usando o método de amostragem**|-   [Coletando estatísticas do aplicativo usando amostragem](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Perfile usando o método de instrumentação**|-   [Coletando dados de tempo detalhados usando a instrumentação](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**Conflito de recurso de perfil e atividade de thread**|-   [Coletando dados de simultaneidade](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### Analisando dados de memória do .NET Framework  
  
|Tarefa|Conteúdo relacionado|  
|------------|--------------------------|  
|**Aplicativos autônomos de perfil \(cliente\)**|-   [Coletando dados de memória do .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Serviços de perfil**|-   [Coletando dados de memória do .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### Analisando dados de memória de O exibe e relatórios  
 [Exibições de dados da memória do .NET](../profiling/dotnet-memory-data-views.md)  
  
## Referência  
 [Referência de ferramentas de criação de perfil de linha de comando](../profiling/command-line-profiling-tools-reference.md)