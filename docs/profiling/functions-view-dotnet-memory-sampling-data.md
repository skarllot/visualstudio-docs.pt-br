---
title: "Exibição de Funções – Dados de Amostragem de Memória do .NET | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Functions view
ms.assetid: 5d9c6302-2ffd-430e-9535-13ce795f9f7c
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 6b76b0e648715cb52e6039dd02ae1eba04cd2dd4
ms.lasthandoff: 02/22/2017

---
# <a name="functions-view---net-memory-sampling-data"></a>Exibição de Funções – Dados de Amostragem de Memória do .NET
A exibição Funções dos dados de criação de perfil de alocação de memória do .NET que foram coletados usando o método de amostragem lista as funções que alocaram a memória durante a execução da criação de perfil e reporta o tamanho e quantidade de alocações.  
  
|Column|Descrição|  
|------------|-----------------|  
|**ID do Processo**|A ID de processo (PID) da criação de perfil.|  
|**Nome do Processo**|O nome do processo.|  
|**Nome do Módulo**|O nome do módulo que contém a função.|  
|**Caminho do Módulo**|O demarcador do módulo que contém a função.|  
|**Arquivo de Origem**|O arquivo de origem que contém a definição dessa função.|  
|**Nome da Função**|O nome totalmente qualificado da função.|  
|**Número de linha da função**|O número de linha do início dessa função no arquivo de origem.|  
|**Endereço da Função**|O endereço da função.|  
|**Alocações Inclusivas**|O número total de objetos que foram alocados nessa função e suas funções filho.|  
|**% de Alocações Inclusivas**|O percentual de todos os objetos que foram alocados na execução da criação de perfil que eram alocações inclusivas dessa função.|  
|**Alocações Exclusivas**|O número de objetos criados quando a função estava executando diretamente na parte superior da pilha de chamadas. Esse número não inclui objetos criados em funções filho.|  
|**% de Alocações Exclusivas**|O percentual de todos os objetos alocados na execução de criação de perfil que eram alocações exclusivas dessa função.|  
|**Bytes Inclusivos**|O número de bytes da memória que foram alocados por esta função e suas funções filho.|  
|**% de Bytes Inclusivos**|O percentual de todos os bytes de memória que foram alocados na execução de criação de perfil que eram bytes inclusivos dessa função.|  
|**Bytes Exclusivos**|O número de bytes da memória que foram alocados por esta função, mas não por suas funções filho.|  
|**% de Bytes Exclusivos**|O percentual de todos os bytes de memória que foram alocados na execução de criação de perfil que eram bytes exclusivos dessa função.|  
  
## <a name="see-also"></a>Consulte também  
 [Exibição de Funções – Instrumentação](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Exibição de Funções](../profiling/functions-view-sampling-data.md)   
 [Exibição Funções](../profiling/functions-view-instrumentation-data.md)
