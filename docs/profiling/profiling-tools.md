---
title: "Ferramentas de Criação de Perfil | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.diagnosticshub.overview
ms.assetid: 0fb6cd5d-e16a-4526-84a5-19e63c625bc5
caps.latest.revision: 20
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
ms.sourcegitcommit: 8f844c2d7d975476bc4c059d211a1d6cb0df64eb
ms.openlocfilehash: 4c995fb6df6316ce7f84fae7075b81063b54ebf7
ms.lasthandoff: 02/28/2017

---
# <a name="profiling-tools"></a>Ferramentas de Criação de Perfil
Ferramentas de Diagnóstico e Criação de Perfil ajudam você a diagnosticar o uso de memória e uso de CPU e outros problemas em nível de aplicativo. Com essas ferramentas, você pode acumular dados (como valores de variáveis, chamadas de função e eventos) ao longo do tempo em que você executar o aplicativo no depurador. Você pode exibir o estado do seu aplicativo em pontos diferentes durante a execução do seu código.  
  
 Confira o resumo na parte inferior para ver quais ferramentas estão disponíveis para o tipo de projeto (por exemplo, área de trabalho, UWP, ASP.NET).  
  
 Você pode acessar as ferramentas de criação de perfil usando **Depurar/Janelas/Mostrar Ferramentas de Diagnóstico** para usar as ferramentas durante a sessão de depuração ou você pode fazer uma análise post-mortem usando algumas outras abordagens.  Consulte [Executando ferramentas de criação de perfil com ou sem o depurador](../profiling/running-profiling-tools-with-or-without-the-debugger.md) para obter mais informações sobre as diferentes abordagens.
  
 ![DebugDiagnosticsToolsMenu](../profiling/media/debugdiagnosticstoolsmenu.png "DebugDiagnosticsToolsMenu")
  
 Consulte [O que há de novo nas ferramentas de criação de perfil](../profiling/what-s-new-in-profiling-tools.md) para saber mais sobre as novas funcionalidades desta versão.
  
 As seções a seguir descrevem as diferentes ferramentas de desempenho que estão disponíveis no Visual Studio.
  
## <a name="memory-usage"></a>Uso de Memória  
 ![DiagMemorySmall](../profiling/media/diagmemorysmall.png "DiagMemorySmall")  
  
 Localize vazamentos de memória e memória ineficiente enquanto você estiver depurando com a ferramenta **Uso da Memória**. A ferramenta permite que você tire instantâneos do heap de memória gerenciada e do heap de memória nativa. Você pode usar essa ferramenta com aplicativos ASP.NET, aplicativos universais do Windows e aplicativos da área de trabalho. A ferramenta **Uso da Memória** pode ser executada da janela **Ferramentas de Diagnóstico** enquanto você está depurando (**Depurar/Janelas/Mostrar Ferramentas de Diagnóstico**) ou fora do depurador (**Depurar/Criador de Perfil de Desempenho...**). Consulte [Uso da Memória](../profiling/memory-usage.md) e [Uso da Memória sem Depuração](../profiling/Memory-Usage-without-Debugging2.md) para obter mais informações.  
  
## <a name="cpu-usage"></a>Uso da CPU  
 ![DiagCPUSmall](../profiling/media/diagcpusmall.png "DiagCPUSmall")  
  
 A ferramenta **Uso da CPU** mostra em que a CPU está dedicando tempo a executar código C++, C#/VB e JavaScript.  Você pode usar essa ferramenta com aplicativos de área de trabalho e universais do Windows, bem como aplicativos do Serviço de Aplicativo do Azure e ASP.NET. A ferramenta **Uso de CPU** pode ser executada da janela **Ferramentas de Diagnóstico** enquanto você está depurando (**Depurar/Janelas/Mostrar Ferramentas de Diagnóstico**) ou fora do depurador (**Depurar/Criador de Perfil de Desempenho...**). Para obter mais informações, consulte o [Guia de Iniciantes para a Criação de Perfil de Desempenho](../profiling/beginners-guide-to-performance-profiling.md) e [Uso de CPU](../profiling/cpu-usage.md).
  
## <a name="gpu-usage"></a>Uso de GPU  
 ![DiagGPUUsage](../profiling/media/diaggpuusage.png "DiagGPUUsage")  
  
 Use a ferramenta [Uso de GPU](../debugger/gpu-usage.md) para compreender melhor a utilização do hardware de alto nível do aplicativo Direct3D. Você pode usar essa ferramenta com aplicativos universais do Windows e aplicativos da área de trabalho, mas não com aplicativos ASP.NET. A ferramenta **Uso de GPU** pode ser executada fora do depurador (**Depurar/Criador de Perfil de Desempenho...**).  
  
## <a name="application-timeline"></a>Linha do Tempo do Aplicativo  
 ![DiagAppTimeline](../profiling/media/diagapptimeline.png "DiagAppTimeline")  
  
 A ferramenta [Linha do Tempo do Aplicativo](../profiling/application-timeline.md) ajuda a melhorar o desempenho de aplicativos XAML fornecendo uma exibição detalhada do consumo de recursos por esses aplicativos. Você pode usar a **Linha do Tempo do Aplicativo** com aplicativos universais do Windows e aplicativos da área de trabalho, mas não com aplicativos ASP.NET. A ferramenta **Linha do Tempo do Aplicativo** pode ser executada fora do depurador (**Depurar/Criador de Perfil de Desempenho...**).
  
## <a name="perftips"></a>PerfTips  
 ![DiagPerfTips](../profiling/media/diagperftips.png "DiagPerfTips")  
  
 Quando o depurador interrompe a execução em um ponto de interrupção ou operação passo a passo, o tempo decorrido entre a interrupção e o ponto de interrupção anterior aparece como uma dica na janela do editor. Essas [PerfTips](../profiling/perftips.md) ajudam você a monitorar e analisar o desempenho de seu aplicativo enquanto você está depurando. Você pode ver **PerfTips** em aplicativos da área de trabalho, universais do Windows e ASP.NET.

## <a name="performance-explorer"></a>Performance Explorer  
 ![PerfTools](../profiling/media/perftools.png "PerfTools")  
  
 O **Gerenciador de Desempenho** (**Depurar/Criador de Perfil/Gerenciador de Desempenho**) permite que você use várias ferramentas diferentes, incluindo **Amostragem de CPU**, **Instrumentação**, **Alocação de Memória .NET** e **Contenção de Recursos**. Você pode usar ferramentas do Gerenciador de Desempenho com aplicativos de área de trabalho e aplicativos ASP.NET, mas não com aplicativos universais do Windows. Para obter mais informações, consulte [Gerenciador de Desempenho](../profiling/performance-explorer.md).

 > [!NOTE]
 > A menos que você deseje executar uma tarefa especializada como a instrumentação, use as ferramentas de diagnóstico como o uso de memória e o uso de CPU em vez do Gerenciador de Desempenho (que agora é uma ferramenta herdada).
  
## <a name="javascript-memory"></a>Memória JavaScript  
 ![DiagJSMemory](../profiling/media/diagjsmemory.png "DiagJSMemory")  
  
 A ferramenta [Memória JavaScript](../profiling/javascript-memory.md) permite localizar vazamentos de memória e uso ineficiente de memória nos aplicativos. A ferramenta permite que você tire instantâneos do heap de JavaScript. Você pode usar essa ferramenta com aplicativos HTML universais do Windows. A ferramenta **Memória JavaScript** pode ser executada fora do depurador (**Depurar/Criador de Perfil de Desempenho...**).  
  
## <a name="html-ui-responsiveness"></a>Capacidade de Resposta da Interface de Usuário HTML  
 ![DiagHTMLResp](../profiling/media/diaghtmlresp.png "DiagHTMLResp")  
  
 A ferramenta [Capacidade de resposta da interface do usuário HTML](../profiling/html-ui-responsiveness.md) ajuda você a isolar problemas de desempenho em seus aplicativos, incluindo a falta de capacidade de resposta, tempo de carregamento lento e atualizações visuais que são menos frequentes do que o esperado. Você pode usar essa ferramenta com aplicativos HTML universais do Windows. A ferramenta **Capacidade de Resposta de Interface do Usuário HTML** pode ser executada fora do depurador (**Depurar/Criador de Perfil de Desempenho...**).  
  
## <a name="intellitrace"></a>IntelliTrace  
 ![DiagIntelliTrace](../profiling/media/diagintellitrace.png "DiagIntelliTrace")  
  
 O [IntelliTrace](../debugger/intellitrace.md) lhe permite registrar eventos específicos, examinar os dados na janela **Locais** durante eventos do depurador e chamadas de função e depurar erros difíceis de reproduzir.  O IntelliTrace é principalmente uma ferramenta de depuração, mas ela também fornece informações que podem ser usadas para investigações de desempenho. Você pode usar essa ferramenta no Visual Studio Enterprise somente com aplicativos de área de trabalho, aplicativos universais do Windows e C# ASP.NET. Você pode encontrar o IntelliTrace na janela **Ferramentas de Diagnóstico** enquanto você está depurando (**Depurar/Janelas/Mostrar Ferramentas de Diagnóstico**).  
  
## <a name="profiling-in-production"></a>Criação de perfil na produção  
 A abordagem recomendada para criação de perfil na produção é criar o perfil por meio da [linha de comando usando vsperf.exe](../profiling/using-the-profiling-tools-from-the-command-line.md) para coletar um perfil de CPU. Para suporte à criação de perfil remota no Serviço de Aplicativo do Azure, crie o perfil por meio do [Gerenciador de Servidores ou do Portal Kudu](https://azure.microsoft.com/en-us/blog/remote-profiling-support-in-azure-app-service/).  
  
## <a name="which-tool-should-i-use"></a>Qual ferramenta devo usar?  
 Eis aqui uma tabela que lista as diferentes ferramentas que o Visual Studio oferece e os diferentes tipos de projeto com os quais você poderá usá-las:  
  
|Ferramenta de Desempenho|Área de Trabalho do Windows|Windows Universal/Store|ASP.NET|  
|----------------------|---------------------|------------------------------|-------------|  
|[Uso de Memória](../profiling/memory-usage.md)|sim|sim|sim|  
|[Uso da CPU](../profiling/cpu-usage.md)|sim|sim|sim|  
|[Uso de GPU](../debugger/gpu-usage.md)|sim|sim|no|  
|[Linha do tempo do aplicativo](../profiling/application-timeline.md)|sim|sim|no|  
|[PerfTips](../profiling/perftips.md)|sim|sim para XAML, não para HTML|no|  
|[Gerenciador de Desempenho](../profiling/performance-explorer.md)|sim|no|sim|  
|[IntelliTrace](../debugger/intellitrace.md)|Somente .NET Enterprise|Somente .NET Enterprise|Somente .NET Enterprise|  
|[Capacidade de Resposta de interface do usuário em HTML](../profiling/html-ui-responsiveness.md)|no|sim para HTML, não para XAML|no|  
|[Memória JavaScript](../profiling/javascript-memory.md)|no|sim para HTML, não para XAML|no|  
  
## <a name="see-also"></a>Consulte também  
 [Visual Studio IDE](../ide/visual-studio-ide.md)
