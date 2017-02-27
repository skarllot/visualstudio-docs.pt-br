---
title: Como escolher eventos de amostragem | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.property.sampling
helpviewer_keywords:
- clock cycles sample event
- sample events, choosing
- profiling tools, sample events
- page faults sample event
- system calls sample event
- performance counter sample event
- performance tools, sample events
ms.assetid: ce7cb734-80ac-4930-a4ef-e24395e1cc07
caps.latest.revision: 23
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
ms.openlocfilehash: c5c031c5eb857e95af97a92500327088665e364d

---
# <a name="how-to-choose-sampling-events"></a>Como escolher eventos de amostragem
Por padrão, as ferramentas de criação de perfil do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] coletam dados de desempenho em um intervalo especificado como um número de ciclos de processador que são usados pelo processo analisado. O número padrão de ciclos em um intervalo é de 10.000.000, que é aproximadamente 0,01 segundos em um computador de 1 GH. Você pode alterar o número de ciclos em um intervalo e também pode alterar o evento de amostragem. Os eventos de amostragem a seguir estão disponíveis:  
  
-   Ciclos do relógio – para problemas associados à CPU.  
  
-   Falhas de página – para problemas relacionados à memória.  
  
-   Chamadas do sistema – para problemas relacionados a E/S.  
  
-   Contador de desempenho – contadores de CPU para problemas de baixo desempenho.  
  
> [!IMPORTANT]
>  Se você estiver coletando dados de memória do .NET (alocações, tempos de vida do objeto ou ambos) usando o método de amostragem, todos os eventos de amostragem especificados pelo usuário serão ignorados e os eventos de alocação de memória ou de coleta de lixo adequados ou ambos, serão usados para coletar dados.  
  
### <a name="to-select-a-sample-event"></a>Para selecionar um evento de amostragem  
  
1.  No **Gerenciador de Desempenho**, clique com o botão direito do mouse na sessão de desempenho e, em seguida, clique em **Propriedades**.  
  
2.  Nas **Páginas de Propriedades**, clique nas propriedades de **Amostragem**.  
  
3.  Na lista suspensa **Evento de amostra**, selecione o evento de amostragem que você deseja usar para criar o perfil de seu aplicativo.  
  
    > [!NOTE]
    >  Os **Contadores de desempenho disponíveis** serão habilitados somente se você selecionar **Contador de desempenho** na lista suspensa **Evento de amostra**.  
  
4.  Se você selecionar **Contador de desempenho**, selecione um contador de CPU específico no controle de exibição de árvore **Contadores de desempenho disponíveis**.  
  
    -   Os contadores no nó **Eventos Portáteis** estão disponíveis em todos os tipos de processadores.  
  
    -   Os contadores no nó **Eventos de Plataforma** são específicos para o processador no computador atual e podem não estar disponíveis em outros tipos de processadores.  
  
5.  Ao selecionar um evento de amostra, um valor de intervalo de amostragem padrão é exibido na caixa de texto **Intervalo de Amostragem**. Se necessário, insira o valor desejado na caixa de texto.  
  
## <a name="see-also"></a>Consulte também  
 [Configurando sessões de desempenho](../profiling/configuring-performance-sessions.md)   
 [Como escolher métodos de coleta](../profiling/how-to-choose-collection-methods.md)   
 [Contadores da CPU e do Windows](../profiling/cpu-and-windows-counters.md)   
 [Noções básicas sobre valores de dados de amostragem](../profiling/understanding-sampling-data-values.md)   
 [Criando perfil na linha de comando](../profiling/using-the-profiling-tools-from-the-command-line.md)


<!--HONumber=Feb17_HO4-->


