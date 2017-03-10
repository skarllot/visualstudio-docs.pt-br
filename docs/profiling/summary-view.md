---
title: "Exibi&#231;&#227;o de resumo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.summary"
helpviewer_keywords: 
  - "relatório de desempenho, exibição resumida"
  - "relatórios de ferramentas de criação de perfil, Exibição resumida"
  - "ferramentas de criação de perfil, Exibição resumida"
  - "Exibição resumida"
ms.assetid: 98a1eb71-bbf5-4ce7-8559-cdc29f082c4b
caps.latest.revision: 37
caps.handback.revision: 37
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Exibi&#231;&#227;o de resumo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A exibição de resumo exibe informações sobre as funções ou os objetos de desempenho os mais caras em analisar executado.  Esta exibição fornece um gráfico de linha de tempo e dois ou mais lista de funções ou mais dos objetos caros com base em métricas de desempenho do método analisando.  Os dados dessa exibição dependem do método analisando que foi usado \(amostragem \(, ou\) simultaneidade e se a alocação de memória de O esteve coletada.  
  
 Para todas as exibições resumidos exceto a exibição resumida de dados de simultaneidade, o gráfico de linha de tempo na exibição de resumo mostra a utilização do processador \(CPU\) do aplicativo analisado sobre o tempo que analisar ocorreu.  
  
-   Se você especificar um segmento de tempo no gráfico, você pode reanalyze os dados para aquele segmento ou ampliar a exibição da linha de tempo ao segmento que você especificou.  Para obter mais informações, consulte [Como filtrar exibições de relatório a partir da linha do tempo de resumo](../Topic/How%20to:%20Filter%20Report%20Views%20from%20the%20Summary%20Timeline.md)  
  
-   Você pode clicar em uma função em uma lista de resumo da exibição para abrir a exibição de detalhes da função da função.  Você também pode clicar com o botão direito do mouse na função para outras opções de exibição.  
  
-   Para alterar o número de itens que aparecem na exibição resumo lista, abra o menu de **Ferramentas** , aponte para **Opções**, e clique em **Ferramentas de desempenho**.  Em **Configurações Gerais**, modifique a definição de **Número de exibição das funções em resumo** .  
  
## Notificações Links  
 Clique nos links na lista de notificação para definir as opções de exibição do relatório.  É a lista à direita do gráfico da linha do tempo.  
  
|||  
|-|-|  
|**Código do usuário não de apresentação**<br /><br /> **Mostrar apenas o código**|Não disponível para o código nativo ou para os dados de perfil que foram coletados usando o método de gerenciamento.  Alterna entre exibir apenas os dados do código do usuário \(**Mostrar apenas o código**\) e exibir dados de qualquer código, incluindo o código do sistema \(**Código do usuário não de apresentação**\).  Por padrão, os dados são limitados ao código do usuário.  Para alterar a configuração, consulte [Como filtrar exibições de relatório para exibir apenas meu código](../Topic/How%20to:%20Filter%20Profiling%20Tools%20Report%20Views%20to%20Display%20Just%20My%20Code.md).|  
|**Exibir a orientação**|Exibe avisos de regra de desempenho na janela de **Lista de Erros** .  Para obter mais informações, consulte [Usando regras de desempenho para analisar dados](../profiling/using-performance-rules-to-analyze-data.md)|  
  
## Relatório  
 Você pode clicar nos links na lista de relatório para abrir exibições diferentes e comparar, salvar, ou filtrar o relatório.  É a lista à direita do gráfico da linha do tempo.  
  
|||  
|-|-|  
|**Árvore cortada apresentação de chamada**|Exibe os caminhos os mais caros de execução no modo de exibição de árvore de chamada.  Para obter mais informações, consulte [Exibição de árvore de chamadas](../profiling/call-tree-view.md).|  
|**Direcionar linhas de apresentação**|Não disponível para os dados de perfil que foram coletados usando o método de gerenciamento.  Exibe as linhas do código\-fonte as mais caras nas linhas exibição.  Para obter mais informações, consulte [Exibição de linhas](../profiling/lines-view.md).|  
|**Compare relatórios**|Exibe a caixa de diálogo de **Selecionar arquivos de análise da comparação** onde você pode especificar outro arquivo de dados de perfil para comparar ao arquivo atual.  Para obter mais informações, consulte [Comparando arquivos de dados de desempenho](../profiling/comparing-performance-data-files.md).|  
|**Dados de relatório de exportação**|Exibe a caixa de diálogo de **Exportar Relatório** onde você pode especificar um ou mais exibições de relatório para salvar como o arquivo CSV \(.csv\) ou os arquivos .xml.  Para obter mais informações, consulte [How to: Export Profiling Tools Reports](http://msdn.microsoft.com/pt-br/174b5bd3-df9b-4fd4-88d4-76032ab90451).|  
|**Salve o relatório analisado**|Salva o arquivo de dados de perfil do atual como um arquivo de .vsps, que abre mais rápido na interface para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Para obter mais informações, consulte [How to: Save Analyzed Profiling Data Files](http://msdn.microsoft.com/pt-br/0340ddde-caf4-48ac-8af3-d15dcdade556).|  
|**Dados de relatório de filtro**|Exibe o painel analisando de filtro de relatório onde você pode especificar critérios para restringir os dados na visualização de relatório.  Para obter mais informações, consulte [Filtro de exibição do relatório de ferramentas de criação de perfil](../profiling/performance-report-view-filter.md)|  
|**Tela cheia de alternância**|\/desativar Ativa o modo de tela cheia para a visualização de relatório.|  
  
## Consulte também  
 [Exibição do Resumo](../profiling/summary-view-sampling-data.md)   
 [Exibição do Resumo](../profiling/summary-view-instrumentation-data.md)   
 [Exibição do Resumo](../profiling/summary-view-dotnet-memory-data.md)