---
title: "Exibi&#231;&#227;o de fun&#231;&#245;es - dados de conten&#231;&#227;o do criador de perfil | Microsoft Docs"
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
  - "exibição Funções"
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Exibi&#231;&#227;o de fun&#231;&#245;es - dados de conten&#231;&#227;o do criador de perfil
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A visualização de relatório das funções de listas de dados de contenção as funções analisar executado em que foram bloqueadas de execução durante analisar executado.  
  
 A tabela a seguir explica os valores que são exibidos na exibição das funções de um arquivo de dados de perfil que seja coletado usando o método de simultaneidade.  
  
|Coluna|Descrição|  
|------------|---------------|  
|**Tempo bloqueados exclusivos**|A quantidade de tempo durante o qual esta função foi bloqueada de executar o código no corpo da função.  O tempo bloqueados em funções que eram chamadas pela função não estão incluídos.|  
|**Tempo bloqueados exclusivo %**|A porcentagem de todas as horas bloqueadas analisar executado em que o foi bloqueado hora exclusivo desta função.|  
|**Disputas exclusivas**|O número de vezes que a função foi bloqueada de executar o código no corpo da função.  As disputas em funções que eram chamadas pela função não são incluídas.|  
|**Disputas exclusivas %**|A porcentagem de todas as disputas na análise foi executado disputas exclusivas dessa função.|  
|**Endereço da função**|O endereço da função.|  
|**Nome da Função**|O nome completo da função.|  
|**Tempo inclusive bloqueados**|A hora em que essa função ou uma função que é chamada por essa função foram bloqueadas de executar.|  
|**Tempo inclusive bloqueados %**|A porcentagem de todas as horas bloqueadas analisar executado em que foi bloqueado inclusive hora desse função ou módulo.|  
|**Disputas inclusivos**|O número de vezes que a função ou uma função que é chamada por essa função foram bloqueadas de executar.|  
|**Disputas inclusivas %**|A porcentagem de todas as disputas analisar executado em que estavam disputas inclusivo desse função ou módulo.|  
|**Número de Linha da Função**|O número de linhas do início desta função no arquivo fonte.|  
|**Nome do Módulo**|O nome do módulo que contém a função.|  
|**Caminho do Módulo**|O caminho do módulo que contém a função.|  
|**Identificação do Processo**|A ID de O processo \(PID\) do processo no qual a função estava sendo executada.|  
|**Nome do Processo**|O nome do processo.|  
|**Source File**|O arquivo de origem contendo a definição para essa função.|  
  
## Consulte também  
 [Como personalizar as colunas de exibição do relatório](../profiling/how-to-customize-report-view-columns.md)   
 [Exibição de funções](../profiling/functions-view.md)   
 [Exibição de funções \- instrumentação](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Exibição de funções \- amostragem](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Exibição de funções](../profiling/functions-view-instrumentation-data.md)   
 [Exibição de funções](../profiling/functions-view-sampling-data.md)