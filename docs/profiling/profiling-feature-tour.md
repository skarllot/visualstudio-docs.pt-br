---
title: "Tour pelos recursos de criação de perfil | Microsoft Docs"
ms.custom: 
ms.date: 02/03/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugger
ms.assetid: d2ee0301-ea78-43d8-851a-71b7b2043d73
caps.latest.revision: 1
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
ms.sourcegitcommit: 46788b9980e487d6a6b914212d638a25cf32f9c3
ms.openlocfilehash: e9c8b43df9495d256b245b185eebb714e6b1f335
ms.lasthandoff: 03/01/2017

---
# <a name="profiling-feature-tour"></a>Tour pelos recursos de criação de perfil

O Visual Studio fornece uma variedade de ferramentas de criação de perfil para ajudá-lo a diagnosticar diferentes tipos de problemas de desempenho, dependendo do tipo do aplicativo.

As ferramentas de criação de perfil que podem ser acessadas durante uma sessão de depuração estão disponíveis na janela Ferramentas de Diagnóstico. A janela Ferramentas de Diagnóstico é exibida automaticamente, a menos que tenha sido desativada. Para abrir a janela, clique em **Depurar/Windows/Mostrar Ferramentas de Diagnóstico**. Com a janela aberta, é possível selecionar ferramentas para as quais você deseja coletar dados.

![Ferramentas de Diagnóstico](../profiling/media/prof-tour-diagnostic-tools.png "Ferramentas de Diagnóstico")

Durante a depuração, é possível usar a janela **Ferramentas de Diagnóstico** para analisar o uso da CPU e de memória e exibir os eventos que mostram informações relacionadas ao desempenho.

![Resumo das Ferramentas de Diagnóstico](../profiling/media/prof-tour-cpu-and-memory-graph.gif "Resumo das Ferramentas de Diagnóstico")

A janela **Ferramentas de Diagnóstico** costuma ser a maneira preferencial de criar perfil de aplicativos, mas também é possível fazer uma análise post-mortem do aplicativo. Se desejar obter mais informações sobre diferentes abordagens, consulte [Executando ferramentas de criação de perfil com ou sem o depurador](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="analyze-cpu-usage"></a>Analisar o uso de CPU

A ferramenta Uso da CPU é um bom lugar para começar a analisar o desempenho do aplicativo. Ela informará mais sobre os recursos de CPU que o aplicativo está consumindo. Para obter um passo a passo mais detalhado da ferramenta Uso da CPU, consulte o [Guia do iniciante à criação de perfil de desempenho](../profiling/beginners-guide-to-performance-profiling.md).

Na exibição **Resumo** das Ferramentas de Diagnóstico, escolha **Habilitar Criação de Perfil da CPU** (é necessário estar em uma sessão de depuração).

![Habilitar Uso da CPU das Ferramentas de Diagnóstico](../profiling/media/prof-tour-enable-cpu-profiling.png "Habilitar Uso da CPU das Ferramentas de Diagnóstico")

Para usar a ferramenta com mais eficiência, defina dois pontos de interrupção no código: um no início e outro no final da função ou na região de código que você deseja analisar. Examine os dados de criação de perfil quando eles estiverem em pausa no segundo ponto de interrupção.

A exibição **Uso da CPU** mostra uma lista de funções ordenadas pela execução mais longa, com a função de execução mais longa na parte superior. Isso pode ajudar a levá-lo para as funções em que estão ocorrendo afunilamentos de desempenho.

![Uso da CPU das Ferramentas de Diagnóstico](../profiling/media/prof-tour-cpu-usage.png "Uso da CPU das Ferramentas de Diagnóstico")

Clique duas vezes em uma função de interesse e você verá uma exibição de três painéis mais detalhada, com a função selecionada no centro da janela, a função de chamada à esquerda e as funções chamadas à direita. A seção **Corpo da função** também mostra o tempo total (e o percentual de tempo) gasto no corpo da função, excluindo o tempo gasto nas funções de chamada e nas funções chamadas. Esses dados podem ajudá-lo a avaliar se a própria função é um afunilamento de desempenho.

![Exibição Computador Chamado do Chamador das Ferramentas de Diagnóstico](../profiling/media/prof-tour-cpu-usage-caller-callee.png "Exibição Computador Chamado do Chamador das Ferramentas de Diagnóstico")

## <a name="analyze-memory-usage"></a>Analisar o uso de memória

A janela Ferramentas de Diagnóstico também permite avaliar o uso de memória no aplicativo. Por exemplo, é possível examinar o número e tamanho dos objetos no heap. Para obter instruções mais detalhadas para analisar a memória, consulte [Uso de memória](../profiling/memory-usage.md).

Para analisar o uso de memória, você precisa obter pelo menos um instantâneo de memória durante a depuração. Em geral, a melhor maneira de analisar a memória é usar dois instantâneos: o primeiro, logo antes de um problema de memória suspeito e o segundo instantâneo, logo após a ocorrência de um problema de memória suspeito. Depois, é possível exibir uma comparação dos dois instantâneos e ver exatamente o que mudou.

![Usar Instantâneos das Ferramentas de Diagnóstico](../profiling/media/prof-tour-take-snapshots.gif "Usar Instantâneos das Ferramentas de Diagnóstico")

Ao selecionar um dos links a seta, você terá uma exibição diferencial do heap (uma seta vermelha para cima ![Aumento do Uso de Memória](../profiling/media/prof-tour-mem-usage-up-arrow.png "Aumento do Uso de Memória") mostra uma contagem crescente de objetos – à esquerda – ou um tamanho crescente de heap – à direita). Se você clicar no link à direita, terá uma exibição diferencial do heap, ordenada por objetos com maior aumento de tamanho de heap. Isso pode ajudá-lo a identificar problemas de memória. Por exemplo, na ilustração abaixo, os bytes usados por objetos `ClassHandlersStore` aumentaram em 3.492 bytes no segundo instantâneo.

![Exibição Comparação de Heap das Ferramentas de Diagnóstico](../profiling/media/prof-tour-mem-usage-diff-heap.png "Exibição Comparação de Heap das Ferramentas de Diagnóstico")

Se você clicar no link à esquerda, na exibição **Uso de Memória**, a exibição do heap será organizada pela contagem de objetos: os objetos de um tipo específico com maior aumento em número são mostrados na parte superior (classificados pela coluna **Comparação de Contagem**).

## <a name="examine-performance-events"></a>Examinar eventos de desempenho

A exibição **Eventos** das Ferramentas de Diagnóstico mostra diferentes eventos que ocorrem durante a depuração, como a configuração de um ponto de interrupção ou uma operação de execução de código em etapas. É possível verificar informações como a duração do evento (medido da última pausa do depurador ou da inicialização do aplicativo). Por exemplo, se você executar o código em etapas (F10, F11), a exibição **Eventos** mostrará a duração de tempo de execução do aplicativo da operação de etapa anterior à etapa atual.

![Exibição Eventos das Ferramentas de Diagnóstico](../profiling/media/prof-tour-events.png "Exibição Eventos das Ferramentas de Diagnóstico")

 > [!NOTE]
 > Se você tiver o Visual Studio Enterprise, também poderá ver [eventos do IntelliTrace](../debugger/intellitrace.md) nessa guia.

Os mesmos eventos também são mostrados no Editor de Código, que podem ser exibidos como PerfTips.

![Tour pela criação de perfil – PerfTips](../profiling/media/prof-tour-perf-tips.png "Tour pela criação de perfil – PerfTips")

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>Examinar o desempenho de interface do usuário e eventos de acessibilidade (UWP)

Nos aplicativos UWP, é possível habilitar a **Análise de Interface do Usuário** na janela Ferramentas de Diagnóstico. A ferramenta pesquisa problemas comuns de desempenho ou de acessibilidade, mostrando-os na exibição **Eventos** durante a depuração. As descrições de eventos fornecem informações que podem ajudar a resolver problemas.

![Exibição Eventos de Análise de Interface do Usuário da Ferramentas de Diagnóstico](../profiling/media/prof-tour-ui-analysis.png "Exibição Eventos de Análise de Interface do Usuário da Ferramentas de Diagnóstico")

## <a name="profile-release-builds-without-the-debugger"></a>Builds de versão de perfil sem o depurador

Ferramentas de criação de perfil como Uso da CPU e Uso de Memória podem ser usadas com o depurador (consulte as seções anteriores) ou é possível executar ferramentas de criação de perfil usando o Criador de Perfil de Desempenho, que se destina a fornecer análise para builds de **Versão**. No Criador de Perfil de Desempenho, é possível coletar informações de diagnóstico durante a execução do aplicativo e, em seguida, examinar as informações coletadas depois que o aplicativo é interrompido. Para obter mais informações sobre essas diferentes abordagens, consulte [Executando ferramentas de criação de perfil com ou sem o depurador](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

![Criador de Perfil de Desempenho](../profiling/media/prof-tour-performance-profiler.png "Criador de Perfil de Desempenho")

Abra o Criador de Perfil de Desempenho escolhendo **Depurar/Criador de Perfil de Desempenho**.

A janela permitirá selecionar várias ferramentas de criação de perfil em alguns cenários. Ferramentas como Uso da CPU podem fornecer dados complementares que podem ser usados para ajudar na análise.

## <a name="analyze-resource-consumption-xaml"></a>Analisar o consumo de recursos (XAML)

Em aplicativos XAML, como aplicativos WPF da área de trabalho do Windows e aplicativos da Windows Store, é possível analisar o consumo de recursos usando a ferramenta Linha de Tempo do Aplicativo. Por exemplo, é possível analisar o tempo gasto pelo aplicativo para preparar quadros de interface do usuário (layout e renderização), atender a solicitações de rede e de disco e em cenários como inicialização do aplicativo, carregamento de página e redimensionamento do Windows. Para usar a ferramenta, escolha **Linha do Tempo do Aplicativo** no Criador de Perfil de Desempenho e, em seguida, escolha **Iniciar**. No aplicativo, percorra o cenário com um problema de consumo de recursos suspeito e escolha **Parar coleta** para gerar o relatório.

Taxas de quadros baixas no gráfico **Taxa de transferência visual** podem corresponder aos problemas visuais vistos ao executar o aplicativo. Da mesma forma, números elevados no gráfico **Utilização de thread de interface do usuário** também podem corresponder a problemas de capacidade de resposta da interface do usuário. No relatório, é possível selecionar um período com um problema de desempenho suspeito e, em seguida, examinar as atividades detalhadas de thread de interface do usuário na exibição Detalhes da linha do tempo (painel inferior).

![Tour pela criação de perfil – Linha do Tempo do Aplicativo](../profiling/media/prof-tour-application-timeline.gif "Tour pela criação de perfil – Linha do Tempo do Aplicativo")

Na exibição Detalhes da linha do tempo, você encontrará informações como o tipo de atividade (ou o elemento de interface do usuário envolvido) junto com a duração da atividade. Por exemplo, na ilustração, um evento **Layout** de um controle Grade usa 57,53 ms.

Para obter mais informações, consulte [Linha do Tempo do Aplicativo](../profiling/application-timeline.md).

## <a name="analyze-gpu-usage-direct3d"></a>Analisar o uso da GPU (Direct3D)

Em aplicativos Direct3D (os componentes Direct3D devem estar no C++), é possível examinar a atividade na GPU e analisar problemas de desempenho. Para obter mais informações, consulte [Uso da GPU](../debugger/gpu-usage.md). Para usar a ferramenta, escolha **Uso da GPU** no Criador de Perfil de Desempenho e, em seguida, escolha **Iniciar**. No aplicativo, percorra o cenário de interesse na criação de perfil e, em seguida, escolha **Parar coleta** para gerar um relatório.

Ao selecionar um período nos gráficos e escolher **Exibir detalhes**, uma exibição detalhada será exibida no painel inferior. Na exibição detalhada, é possível examinar as atividades que estão ocorrendo em cada CPU e GPU. Selecione eventos no painel inferior para obter pop-ups na linha do tempo. Por exemplo, selecione o eventos **Presente** para exibir pop-ups da chamada **Presente**. (As linhas verticais Vsync cinza-claras podem ser usadas como referência para entender se algumas chamadas **Presente** não têm Vsync. Deve haver uma chamada **Presente** entre cada dois Vsyncs para que o aplicativo atinja progressivamente 60 FPS.)

![Diagnóstico Uso da GPU](../profiling/media/prof-tour-gpu-usage.png "Diagnóstico Uso da GPU")

Também é possível usar os gráficos para determinar se há afunilamentos de desempenho limitados à CPU ou à GPU.

## <a name="analyze-performance-javascript"></a>Analisar o desempenho (JavaScript)

Para aplicativos HTML Universais do Windows, é possível usar as ferramentas Memória JavaScript e Capacidade de Resposta de Interface do Usuário HTML.

A ferramenta Memória JavaScript é semelhante à ferramenta Uso de Memória disponível para outros tipos de aplicativos. É possível usar essa ferramenta para entender o uso de memória e encontrar perdas de memória no aplicativo. Para obter mais detalhes sobre a ferramenta, consulte [Memória JavaScript](../profiling/javascript-memory.md).

![DiagJSMemory](../profiling/media/diagjsmemory.png "DiagJSMemory")

Para diagnosticar a capacidade de resposta de interface do usuário, tempo de carregamento lento e atualizações lentas de visual em aplicativos HTML Universais do Windows, use a ferramenta Capacidade de Resposta de Interface do Usuário HTML. O uso é semelhante à ferramenta Linha do Tempo do Aplicativo para outros tipos de aplicativos. Para obter mais informações, consulte [Capacidade de resposta de interface do usuário HTML](../profiling/html-ui-responsiveness.md).

![DiagHTMLResp](../profiling/media/diaghtmlresp.png "DiagHTMLResp")

## <a name="analyze-network-usage-uwp"></a>Analisar o uso de rede (UWP)

Em aplicativos UWP, é possível analisar as operações de rede executadas usando a API `Windows.Web.Http`. Essa ferramenta pode ajudá-lo a resolver problemas, como problemas de acesso e autenticação, uso de cache incorreto e desempenho insatisfatório de exibição e download. Para usar a ferramenta, escolha **Rede** no Criador de Perfil de Desempenho e, em seguida, escolha **Iniciar**. No aplicativo, percorra o cenário que usa `Windows.Web.Http` e escolha **Parar coleta** para gerar o relatório.

![Diagnóstico Uso de Rede](../profiling/media/prof-tour-network-usage.png "Diagnóstico Uso de Rede")

Selecione uma operação na exibição de resumo para exibir mais detalhes.

![Diagnóstico Detalhes de Uso de Rede](../profiling/media/prof-tour-network-usage-details.png "Diagnóstico Detalhes de Uso de Rede")

Para obter mais informações, consulte [Uso de rede](../profiling/network-usage.md).

## <a name="analyze-performance-legacy-tools"></a>Analisar o desempenho (ferramentas herdadas)

Se você precisar de recursos, como instrumentação, que não estão atualmente presentes nas ferramentas Uso da CPU ou Uso de Memória, e estiver executando aplicativos de área de trabalho ou aplicativos ASP.NET, poderá usar o Gerenciador de Desempenho para a criação de perfil. (Sem suporte em aplicativos UWP). Para obter mais informações, consulte [Gerenciador de Desempenho](../profiling/performance-explorer.md)

![Gerenciador de Desempenho](../profiling/media/prof-tour-performance-explorer.png "Gerenciador de Desempenho")

## <a name="see-also"></a>Consulte também  
 [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md)
