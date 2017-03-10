---
title: "Exibi&#231;&#227;o do tempo de vida do objeto | Microsoft Docs"
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
  - "vs.performance.view.objectlifetime"
helpviewer_keywords: 
  - "tempo de vida, Objetos "
  - "exibição Tempo de Vida de Objetos"
  - "relatório de desempenho, exibição tempo de vida de objetos"
  - "relatórios de ferramentas de criação de perfil, exibição Tempo de Vida"
  - "ferramentas de criação de perfil, exibição Tempo de Vida"
ms.assetid: d0501fdd-4b3a-4e74-b6ac-51d950a2e15b
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Exibi&#231;&#227;o do tempo de vida do objeto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A exibição de tempo de vida do objeto está disponível quando **Também coletar dados de tempo de vida do objeto do .NET** é verificado nas páginas de propriedades da sessão de desempenho.  
  
 O coletor de lixo de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] gerencia a alocação e a versão de memória para seu aplicativo.  Para otimizar o desempenho do coletor de lixo, o heap gerenciado é dividido em três gerações: 0, 1 e 2.  O coletor de lixo de tempo de execução armazena novos objetos na geração 0.  Os objetos que sobrevivem a coleções são promovidos e armazenados nas gerações 1 e 2.  
  
 O coletor de lixo recupera a memória desalocando uma geração inteira de objetos.  Para os objetos criados pelo aplicativo pela análise, exibe de exibição de tempo de vida do objeto do número e o tamanho dos objetos e a geração na qual são recuperados.  
  
## Geral  
  
|Coluna|Descrição|  
|------------|---------------|  
|**Class Name**|O nome da classe do tipo atribuído.|  
|**Identificação do Processo**|A ID de processo de analisar executado.|  
|**Nome do Processo**|O nome do processo.|  
|**Nome do Módulo**|O nome do módulo que contém a função.|  
|**Caminho do Módulo**|O caminho do módulo que contém a função.|  
  
## Dados da instância  
 Os dados da instância indicam o número de objetos do tipo que foram criados em analisar executado, e a geração na qual os objetos tiverem sido desalocado pelo coletor de lixo.  
  
|Coluna|Descrição|  
|------------|---------------|  
|**Instâncias**|O número de alocações de objetos desse tipo.|  
|**O total instâncias %**|A porcentagem do número total de alocações que foram feitas em analisar executado.|  
|**Instâncias de Gen 0 coletadas**|O número de instâncias do tipo que foram desalocadas na geração 0 do algoritmo de coleta de lixo.|  
|**Instâncias de Gen 1 coletadas**|O número de instâncias do tipo que foram desalocadas na geração 1 do algoritmo de coleta de lixo.|  
|**Instâncias de Gen 2 coletadas**|O número de instâncias do tipo que foram desalocadas na geração 2 do algoritmo de coleta de lixo.|  
|**Instâncias tempo na extremidade**|O número de instâncias do tipo que não foi desalocada até o final da execução.|  
  
## Dados de tamanho \(bytes\)  
 Os dados de tamanho \(bytes\) indica o tamanho dos objetos do tipo que foram criados em analisar executado, e da quantidade de memória que eles são recuperados em cada geração na qual os objetos foram desalocados.  
  
|Coluna|Descrição|  
|------------|---------------|  
|**Total de bytes alocados**|O número total de bytes para todas as instâncias do tipo.|  
|**Total de bytes %**|A porcentagem do número total de bytes alocados analisar executado em que foi atribuído para instâncias desse tipo.|  
|**Bytes de Gen coletados 0**|O tamanho das instâncias do tipo que foram desalocadas na geração 0 do algoritmo de coleta de lixo.|  
|**Bytes de Gen coletados 1**|O tamanho das instâncias do tipo que foram desalocadas na geração 1 do algoritmo de coleta de lixo.|  
|**Gen 2 bytes coletados**|O tamanho das instâncias do tipo que foram desalocadas na geração 2 do algoritmo de coleta de lixo.|  
  
## Dados grandes de heap de objeto  
 O alocador de memória de O gerencia objetos muito grandes em um local que está separado do heap gerenciado padrão.  Dados grandes de heap de objeto indicam o número e o tamanho dos objetos do tipo que foram gerenciadas nesse local.  
  
|Coluna|Descrição|  
|------------|---------------|  
|**Grandes instâncias do heap do objeto coletadas**|O número de instâncias deste tipo que foram localizadas no heap de objeto grande e que foram coletadas em analisar executado.|  
|**Grandes bytes do heap de objeto coletados**|O tamanho, em bytes, das instâncias deste tipo que foram localizadas no heap de objeto grande e que foram coletadas em analisar executado.|  
  
## Consulte também  
 [Exibições de dados da memória do .NET](../profiling/dotnet-memory-data-views.md)