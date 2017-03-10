---
title: "Exibi&#231;&#227;o de fun&#231;&#245;es - dados de instrumenta&#231;&#227;o da mem&#243;ria de .NET do criador de perfil | Microsoft Docs"
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
ms.assetid: cd45b379-394b-4b71-828c-92cd89e46ae0
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Exibi&#231;&#227;o de fun&#231;&#245;es - dados de instrumenta&#231;&#227;o da mem&#243;ria de .NET do criador de perfil
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A exibição das funções dos dados de criação de perfil de alocação de memória .NET que foram coletados por meio do método da instrumentação lista as funções que atribuídas a memória durante analisar executado.  Uma linha da função informa o tamanho e número de alocações, e os dados de controle de tempo para a função.  
  
## Geral  
  
|Coluna|Descrição|  
|------------|---------------|  
|**Nome da Função**|O nome da função.|  
|**Endereço da função**|O endereço da função.|  
|**Número de Linha da Função**|O número de linhas do início desta função no arquivo fonte.|  
|**Número de Chamadas**|O número total de chamadas que são feitas nesta função.|  
|**Source File**|O arquivo de origem que contém a definição dessa função.|  
|**Nome do Módulo**|O nome do módulo que contém a função.|  
|**Caminho do Módulo**|O caminho do módulo que contém a função.|  
|**Identificação do Processo**|A identificação do processo \(PID\) da execução de criação de perfil.|  
|**Nome do Processo**|O nome do processo.|  
|**Sobrecarga de Sondagem Exclusiva de Tempo**|A sobrecarga de tempo para essa função devido à instrumentação.  A sondagem da sobrecarga foi subtraída de todos os tempos exclusivos.|  
|**Sobrecarga de Sondagem Inclusiva de Tempo**|A sobrecarga de tempo para essa função e suas funções filhos devido à instrumentação.  A sobrecarga de sondagem foi subtraída de todos os tempos inclusivos.|  
  
## Valores de memória .NET  
 Os valores inclusivos de memória .NET de uma função indicam o número \(alocações\) e o tamanho \(bytes\) dos objetos criados pela função e pelas funções do filho.  
  
 Os valores exclusivos de memória indicam o número e o tamanho dos objetos criados pela função e não pelas funções filhos.  
  
|Coluna|Descrição|  
|------------|---------------|  
|**Alocações Inclusivas**|O número total de objetos que foram criados nesta função e funções que eram chamadas por essa função.|  
|**% de Alocações Inclusivas**|A porcentagem de todos os objetos que foram atribuídos em que foi executado analisar alocações inclusivo dessa função.|  
|**Alocações Exclusivas**|O número total de objetos que foram criados quando a função estivesse executando o código no corpo da função.  Esse número não inclui objetos que foram criados em funções que eram chamadas por essa função.|  
|**% de Alocações Exclusivas**|A porcentagem de todos os objetos que foram criados em que foi executado analisar alocações exclusivas dessa função.|  
|**Bytes Inclusivos**|O número de bytes de memória que foi atribuído nessa função e funções que eram chamadas por essa função.|  
|**% de Bytes Inclusivos**|A porcentagem de todos os bytes de memória que foi atribuído em que foi executado analisar bytes inclusivos dessa função.|  
|**Bytes Exclusivos**|O número de bytes de memória que foi atribuído por essa função mas não por funções que eram chamadas por essa função.|  
|**% de Bytes Exclusivos**|A porcentagem de todos os bytes de memória que foi atribuído em que foi executado analisar bytes exclusivos dessa função.|  
  
## Valores Inclusivos Decorridos  
 Os valores inclusivos decorridos indicam o tempo que uma função estava na pilha de chamada.  O tempo incluem tempo que esteve gastou em funções e filho em chamadas para o sistema operacional, como alternâncias de contexto e operações de entrada\/saída.  
  
|Coluna|Descrição|  
|------------|---------------|  
|**Tempo Inclusivo Decorrido**|O tempo decorrido total inclusivo de todas as chamadas para essa função.|  
|**Tempo Inclusivo Decorrido %**|A porcentagem do total decorrido vezes inclusivo de analisar executado que foi gasto durante inclusivas decorridas dessa função.|  
|**Tempo Inclusivo Decorrido Médio**|A média tempo decorrido inclusivo de uma chamada para essa função.|  
|**Tempo Inclusivo Decorrido Máximo**|O tempo máximo decorrido inclusivo de uma chamada para essa função.|  
|**Tempo Inclusivo Decorrido Mínimo**|O tempo decorrido mínimo inclusivo de uma chamada para essa função.|  
  
## Valores Exclusivos Decorridos  
 Os valores exclusivos decorridos indicam o tempo que uma função estava executando diretamente na parte superior da pilha de chamadas.  O tempo incluem tempo em chamadas para o sistema operacional, como alternâncias de contexto e operações de entrada\/saída, mas não incluem o tempo gasto em funções que foram filhos.  
  
|Coluna|Descrição|  
|------------|---------------|  
|**Tempo Exclusivo Decorrido**|O tempo decorrido total exclusivas de todas as chamadas para essa função.|  
|**Tempo Exclusivo Decorrido %**|A porcentagem do total decorrido vezes exclusivas de analisar executado que foi gasto no tempo total decorrido exclusivas dessa função.|  
|**Tempo Exclusivo Decorrido Médio**|A média tempo decorrido exclusivas de uma chamada para essa função.|  
|**Tempo Exclusivo Decorrido Máximo**|O tempo máximo decorrido exclusivas de uma chamada para essa função.|  
|**Tempo Exclusivo Decorrido Mínimo**|O tempo decorrido mínimo exclusivas de uma chamada para essa função.|  
  
## Valores Inclusivos do Aplicativo  
 Os valores inclusivos do aplicativo indicam o tempo que uma função ficou na pilha de chamadas.  O tempo não inclui o tempo gasto em chamadas para o sistema operacional, como interruptores contextuais e operações entrada\/saída, mas inclui o tempo gasto em funções filhas.  
  
|Coluna|Descrição|  
|------------|---------------|  
|**Tempo Inclusivo do Aplicativo**|As vezes inclusivo do aplicativo total de todas as chamadas para essa função.|  
|**Tempo Inclusivo do Aplicativo %**|A porcentagem do total decorrido vezes inclusivo de analisar executado que foi gasto durante inclusivo do aplicativo total dessa função.|  
|**Tempo Inclusivo Médio do Aplicativo**|As vezes inclusivo do aplicativo médio de uma chamada para essa função.|  
|**Tempo Inclusivo Máximo do Aplicativo**|A hora do aplicativo inclusivo máximo de uma chamada para essa função.|  
|**Tempo Inclusivo Mínimo do Aplicativo**|A hora do aplicativo inclusivo mínimo de uma chamada para essa função.|  
  
## Valores Exclusivos do Aplicativo  
 Os valores exclusivos de aplicativo indica a hora em que uma função executava diretamente na parte superior da pilha de chamadas.  A hora não incluem o tempo que foram gasto em chamadas para o sistema operacional, como o contexto alternam e as operações de entrada\/saída, nem incluem o tempo gasto em funções que foram filhos.  
  
|Coluna|Descrição|  
|------------|---------------|  
|**Tempo Exclusivo do Aplicativo**|As vezes exclusivas do aplicativo total de todas as chamadas para essa função.|  
|**Tempo Exclusivo do Aplicativo %**|A porcentagem do total decorrido vezes exclusivas de analisar executado que foi gasto durante exclusivas do aplicativo total dessa função.|  
|**Tempo Exclusivo Médio do Aplicativo**|As vezes exclusivas do aplicativo médio de uma chamada para essa função.|  
|**Tempo Exclusivo Máximo do Aplicativo**|As vezes exclusivas do aplicativo máximo de uma chamada para essa função.|  
|**Tempo Exclusivo Mínimo do Aplicativo**|As vezes exclusivas do aplicativo mínimo de uma chamada para essa função.|  
  
## Consulte também  
 [Como personalizar as colunas de exibição do relatório](../profiling/how-to-customize-report-view-columns.md)   
 [Exibição de funções \- amostragem](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Exibição de funções](../profiling/functions-view-instrumentation-data.md)   
 [Exibição de funções](../profiling/functions-view-sampling-data.md)