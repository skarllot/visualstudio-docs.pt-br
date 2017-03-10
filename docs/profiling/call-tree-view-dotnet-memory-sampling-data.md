---
title: "Exibi&#231;&#227;o de &#225;rvore de chamadas - dados de amostragem da mem&#243;ria do .NET do criador de perfil | Microsoft Docs"
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
  - "Exibição Árvore de Chamadas"
ms.assetid: fbb6cb60-420b-4ca9-8306-2494f7d321fe
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Exibi&#231;&#227;o de &#225;rvore de chamadas - dados de amostragem da mem&#243;ria do .NET do criador de perfil
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A exibição de árvore de chamada exibe os caminhos de execução da função que foram atravessados no aplicativo analisado.  A raiz da árvore é o ponto de entrada no aplicativo ou no componente.  Cada nó da função lista todas as funções que chamou e dados de alocação de memória do .NET sobre essas chamadas de função.  
  
 Os valores na exibição de árvore de chamada são para as instâncias da função que eram chamadas pela função pai da árvore de chamada.  Os valores de porcentagem são calculados comparando o valor da instância da função ao número total ou ao tamanho das alocações em analisar executado.  
  
## Destacando o Caminho Mais Ativo de Execução  
 A exibição de árvore de chamada pode expandir e realce o caminho de execução do processo ou função que criou o maior ou a maioria dos objetos de memória.  Para exibir o caminho o mais ativa, clique com o botão direito do mouse no processo ou da função, e clique em **Expanda o caminho quente**.  
  
## Definindo o nó raiz da árvore de chamada  
 Cada processo de analisar executado é exibido como um nó raiz.  Para definir o nó a partir da exibição de árvore da chamada para outro nó, clique com o botão direito do mouse no nó que você deseja definir como o nó de início e selecione **Raiz de conjunto**.  
  
 Quando você define o nó raiz, você eliminar todas as outras entradas da exibição exceto a subárvore do nó selecionado.  Você pode redefinir o nó raiz de volta ao nó que você estivesse exibindo; clique com o botão direito do mouse na janela de exibição de árvore de chamada e selecione **Redefinir a raiz**.  
  
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
|**Nível**|A profundidade da função na árvore de chamada.|  
|**Alocações Inclusivas**|O número de objetos que foram atribuídos por instâncias dessa função que eram chamadas pela função pai da árvore de chamada.  Esse número inclui as alocações que foram feitas por funções filhos.|  
|**% de Alocações Inclusivas**|A porcentagem de todos os objetos que foram criados em que foi executado analisar alocações inclusivo dessa função.|  
|**Alocações Exclusivas**|O número de objetos que foram atribuídos por instâncias dessa função que eram chamadas pela função pai da árvore de chamada.  Esse número não inclui as alocações que foram feitas por funções filhos.|  
|**% de Alocações Exclusivas**|A porcentagem de todos os objetos que foram criados em que foi executado analisar alocações exclusivas de instâncias de função que eram chamadas pela função pai da árvore de chamada.|  
|**Bytes Inclusivos**|O número de bytes na memória que foi atribuído por instâncias dessa função que eram chamadas pela função pai da árvore de chamada.  Esse número inclui as alocações que foram feitas por funções filhos.|  
|**% de Bytes Inclusivos**|A porcentagem de todos os bytes de memória que foi atribuído em que foi executado analisar alocações inclusivo dessa função.|  
|**Bytes Exclusivos**|O número de bytes na memória que foi atribuído por instâncias dessa função que eram chamadas pela função pai da árvore de chamada.  Esse número não inclui as alocações que foram feitas por funções filhos.|  
|**% de Bytes Exclusivos**|A porcentagem de todos os bytes de memória que foi atribuído em que foi executado analisar alocações exclusivas dessa função.|  
  
## Consulte também  
 [Exibição de árvore de chamadas \- instrumentação](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Exibição de árvore de chamadas](../profiling/call-tree-view-sampling-data.md)   
 [Exibição de árvore de chamadas](../profiling/call-tree-view-instrumentation-data.md)