---
title: "Como escolher métodos de coleta | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance tools, choosing collection method
- profiling tools, choosing collection method
- performance collection methods
ms.assetid: c87cfd3a-0fc7-49ae-9c05-d8480891cc63
caps.latest.revision: 34
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
ms.openlocfilehash: 36eb22c4f770d66584f3007786a63181f6826a6b

---
# <a name="how-to-choose-collection-methods"></a>Como escolher métodos de coleção
As ferramentas de criação de perfil do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dão suporte a três métodos de coleta de dados de desempenho: amostragem, instrumentação e simultaneidade. Você também pode usar o método de amostragem ou instrumentação para coletar dados de tempo de vida e de alocação de memória do .NET.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Você pode usar a propriedade **Método** da sessão de desempenho para especificar o método de coleta mais apropriado para o seu aplicativo. É possível definir o método de coleta no Assistente de Desempenho, do Gerenciador de Desempenho ou de páginas de propriedades de uma sessão de desempenho. Se você estiver usando ferramentas de linha de comando, consulte [Criação de perfil na linha de comando](../profiling/using-the-profiling-tools-from-the-command-line.md) para obter mais informações.  
  
## <a name="performance-wizard"></a>Assistente de Desempenho  
  
#### <a name="to-select-a-collection-method-using-the-performance-wizard"></a>Para selecionar um método de coleta usando o Assistente de Desempenho  
  
-   Na primeira página do assistente, selecione uma das seguintes opções:  
  
|Opção|Descrição|  
|------------|-----------------|  
|**Amostragem de CPU**|Coleta estatísticas de aplicativo que são úteis para a análise inicial e para analisar problemas de utilização de CPU.|  
|**Instrumentação**|Coleta dados de tempo detalhados que são úteis para análise concentrada e para analisar problemas de desempenho de entrada/saída.|  
|**Alocação de memória do .NET**|Coleta dados de alocação de memória do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] usando o método de criação de perfil de amostragem.|  
|**Simultaneidade**|Coleta dados de contenção de recursos numéricos.|  
  
## <a name="performance-explorer"></a>Performance Explorer  
  
#### <a name="to-select-a-collection-method-using-performance-explorer"></a>Para selecionar um método de coleta usando o Gerenciador de Desempenho  
  
1.  Na barra de ferramentas do **Gerenciador de Desempenho**, clique na seta ao lado da lista suspensa **Método**.  
  
2.  Clique no método de coleta que você preferir.  
  
## <a name="performance-session-property-pages"></a>Páginas de propriedades da Sessão de Desempenho  
  
#### <a name="to-select-the-sampling-or-instrumentation-method-using-performance-session-properties"></a>Para selecionar o método de amostragem ou de instrumentação usando propriedades da sessão de desempenho  
  
1.  No **Gerenciador de Desempenho**, selecione a sessão de desempenho.  
  
     Um nome de arquivo de sessão de desempenho tem uma extensão .psess.  
  
2.  Clique com o botão direito do mouse na sessão de desempenho e, em seguida, clique em **Propriedades**.  
  
3.  Nas **Páginas de Propriedades**, clique em **Geral**.  
  
4.  Clique no método de coleta que você preferir.  
  
    -   Para obter informações sobre as outras opções que estão disponíveis ao coletar dados de amostragem, consulte [Coletando estatísticas de desempenho usando amostragem](../profiling/collecting-performance-statistics-by-using-sampling.md)  
  
    -   Para obter informações sobre as outras opções que estão disponíveis ao coletar dados de amostragem, consulte [Coletando dados de tempo detalhados usando instrumentação](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md).  
  
#### <a name="to-select-net-memory-data-collection-by-using-performance-session-properties"></a>Para selecionar a coleção de dados de memória do .NET usando as propriedades da sessão de desempenho  
  
1.  No **Gerenciador de Desempenho**, selecione a sessão de desempenho.  
  
     Um nome de arquivo de sessão de desempenho tem uma extensão .psess.  
  
2.  Clique com o botão direito do mouse na sessão de desempenho e, em seguida, clique em **Propriedades**.  
  
3.  Nas **Páginas de Propriedades**, clique em **Geral**.  
  
4.  Clique em **Amostragem** ou **Instrumentação**.  
  
5.  Clique em **Coletar informações de alocação de objeto do .NET** para coletar o tamanho e o número de alocações de objeto do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
6.  (Opcional) Clique em **Também coletar informações de tempo de vida do objeto .NET** para coletar dados sobre as gerações de coleta de lixo nas quais a memória do objeto foi recuperada.  
  
     Para obter informações sobre as outras opções que estão disponíveis ao coletar dados de memória do .NET, consulte [Coletando a alocação de memória do .NET e os dados de tempo de vida](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md).  
  
#### <a name="to-select-concurrency-data-collection-by-using-performance-session-properties"></a>Para selecionar a coleta de dados de simultaneidade usando as propriedades da sessão de desempenho  
  
1.  No **Gerenciador de Desempenho**, clique com o botão direito do mouse na sessão de desempenho e, em seguida, clique em **Propriedades**.  
  
2.  Nas **Páginas de Propriedades**, clique em **Geral**.  
  
3.  Clique em **Simultaneidade**.  
  
## <a name="see-also"></a>Consulte também  
 [Configurando sessões de desempenho](../profiling/configuring-performance-sessions.md)   
 [Noções básicas sobre valores de dados de amostragem](../profiling/understanding-sampling-data-values.md)   
 [Propriedades da sessão de desempenho](../profiling/performance-session-properties.md)


<!--HONumber=Feb17_HO4-->


