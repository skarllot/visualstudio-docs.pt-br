---
title: "Coletando dados de simultaneidade para um serviço usando a linha de comando do criador de perfil | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 4e8eaa90e6f54710b9a7c31010b08f29197c3317

---
# <a name="collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Coletando dados de simultaneidade para um serviço usando a linha de comando do criador de perfil
O método de simultaneidade das Ferramentas de Criação de Perfil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permite coletar dados de contenção de recursos e dados de atividade do thread que mostram a utilização da CPU, contenção e migração do thread, atrasos na sincronização, áreas de ES sobrepostas e outros eventos do sistema.  
  
> [!NOTE]
>  Os recursos de segurança aprimorados no Windows 8 e no Windows Server 2012 exigiram alterações significativas na maneira como o criador de perfil do Visual Studio coleta dados nessas plataformas. Os aplicativos da Windows Store também requerem novas técnicas de coleta. Consulte [Ferramentas de desempenho em aplicativos do Windows 8 e do Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Tarefas comuns  
  
|Tarefa|Conteúdo relacionado|  
|----------|---------------------|  
|**Attach to a running .NET service (Anexar a um serviço do .NET em execução)**|-   [How to: Attach the Profiler to a .NET Service to Collect Concurrency Data (Como anexar o criador de perfil a um serviço do .NET para coletar dados de simultaneidade)](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Add tier-interaction data (Adicionar dados de interação de camada)**|-   [Coletando dados de interação entre camadas](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Anexar a um serviço do C/C++ em execução**|-   [How to: Attach the Profiler to a Native Service to Collect Concurrency Data (Como anexar o criador de perfil a um serviço nativo para coletar dados de simultaneidade)](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Tarefas relacionadas  
  
### <a name="profiling-windows-services"></a>Criando o perfil de Serviços Microsoft Windows  
  
|Tarefa|Conteúdo relacionado|  
|----------|---------------------|  
|**Criar perfil usando o método de amostragem**|-   [Coletando estatísticas do aplicativo usando amostragem](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**Criar perfil usando o método de instrumentação**|-   [Coletando dados de tempo detalhados usando a instrumentação](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**Criar o perfil de alocação de memória e coleta de lixo do .NET**|-   [Coletando dados de memória do .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### <a name="profiling-concurrency-data"></a>Criando o perfil de dados de simultaneidade  
  
|Tarefa|Conteúdo relacionado|  
|----------|---------------------|  
|**Aplicativos Autônomos de Perfil**|-   [Coletando dados de simultaneidade](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Criar o perfil de aplicativos Web ASP.NET**|-   [Coletando dados de simultaneidade](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-concurrency-data-views-and-reports"></a>Analisando modos de exibição e relatórios de Dados de Simultaneidade  
 [Exibições de dados da contenção de recurso](../profiling/resource-contention-data-views.md)  
  
 [Visualização Simultânea](../profiling/concurrency-visualizer.md)  
  
## <a name="reference"></a>Referência  
 [Referência de ferramentas de criação de perfil de linha de comando](../profiling/command-line-profiling-tools-reference.md)


<!--HONumber=Feb17_HO4-->


