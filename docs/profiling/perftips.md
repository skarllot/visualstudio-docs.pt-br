---
title: PerfTips | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
caps.latest.revision: 6
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
ms.sourcegitcommit: 65bceca75b87aaf187926ebbed1a54ce4f0e8eec
ms.openlocfilehash: db7c9121beea3b6a27a435680dfe01cbc8cba8b6

---
# <a name="perftips"></a>PerfTips
O depurador do Visual Studio *PerfTips* e as **Ferramentas de Diagnóstico** integradas ao depurador ajudam a monitorar e analisar o desempenho de seu aplicativo durante a depuração.  
  
 Embora as ferramentas de diagnóstico integradas ao depurador sejam uma ótima maneira de descobrir problemas de desempenho durante o desenvolvimento, o depurador pode exercer um impacto significativo sobre o desempenho do seu aplicativo. Para coletar dados de desempenho mais precisos, considere usar também as ferramentas de diagnóstico do Visual Studio que são executados fora do depurador como uma parte adicional das suas investigações de desempenho. Consulte [Executar ferramentas de criação de perfil com ou sem o depurador](../profiling/running-profiling-tools-with-or-without-the-debugger.md).  
  
## <a name="perftips"></a>PerfTips  
 Quando o depurador interrompe a execução em um ponto de interrupção ou operação passo a passo, o tempo decorrido entre a interrupção e o ponto de interrupção anterior aparece como uma dica na janela do editor. Para obter mais informações, consulte [PerfTips: informações de desempenho imediatas durante a depuração com o Visual Studio](http://blogs.msdn.com/b/visualstudioalm/archive/2014/08/18/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio.aspx).  
  
 ![PerfTip](../profiling/media/dbgdiag_perf_perftip.png "DBGDIAG_PERF_PerfTip")  
  
## <a name="diagnostics-tools-window"></a>Janela Ferramentas de Diagnóstico  
 Pontos de interrupção e dados de tempo associados são registrados na janela Ferramentas de Diagnóstico  
  
 O gráfico a seguir mostra a janela Ferramentas de Diagnóstico no Visual Studio 2015 Atualização 1:  
  
 ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
-   A linha do tempo **Eventos de Interrupção** marca os pontos de interrupção atingidos na sessão de depuração. Clique em um evento para selecioná-lo na lista de detalhes do **Depurador**.  
  
-   O gráfico **Utilização de CPU** mostra a alteração na utilização da CPU entre todos os núcleos de processador na sessão de depuração.  
  
-   A lista **Eventos** do painel de detalhes **Depurador** inclui itens para cada evento de interrupção.  
  
-   A coluna **Duração** de um evento de interrupção exibe o tempo decorrido entre o evento e o ponto de interrupção anterior.  
  
## <a name="turn-perftips-on-or-off"></a>Ativar ou desativar PerfTips  
 Para habilitar ou desabilitar PerfTips:  
  
1.  No menu **Depurar**, escolha **Opções**.  
  
2.  Marque ou desmarque **Mostrar tempo decorrido PerfTip durante a depuração**.  
  
## <a name="turn-the-diagnostic-tools-window-on-or-off"></a>Ativar ou desativar a janela de Ferramentas de Diagnóstico  
 Para habilitar ou desabilitar a janela de Ferramentas de Diagnóstico:  
  
1.  No menu **Depurar**, escolha **Opções**.  
  
2.  Marque ou desmarque **Habilitar ferramentas de diagnóstico durante a depuração**.


<!--HONumber=Feb17_HO4-->


