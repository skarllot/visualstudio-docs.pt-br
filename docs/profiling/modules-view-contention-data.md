---
title: "Exibi&#231;&#227;o de m&#243;dulos - dados de conten&#231;&#227;o do criador de perfil | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "exibição Módulos"
ms.assetid: 1a9aa122-2d8f-4a09-b503-92975aa6b648
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Exibi&#231;&#227;o de m&#243;dulos - dados de conten&#231;&#227;o do criador de perfil
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A exibição dos módulos de dados de simultaneidade vídeos de dados de contenção agrupados pelos módulos que foram amostrados nos dados de perfil.  Cada módulo é a raiz de uma árvore hierárquica.  As funções do módulo no qual os eventos de contenção ocorreram são listadas sob o nó do módulo.  
  
 Se a função executava seu próprio código quando um evento de contenção ocorreu, ou seja, a função estava na parte superior da pilha de chamadas, as linhas de origem e os endereços de instrução que executaram é listada no nó da função.  Como os dados são coletados para uma linha de origem ou um ponteiro de instrução quando a linha ou a instrução estiver em execução, inclusive e os valores exclusivos são sempre os mesmos para a linha dados e os dados da instrução.  
  
 A tabela a seguir descreve os valores das colunas na exibição dos módulos de dados de contenção.  
  
|Coluna|Descrição|  
|------------|---------------|  
|**Tempo bloqueados exclusivos**|-   Para uma função, o tempo que essa função esteve bloqueada de executar o código no corpo da função.  O tempo bloqueados em funções que eram chamadas pela função não estão incluídos.<br />-   Para um módulo, a soma da tentativa bloqueado hora de funções no módulo.<br />-   Para uma linha ou uma instrução, o tempo que essa linha ou instrução foi bloqueadas de executar.|  
|**Tempo bloqueados exclusivo %**|-   Para uma função ou um módulo, o percentual de todas as horas bloqueadas analisar executado em que o foi bloqueado hora exclusivo desse função ou módulo.<br />-   Para uma linha ou uma instrução, o percentual de todas as horas bloqueadas em analisar executado no qual essa linha ou instrução foi bloqueadas de executar.|  
|**Disputas exclusivas**|-   Para uma função, o número de vezes que a função foi bloqueada de executar o código no corpo da função.  As disputas em funções que eram chamadas pela função não são incluídas.<br />-   Para um módulo, a soma de disputas exclusivas de funções no módulo.<br />-   Para uma linha ou uma instrução, o número de vezes que a linha ou instrução foi bloqueadas de executar.|  
|**Disputas exclusivas %**|-   Para uma função ou um módulo, o percentual de todas as disputas analisar executado em que estavam disputas exclusivas deste função ou módulo.<br />-   Para uma linha ou uma instrução, o percentual de todas as disputas analisar executado em que foram disputas que foi bloqueada essa linha ou instrução de execução.|  
|**Tempo inclusive bloqueados**|-   Para uma função, o tempo que essa função ou uma função que é chamada por essa função foram bloqueadas de executar.<br />-   Para um módulo, a soma de tempo bloqueadas em que pelo menos uma função desse módulo estava na pilha.<br />-   Para uma linha ou uma instrução, o tempo que essa linha ou instrução foi bloqueadas de executar.|  
|**Tempo inclusive bloqueados %**|-   Para uma função ou um módulo, o percentual de todas as horas bloqueadas analisar executado em que foi bloqueado inclusive hora desse função ou módulo.<br />-   Para uma linha ou uma instrução, o percentual de todas as horas bloqueadas em analisar executado no qual essa linha ou executaram instrução.|  
|**Disputas inclusivos**|-   Para uma função, o número de vezes que a função ou uma função que é chamada por essa função foram bloqueadas de executar.<br />-   Para um módulo, o número de disputas em que pelo menos uma função desse módulo estava na pilha.<br />-   Para uma linha ou uma instrução, o número de vezes que a linha ou instrução foi bloqueadas de executar.|  
|**Disputas inclusivas %**|-   Para uma função ou um módulo, o percentual de todas as disputas analisar executado em que estavam disputas inclusivo desse função ou módulo.<br />-   Para uma linha ou uma instrução, o percentual de todas as horas bloqueadas em analisar executado no qual essa linha ou executaram instrução.|  
|**Número de Linha da Função**|O número de linhas do início desta função no arquivo fonte.|  
|**Nome do Módulo**|O nome do módulo que contém a função, a linha, ou o ponteiro de instrução.|  
|**Caminho do Módulo**|O caminho do módulo que contém o módulo, a função, a linha, ou o ponteiro de instrução.|  
|**Nome**|O nome do módulo ou da função.|  
|**Identificação do Processo**|A identificação do processo \(PID\) da execução de criação de perfil.|  
|**Nome do Processo**|O nome do processo.|  
|**Source File**|O arquivo de origem contendo a definição para essa função.|  
  
## Consulte também  
 [Como personalizar as colunas de exibição do relatório](../profiling/how-to-customize-report-view-columns.md)   
 [Exibição de módulos](../profiling/modules-view.md)   
 [Exibição de módulos \- instrumentação](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Exibição de módulos \- amostragem](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Exibição de módulos](../profiling/modules-view-instrumentation-data.md)   
 [Exibição de módulos](../profiling/modules-view-sampling-data.md)