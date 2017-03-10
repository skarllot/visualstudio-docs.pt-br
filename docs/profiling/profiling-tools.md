---
title: "Ferramentas de Cria&#231;&#227;o de Perfil | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.diagnosticshub.overview"
ms.assetid: 0fb6cd5d-e16a-4526-84a5-19e63c625bc5
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Ferramentas de Cria&#231;&#227;o de Perfil
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ferramentas de criação de perfil e diagnóstico ajudarão\-lo a diagnosticar a memória e uso de CPU e outros problemas de nível de aplicativo. Com essas ferramentas, você pode acumular dados \(como valores de variáveis, chamadas de função e eventos\) ao longo do tempo em que você executar o aplicativo no depurador. Você pode exibir o estado do seu aplicativo em pontos diferentes durante a execução do seu código.  
  
 Confira o resumo na parte inferior para ver quais ferramentas estão disponíveis para o tipo de projeto \(por exemplo, área de trabalho, UWP, ASP.NET\).  
  
 Você pode acessar as ferramentas de criação de perfil usando **Depurar \/ Windows \/ Mostrar ferramentas de diagnóstico** para usar as ferramentas durante a sessão de depuração ou usando **Depurar \/ criador de perfil de desempenho...** para fazer uma análise de desempenho de foco. Consulte [Running Profiling Tools With or Without the Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md) para obter mais informações sobre as diferentes abordagens.  
  
 ![DebugDiagnosticsToolsMenu](../profiling/media/debugdiagnosticstoolsmenu.png "DebugDiagnosticsToolsMenu")  
  
 Consulte [O que há de novo nas ferramentas de criação de perfil](../profiling/what-s-new-in-profiling-tools.md) para saber mais sobre os novos recursos desta versão.  
  
 As seções a seguir descrevem as ferramentas de desempenho diferentes que estão disponíveis no Visual Studio.  
  
## Uso de memória  
 ![DiagMemorySmall](../profiling/media/diagmemorysmall.png "DiagMemorySmall")  
  
 Localizar vazamentos de memória e ineficiente de memória enquanto você estiver depurando com o **uso de memória** ferramenta. A ferramenta permite que você tire instantâneos do heap gerenciado e nativo de memória. Você pode usar essa ferramenta com aplicativos ASP.NET, aplicativos universais do Windows e aplicativos de desktop. O **uso de memória** ferramenta pode ser executada a **Ferramentas de diagnóstico** janela enquanto você está depurando \(**Debug \/ Windows \/ Mostrar ferramentas de diagnóstico**\) ou fora do depurador \(**Depurar \/ criador de perfil de desempenho...**\). Consulte  [Uso de memória](../profiling/memory-usage.md) e [Analisar o uso da memória sem depuração](../Topic/Memory%20Usage%20without%20Debugging1.md) para obter mais informações.  
  
## Uso da CPU  
 ![DiagCPUSmall](../profiling/media/diagcpusmall.png "DiagCPUSmall")  
  
 O **utilização de CPU** ferramenta mostra a você onde a CPU está gastando tempo executando C\+\+, c\# \/ VB e o código JavaScript.  Você pode usar essa ferramenta com área de trabalho e aplicativos universais do Windows, bem como serviços de aplicativos do Azure. O **uso de CPU** ferramenta pode ser executada a **Ferramentas de diagnóstico** janela enquanto você está depurando \(**Debug \/ Windows \/ Mostrar ferramentas de diagnóstico**\) ou fora do depurador \(**Depurar \/ criador de perfil de desempenho...**\). Consulte [Uso da CPU](../profiling/cpu-usage.md) para obter mais informações.  
  
## Performance Explorer  
 ![PerfTools](../profiling/media/perftools.png "PerfTools")  
  
 O **Performance Explorer** \(**Debug \/ Profiler \/ Performance Explorer**\) permite que você use várias ferramentas diferentes, incluindo **amostragem de CPU**,  **instrumentação**, **alocação de memória .NET**, e **contenção de recursos**. Você pode usar ferramentas do Gerenciador de desempenho com aplicativos de desktop e aplicativos ASP.NET, mas não os aplicativos universais do Windows. Para obter mais informações, consulte [Performance Explorer](../profiling/performance-explorer.md).  
  
## Uso de GPU  
 ![DiagGPUUsage](../profiling/media/diaggpuusage.png "DiagGPUUsage")  
  
 Use o [Uso de GPU](../debugger/gpu-usage.md) ferramenta para compreender melhor a utilização do hardware de alto nível do aplicativo Direct3D. Você pode usar essa ferramenta com a área de trabalho e aplicativos universais do Windows, mas não os aplicativos ASP.NET. O **uso de GPU** ferramenta pode ser executada a **Ferramentas de diagnóstico** janela enquanto você está depurando \(**Debug \/ Mostrar ferramentas de diagnóstico**\) ou fora do depurador \(**Debug \/ criador de perfil de desempenho...**\).  
  
## Linha do tempo do aplicativo  
 ![DiagAppTimeline](../profiling/media/diagapptimeline.png "DiagAppTimeline")  
  
 O [Linha do tempo do aplicativo](../profiling/application-timeline.md) ferramenta ajuda a melhorar o desempenho de aplicativos XAML, fornecendo uma exibição detalhada de seu consumo de recursos. Você pode usar o **aplicativo cronograma** com área de trabalho e aplicativos universais do Windows, mas não os aplicativos ASP.NET. O **linha do tempo do aplicativo** ferramenta pode ser executada a **Ferramentas de diagnóstico** janela \(**Debug \/ criador de perfil de desempenho...**\).  
  
## PerfTips  
 ![DiagPerfTips](../profiling/media/diagperftips.png "DiagPerfTips")  
  
 Quando o depurador interrompe a execução em um ponto de interrupção ou operação de revisão, o tempo decorrido entre a interrupção e o ponto de interrupção anterior aparece como uma dica na janela do editor. Essas [PerfTips](../profiling/perftips.md) ajudá\-lo a monitorar e analisar o desempenho de seu aplicativo enquanto você está depurando. Você pode ver **PerfTips** na área de trabalho, Windows Universal e aplicativos ASP.NET.  
  
## Memória de JavaScript  
 ![DiagJSMemory](../profiling/media/diagjsmemory.png "DiagJSMemory")  
  
 O [Memória de JavaScript](../profiling/javascript-memory.md) ferramenta lhe permite medir, avaliar e direcionar problemas relacionados ao desempenho no seu código com a coleta de informações de tempo na entrada e saída de cada função em seu aplicativo. Você pode usar essa ferramenta com aplicativos HTML Universal do Windows. O **temporização de função JavaScript** ferramenta pode ser executada a **Ferramentas de diagnóstico** janela \(**Debug \/ criador de perfil de desempenho...**\).  
  
## Capacidade de Resposta da Interface de Usuário HTML  
 ![DiagHTMLResp](../profiling/media/diaghtmlresp.png "DiagHTMLResp")  
  
 O [Capacidade de resposta da interface do usuário HTML](../profiling/html-ui-responsiveness.md) ferramenta o ajuda a isolar problemas de desempenho em seus aplicativos, incluindo a falta de capacidade de resposta, tempo, de carregamento lenta e freqüentam de atualizações visuais que são menores do que o esperado. Você pode usar essa ferramenta com aplicativos HTML Universal do Windows. O **capacidade de resposta de interface do usuário HTML** ferramenta pode ser executada a **Ferramentas de diagnóstico** janela \(**Debug \/ criador de perfil de desempenho...**\).  
  
## IntelliTrace  
 ![DiagIntelliTrace](../profiling/media/diagintellitrace.png "DiagIntelliTrace")  
  
 [IntelliTrace](../debugger/intellitrace.md) permite registrar eventos específicos, examinar dados de **locais** durante eventos do depurador e chamadas de função e depurar erros difíceis de reproduzir.  IntelliTrace é principalmente uma ferramenta de depuração, mas ela também fornece informações que podem ser usadas para investigações de desempenho. Você pode usar essa ferramenta no Visual Studio Enterprise somente com área de trabalho, Windows Universal e aplicativos ASP.NET c\#. Você pode encontrar o IntelliTrace no **Ferramentas de diagnóstico** janela enquanto você está depurando \(**Debug \/ Windows \/ Mostrar ferramentas de diagnóstico**\).  
  
## Criação de perfil na produção  
 A abordagem recomendada para criação de perfil na produção é o perfil do [linha de comando usando vsperf.exe](../profiling/using-the-profiling-tools-from-the-command-line.md) para coletar um perfil de CPU. Para suporte a criação de perfil remota no serviço de aplicativo do Azure, crie o perfil por meio de [Gerenciador de servidores ou o Portal de Kudu](https://azure.microsoft.com/en-us/blog/remote-profiling-support-in-azure-app-service/).  
  
## Qual ferramenta deverá usar?  
 Aqui está uma tabela que lista as diferentes ferramentas que o Visual Studio oferece e os diferentes tipos de projeto você pode usá\-los com:  
  
|Ferramenta de desempenho|Área de trabalho do Windows|Universal\/da Windows Store|ASP.NET|  
|------------------------------|---------------------------------|---------------------------------|-------------|  
|[Uso de memória](../profiling/memory-usage.md)|Sim|Sim|não|  
|[Uso da CPU](../profiling/cpu-usage.md)|Sim|Sim|Somente o serviço de aplicativo do Azure|  
|[Uso de GPU](../debugger/gpu-usage.md)|Sim|Sim|não|  
|[Linha do tempo do aplicativo](../profiling/application-timeline.md)|Sim|Sim|não|  
|[PerfTips](../profiling/perftips.md)|Sim|Sim para XAML, não para HTML|não|  
|[Performance Explorer](../profiling/performance-explorer.md)|Sim|não|Sim|  
|[IntelliTrace](../debugger/intellitrace.md)|.NET Enterprise somente|.NET Enterprise somente|.NET Enterprise somente|  
|[Capacidade de resposta da interface do usuário HTML](../profiling/html-ui-responsiveness.md)|não|Sim para HTML, não para XAML|não|  
|[Memória de JavaScript](../profiling/javascript-memory.md)|não|Sim para HTML, não para XAML|não|  
  
## Consulte também  
 [Visual Studio IDE](../ide/visual-studio-ide.md)