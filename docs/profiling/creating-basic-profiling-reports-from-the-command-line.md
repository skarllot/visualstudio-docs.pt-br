---
title: "Criando relat&#243;rios de cria&#231;&#227;o de perfil b&#225;sicos a partir da linha de comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Criando relat&#243;rios de cria&#231;&#227;o de perfil b&#225;sicos a partir da linha de comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tópico descreve os comandos básicos do VSPerfReport que geram os relatórios de valores separados por vírgula \(.csv\) de um arquivo de dados de criação de perfil .vsp ou .vsps.  Para obter uma descrição das opções de relatório, consulte [VSPerfReport](../profiling/vsperfreport.md).  
  
## Comandos do relatório  
 Use um dos comandos a seguir para criar um relatório para um arquivo de dados de criação de perfil especificado.  
  
 **VSPerfReport** `VSPFile` **\/Summary:All**  
 Gerencia todos os relatórios disponíveis para o arquivo .vsp ou .vsps.  
  
 **VSPerfReport** `VSPFile` **\/Summary:**`ReportType`\[,`ReportType`...\]  
 Gerencia os tipos de relatório especificados.  
  
 **VSPerfReport** `VSPFile` **\/CallTrace**  
 Gerencia um relatório que lista cada evento da coleção de dados.  Somente instrumentação.  
  
## Parâmetros de tipo de relatório de resumo  
 A tabela a seguir descreve os relatórios que são gerados pela opção especificada de tipo de relatório.  As colunas de um relatório dependem do método de criação de perfil que foi usado para coletar os dados.  
  
|Parâmetro de resumo|Descrição do relatório|Referência de relatório|  
|-------------------------|----------------------------|-----------------------------|  
|**CallerCallee**|Representa relações de pai\/filho entre as funções.|-   [Dados de Amostragem](../profiling/caller-callee-view-sampling-data.md)<br />-   [Dados de Instrumentação](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [Dados de amostragem de memória do .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [Dados de instrumentação de memória do .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [Dados de Contenção](../profiling/caller-callee-view-contention-data.md)|  
|**Function**|Lista os dados da análise por função.|-   [Dados de Amostragem](../profiling/functions-view-sampling-data.md)<br />-   [Dados de Instrumentação](../profiling/functions-view-instrumentation-data.md)<br />-   [Dados de amostragem de memória do .NET](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [Dados de instrumentação de memória do .NET](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [Dados de Contenção](../profiling/functions-view-contention-data.md)|  
|**CallTree**|Representa os caminhos de execução e os dados de criação de perfil de funções na execução da criação de perfil.|-   [Dados de Instrumentação](../profiling/call-tree-view-instrumentation-data.md)<br />-   [Dados de Amostragem](../profiling/call-tree-view-sampling-data.md)<br />-   [Dados de amostragem de memória do .NET](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [Dados de instrumentação de memória do .NET](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [Dados de Contenção](../profiling/call-tree-view-contention-data.md)|  
|**Counter**|Lista as marcas da análise e os valores do contador de desempenho do Windows que foram coletados durante a análise executada.|-   [Exibição de marcas](../profiling/marks-view.md)|  
|**Ip**|Lista os dados da análise por instrução.|-   [Dados de Amostragem](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [Dados de amostragem de memória do .NET](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [Dados de Contenção](../profiling/instruction-pointers-ips-view-contention-data.md)|  
|**Life**|Lista o tempo de vida dos objetos atribuídos.|-   [Exibição do tempo de vida do objeto](../profiling/object-lifetime-view.md)|  
|**Line**|Listas os dados da análise por linha de código\-fonte.|-   [Dados de Amostragem](../profiling/lines-view-sampling-data.md)<br />-   [Dados de amostragem de memória do .NET](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [Dados de Contenção](../profiling/lines-view-contention-data.md)|  
|**Header**|Informações do cabeçalho do arquivo de dados da criação de perfil.|Específico para o arquivo.|  
|**Mark**|Marcas da criação de perfil coletadas na execução da criação de perfil.|-   [Exibição de marcas](../profiling/marks-view.md)|  
|**Module**|Lista os dados da análise para os módulos.|-   [Dados de Amostragem](../profiling/modules-view-sampling-data.md)<br />-   [Dados de Instrumentação](../profiling/modules-view-instrumentation-data.md)<br />-   [Dados de amostragem de memória do .NET](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [Dados de instrumentação de memória do .NET](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [Dados de Contenção](../profiling/modules-view-contention-data.md)|  
|**Process**|Lista os dados da análise para os processos.|-   [Exibição de processo](../profiling/process-view.md)<br />-   [Dados de Contenção](../profiling/process-view-contention-data.md)|  
|**Thread**|Lista os dados da análise para os segmentos.|-   [Exibição de processo](../profiling/process-view.md)|  
|**Type**|Lista os dados de análise da alocação por tipo.|-   [Exibição de alocações](../profiling/dotnet-memory-allocations-view.md)|  
|**Contention**|Contenções de recursos.|-   [Contenções de recursos](../profiling/resource-contentions-view-contention-data.md)|  
|**RuleWarnings**|Lista os problemas das regras de desempenho.|-   Lista a CheckId, descrição, e o local de origem do problema da regra.|  
|**ETW**|Lista os eventos ETW \(Event Tracing for Windows\) coletados na execução da análise.|-   [Relatório de ETW](../profiling/event-tracing-for-windows-etw-report.md)|