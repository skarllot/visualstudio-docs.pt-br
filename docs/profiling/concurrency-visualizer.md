---
title: "Visualização Simultânea | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.performance.viewnavigation
- vs.cv.overview
- vs.cv.performance.gettingstarted
- vs.cv.gettingstarted
helpviewer_keywords:
- Concurrency Visualizer, Concurrency Visualizer
ms.assetid: ae5879a0-1e1a-455a-ba72-148e57f59289
caps.latest.revision: 31
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
ms.openlocfilehash: 88a2158cac4a2e44d50d31c5bffba2a9e8055fa2

---
# <a name="concurrency-visualizer"></a>Visualizador de Simultaneidade
> [!NOTE]
>  A Visualização Simultânea é uma extensão opcional do Visual Studio. Baixe a Visualização Simultânea e a Coleção de Ferramentas de Visualização Simultânea nos seguintes links:  
>   
>  -   Baixe a extensão              [Visualização Simultânea](https://visualstudiogallery.msdn.microsoft.com/a6c24ce9-beec-4545-9261-293061436ee9).  
> -   Baixe a              [Coleção de Ferramentas da Visualização Simultânea para Visual Studio 2015](http://www.microsoft.com/en-in/download/details.aspx?id=49103).  
>   
>      O [CVCollectionCmd (Utilitário de Linha de Comando Visualização Simultânea)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md) permite coletar rastreamentos na linha de comando que podem ser exibidos na Visualização Simultânea para Visual Studio 2015. A ferramenta pode ser usada em computadores que não tenham o Visual Studio instalado.  
  
 É possível usar a Visualização Simultânea para ver como é o desempenho do seu aplicativo multithread. As exibições na Visualização Simultânea oferecem dados gráficos, tabulares e textuais que mostram as relações temporais entre os threads no programa e o sistema como um todo. É possível usar a Visualização Simultânea para localizar afunilamentos de desempenho, subutilização da CPU, contenção de thread, migração de thread entre núcleos, atrasos de sincronização, atividade do DirectX, áreas de E/S sobrepostas e outras informações. As exibições fornecem dados em que você pode agir vinculando sua saída gráfica a pilhas de chamadas e código-fonte.  
  
 A Visualização Simultânea conta com a funcionalidade [Rastreamento de Eventos para Windows](http://go.microsoft.com/fwlink/?LinkId=234579).  
  
> [!NOTE]
>  A Visualização Simultânea não oferece suporte a projetos Web.  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Exibição da utilização](../profiling/utilization-view.md)|Descreve como exibir e analisar a atividade do sistema entre todos os processadores.|  
|[Exibição de Threads](../profiling/threads-view-parallel-performance.md)|Descreve como analisar as interações entre threads no programa.|  
|[Exibição de núcleos](../profiling/cores-view.md)|Descreve como analisar a migração de thread entre núcleos.|  
|[Padrões comuns para aplicativos multi-threaded com mau comportamento](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md)|Descreve diversos padrões em comum e mostra como eles são exibidos na Visualização Simultânea.|  
|[Desenvolvimento paralelo no blog do Visual Studio](http://go.microsoft.com/fwlink/?LinkId=235385)|Dá dicas e práticas recomendadas para a Visualização Simultânea.|  
|[Exibições de relatório de desempenho](../profiling/performance-report-views.md)|Fornece informações de referência sobre os relatórios e as exibições das Ferramentas de Criação de Perfil do Visual Studio.|  
|[SDK da Visualização Simultânea](../profiling/concurrency-visualizer-sdk.md)|Descreve como instrumentalizar o código-fonte para exibir informações adicionais na Visualização Simultânea.|  
|[Utilitário de linha de comando da Visualização Simultânea (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|Descreve como usar o utilitário de linha de comando Visualização Simultânea (CVCollectionCmd.exe) para coletar e processar rastreamentos em máquinas que não tenham o Visual Studio.|  
  
## <a name="see-also"></a>Consulte também  
 [Ferramentas de Criação de Perfil](../profiling/profiling-tools.md)


<!--HONumber=Feb17_HO4-->


