---
title: "Exibi&#231;&#227;o de fun&#231;&#245;es - dados de amostra da mem&#243;ria do .NET do criador de perfil | Microsoft Docs"
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
ms.assetid: 5d9c6302-2ffd-430e-9535-13ce795f9f7c
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Exibi&#231;&#227;o de fun&#231;&#245;es - dados de amostra da mem&#243;ria do .NET do criador de perfil
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A exibição das funções dos dados de criação de perfil de alocação de memória .NET que foram coletados usando o método de amostragem lista as funções que atribuídas a memória durante analisar executado e informa o tamanho e o número de alocações.  
  
|Coluna|Descrição|  
|------------|---------------|  
|**Identificação do Processo**|A identificação do processo \(PID\) da execução de criação de perfil.|  
|**Nome do Processo**|O nome do processo.|  
|**Nome do Módulo**|O nome do módulo que contém a função.|  
|**Caminho do Módulo**|O caminho do módulo que contém a função.|  
|**Source File**|O arquivo de origem contendo a definição para essa função.|  
|**Nome da Função**|O nome completo da função.|  
|**Número de Linha da Função**|O número de linhas do início desta função no arquivo fonte.|  
|**Endereço da função**|O endereço da função.|  
|**Alocações Inclusivas**|O número total de objetos que foram atribuídos a essa função e em suas funções do filho.|  
|**% de Alocações Inclusivas**|A porcentagem de todos os objetos que foram atribuídos em que foi executado analisar alocações inclusivo dessa função.|  
|**Alocações Exclusivas**|O número de objetos que foram criados quando a função estava sendo executada diretamente na parte superior da pilha de chamadas.  Esse número não inclui objetos que foram criados em funções filhos.|  
|**% de Alocações Exclusivas**|A porcentagem de todos os objetos que foram atribuídos em que foi executado analisar alocações exclusivas dessa função.|  
|**Bytes Inclusivos**|O número de bytes de memória que foi atribuído por essa função e pelas funções do filho.|  
|**% de Bytes Inclusivos**|A porcentagem de todos os bytes de memória que foi atribuído em que foi executado analisar bytes inclusivos dessa função.|  
|**Bytes Exclusivos**|O número de bytes de memória que foi atribuído por essa função mas não pelas funções filhos.|  
|**% de Bytes Exclusivos**|A porcentagem de todos os bytes de memória que foi atribuído em que foi executado analisar bytes exclusivos dessa função.|  
  
## Consulte também  
 [Exibição de funções \- instrumentação](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Exibição de funções](../profiling/functions-view-sampling-data.md)   
 [Exibição de funções](../profiling/functions-view-instrumentation-data.md)