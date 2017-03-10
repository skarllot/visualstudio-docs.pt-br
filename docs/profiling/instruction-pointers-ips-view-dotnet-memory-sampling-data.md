---
title: "Exibi&#231;&#227;o de ponteiros de instru&#231;&#227;o (IPs) - dados de amostragem da mem&#243;ria do .NET do criador de perfil | Microsoft Docs"
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
  - "exibição Ponteiros de Instrução"
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Exibi&#231;&#227;o de ponteiros de instru&#231;&#227;o (IPs) - dados de amostragem da mem&#243;ria do .NET do criador de perfil
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A exibição de IPs para os dados de criação de perfil de alocação de memória .NET que foram coletados usando o método de amostragem lista as instruções do assembly que atribuídas a memória durante analisar executado.  As colunas da exibição também listam o tamanho e o número de alocações.  
  
 Somente valores exclusivos são listados.  
  
|Coluna|Descrição|  
|------------|---------------|  
|**Identificação do Processo**|A identificação do processo \(PID\) da execução de criação de perfil.|  
|**Nome do Processo**|O nome do processo.|  
|**Nome do Módulo**|O nome do módulo que contém a instrução.|  
|**Caminho do Módulo**|O caminho do módulo que contém a instrução.|  
|**Source File**|O arquivo de origem que contém a instrução.|  
|**Nome da Função**|O nome da função.|  
|**Número de Linha da Função**|O número de linhas do início desta função no arquivo fonte.|  
|**Endereço da função**|O endereço inicial da função.|  
|**A linha de origem começa**|O número de linha inicial no arquivo de origem no qual a alocação ocorreu.|  
|**Linha de origem extremidade**|O número da linha final no arquivo de origem no qual a alocação ocorreu.|  
|**O caractere de origem começa**|O deslocamento de caractere na linha inicial do arquivo de origem no qual a alocação ocorreu.|  
|**Extremidade de caracteres de origem**|O deslocamento de caractere de término na linha do arquivo de origem no qual a alocação ocorreu.|  
|**Endereço de instrução**|O endereço da instrução.|  
|**Alocações Exclusivas**|O número total de objetos criados pela instrução.|  
|**% de Alocações Exclusivas**|A porcentagem de todos os objetos que foram criados em analisar executado que foi atribuído pela instrução.|  
|**Bytes Exclusivos**|O número de bytes de memória que foi atribuído analisar executado em que foi atribuído pela instrução.|  
|**% de Bytes Exclusivos**|A porcentagem de todos os bytes de memória que foi atribuído analisar executado em que foi atribuído pela instrução.|  
  
## Consulte também  
 [Exibição de ponteiros de instrução \(IPs\)](../profiling/instruction-pointers-ips-view-sampling-data.md)