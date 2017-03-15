---
title: "Modo de exibição de árvore de chamadas - Dados de contenção | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Call Tree view
ms.assetid: 9bd4bde2-2ca3-446c-9ccc-7421522e03ae
caps.latest.revision: 13
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
ms.openlocfilehash: 1628c295449ef57c60e57e3e2d5c4d52954155a0
ms.lasthandoff: 02/22/2017

---
# <a name="call-tree-view---contention-data"></a>Modo de exibição de árvore de chamadas - Dados de contenção
O modo de exibição de Árvore de Chamadas exibe os caminhos de execução de função que foram percorridos no aplicativo analisado. A raiz da árvore é o ponto de entrada do aplicativo ou do componente. Cada nó de função lista todas as funções que chamou, o número de vezes que a função foi bloqueada e por quanto tempo a função esteve bloqueada porque estava competindo por um recurso com outros threads ou processos.  
  
 Os valores no modo de exibição de Árvore de Chamadas são para as instâncias de função que foram chamadas pela função pai na árvore de chamadas. Os percentuais são calculados ao comparar o valor da instância de função ao número total de contenções na execução da criação de perfil.  
  
## <a name="highlighting-the-execution-hot-path"></a>Realce do afunilamento de execução  
 O modo de exibição de árvore de chamadas pode expandir e realçar o caminho de execução do processo ou da função que criou a maior parte das contenções.  
  
-   Para exibir o caminho mais ativo, clique com o botão direito do mouse no processo ou na função e, em seguida, clique em **Expandir Afunilamento**.  
  
## <a name="setting-the-call-tree-root-node"></a>Configuração do nó raiz da árvore de chamadas  
 Cada processo na execução de criação de perfil aparece como um nó raiz. Para definir o nó inicial do modo de exibição de Árvore de Chamadas, clique com o botão direito do mouse no nó que você deseja definir como o nó inicial e, em seguida, clique em **Definir Raiz**.  
  
 Ao definir o nó raiz, você elimina todas as outras entradas da visualização, com exceção da subárvore do nó selecionado. Para redefinir o nó raiz de volta para o nó original, clique com botão direito do mouse na janela modo de exibição de Árvore de Chamadas e, em seguida, clique em **Redefinir Raiz**.  
  
|Column|Descrição|  
|------------|-----------------|  
|**Tempo Bloqueado Exclusivo**|O tempo em que as instâncias dessa função nesse caminho de execução estiveram bloqueadas durante a execução da criação de perfil. O tempo não inclui o período de bloqueio de funções filho que foram chamadas pela função.|  
|**% de Tempo Bloqueado Exclusivo**|O percentual de todo o tempo bloqueado na execução da criação de perfil que representou o tempo bloqueado exclusivo para essa função nesse contexto.|  
|**Contenções Exclusivas**|O número de contenções que ocorreram em instâncias dessa função nesse caminho de execução. O número não inclui contenções de funções filho chamadas pela função.|  
|**% de Contenções Exclusivas**|A porcentagem de todas as contenções na execução da criação de perfil que eram exclusivas das instâncias dessa função e foram chamadas pela função pai na árvore de chamada.|  
|**Endereço da Função**|O endereço da função.|  
|**Nome da Função**|O nome totalmente qualificado da função.|  
|**Tempo Bloqueado Inclusivo**|O tempo total em que as instâncias dessa função nesse caminho de execução estiveram bloqueadas durante a execução da criação de perfil. O tempo inclui o período de bloqueio de funções filho chamadas pela função.|  
|**% de Tempo Bloqueado Inclusivo**|O percentual de todo o tempo bloqueado na execução da criação de perfil que representou o tempo bloqueado inclusivo das instâncias dessa função nesse caminho de execução.|  
|**Contenções Inclusivas**|O número total de contenções que bloquearam instâncias dessa função nesse caminho de execução. O número inclui as contenções de funções filho chamadas pela função.|  
|**% de Contenções Inclusivas**|O percentual de todas as contenções na execução da criação de perfil que eram inclusivas das instâncias dessa função nesse caminho de execução.|  
|**Nível**|O nível da função na árvore de chamadas. Somente em relatórios de linha de comando VSReport. Para obter mais informações, consulte [VSPerfReport](../profiling/vsperfreport.md).|  
|**Número de linha da função**|O número de linha do início dessa função no arquivo de origem.|  
|**Nome do Módulo**|O nome do módulo que contém a função.|  
|**Caminho do Módulo**|O demarcador do módulo que contém a função.|  
|**ID do Processo**|A ID de processo (PID) da criação de perfil.|  
|**Nome do Processo**|O nome do processo.|  
|**Arquivo de Origem**|O arquivo de origem que contém a definição dessa função.|  
  
## <a name="see-also"></a>Consulte também  
 [Como personalizar as colunas de exibição do relatório](../profiling/how-to-customize-report-view-columns.md)   
 [Modo de exibição de árvore de chamadas](../profiling/call-tree-view.md)   
 [Modo de exibição de árvore de chamadas – instrumentação](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Modo de exibição de árvore de chamadas – amostragem](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [Modo de exibição de árvore de chamadas](../profiling/call-tree-view-instrumentation-data.md)   
 [Modo de exibição de árvore de Chamadas](../profiling/call-tree-view-sampling-data.md)
