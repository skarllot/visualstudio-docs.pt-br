---
title: Como coletar dados do contador de CPU | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.property.cpucounters
helpviewer_keywords:
- profiling tools, using portable CPU counters
- performance tools, portable CPU counters
ms.assetid: 102fb6ca-5fbf-4b05-925f-56912ce3f44b
caps.latest.revision: 21
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
ms.openlocfilehash: eed9be16b8cf7487a29332e9b1adb054e0c7597c

---
# <a name="how-to-collect-cpu-counter-data"></a>Como coletar dados do contador de CPU
Um contador de evento de CPU é usado para coletar dados de desempenho específicos de hardware. Este tópico mostra como coletar dados do contador de eventos quando você usa a método de criação de perfil de instrumentação.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Dois tipos de eventos do contador de CPU ocorrem:  
  
-   Eventos portáteis – eventos de CPU que podem ser coletados, independentemente da CPU específica.  
  
-   Eventos de plataforma – eventos de CPU que estão acoplados a uma CPU específica.  
  
 Os eventos portáteis incluem eventos gerais, como Instruções Desativadas e Ciclos Não Interrompidos, eventos de buffer de CPU, eventos de ramificação e eventos de cache L2. Os contadores de evento de plataforma disponíveis são determinados pelo fabricante do processador.  
  
 Categorias de eventos podem ser compartilhadas entre contadores de plataforma e portáteis. Por exemplo, as seguintes categorias de dados são frequentemente comuns aos dois tipos:  
  
-   Eventos de memória.  
  
-   Eventos de front-end.  
  
-   Eventos de ramificação.  
  
 Você pode coletar dados do contador de desempenho de duas formas no Criador de perfil:  
  
-   Colete dados de um ou mais contadores ao analisar por instrumentação.  
  
-   Especifique um evento de contador como o intervalo de amostragem, quando você analisar por amostragem. Para obter mais informações, consulte [Como escolher os eventos de amostragem](../profiling/how-to-choose-sampling-events.md).  
  
### <a name="to-collect-cpu-performance-counter-data-when-you-profile-by-instrumentation"></a>Para coletar dados de contador de desempenho de CPU ao analisar por instrumentação  
  
1.  Nas **Páginas de Propriedade** da sessão de desempenho, clique em **Contadores de CPU.**  
  
2.  Selecione a caixa de seleção **Coletar Contadores de CPU**.  
  
3.  Expanda a árvore **Contadores de desempenho disponíveis** até localizar os eventos de amostragem que você deseja coletar.  
  
4.  Para cada evento que você deseja coletar, selecione o evento e, em seguida, clique na seta à direita para adicionar o evento à lista de **Contadores Selecionados**.  
  
    > [!NOTE]
    >  **Contadores de desempenho disponíveis** estará habilitada somente se você selecionar a caixa de seleção **Coletar Contadores de CPU**.  
  
## <a name="see-also"></a>Consulte também  
 [Configurando sessões de desempenho](../profiling/configuring-performance-sessions.md)   
 [Propriedades da sessão de desempenho](../profiling/performance-session-properties.md)   
 [Contadores da CPU e do Windows](../profiling/cpu-and-windows-counters.md)   
 [Como escolher eventos de amostragem](../profiling/how-to-choose-sampling-events.md)


<!--HONumber=Feb17_HO4-->


