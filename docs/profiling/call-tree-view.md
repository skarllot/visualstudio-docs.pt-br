---
title: "Exibi&#231;&#227;o de &#225;rvore de chamadas | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.calltree"
helpviewer_keywords: 
  - "Exibição Árvore de Chamadas"
  - "relatório de desempenho, Exibição Árvore de Chamadas"
  - "relatórios de ferramentas de criação de perfil, Exibição Árvore de Chamadas"
  - "ferramentas de criação de perfil, Exibição Árvore de Chamadas"
ms.assetid: b2dbc033-bf95-4d10-8e51-f9462979133e
caps.latest.revision: 34
caps.handback.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Exibi&#231;&#227;o de &#225;rvore de chamadas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A exibição de árvore de chamada exibe os caminhos de execução da função que foram atravessados no aplicativo analisado.  A raiz da árvore é o ponto de entrada no aplicativo ou no componente.  Cada nó da função lista todas as funções que chamaram e os dados de desempenho sobre essas chamadas de função.  
  
 A exibição de árvore do chamada também pode expandir e realce o caminho de execução de uma função que consome a maior parte do tempo ou seja provada com mais frequência.  Para exibir o caminho do mais caro, clique com o botão direito do mouse na função e clique em **Expanda o caminho quente**.  
  
 Cada processo de analisar executado é exibido como um nó raiz.  Você pode definir o nó de início da exibição de árvore de chamada clique com o botão direito do mouse no nó que você deseja definir como o nó de início e **Definir a raiz**selecione.  
  
 Quando você define o nó raiz, você eliminar todas as outras entradas da exibição exceto a subárvore do nó selecionado.  Você pode redefinir o nó raiz de volta ao nó que você estivesse exibindo.  Na janela de exibição de árvore da chamada, clique com o botão direito do mouse em e selecione **Raiz de redefinição**.  
  
 A exibição de árvore de chamada pode ser personalizado para adicionar ou remover colunas.  Clique com o botão direito do mouse em **Barra de título do nome da coluna**, e selecione **Adicionar\/remover colunas**.  
  
 A exibição de árvore de chamada pode ser configurado para a redução de ruído limitando a quantidade de dados que são apresentados.  Usando a redução de ruído, problemas de desempenho são mais proeminentes na exibição.  Quando problemas de desempenho são fáceis de distinguir, a análise é mais fácil.  Para obter mais informações, consulte [Como configurar redução de ruído em exibições de relatório](../profiling/how-to-configure-noise-reduction-in-report-views.md).  
  
> [!NOTE]
>  Se a redução de ruído está configurada para exibir um aviso quando estiver habilitada, uma barra de informações serão exibidas no relatório.  
  
 Para obter mais informações sobre as definições para colunas na exibição de árvore da chamada, consulte o seguinte:  
  
 [Exibição de árvore de chamadas](../profiling/call-tree-view-sampling-data.md)  
  
 [Exibição de árvore de chamadas](../profiling/call-tree-view-instrumentation-data.md)  
  
 [Exibição de árvore de chamadas \- amostragem](../profiling/call-tree-view-dotnet-memory-sampling-data.md)  
  
 [Exibição de árvore de chamadas](../profiling/call-tree-view-contention-data.md)  
  
## Consulte também  
 [Exibições de relatório de desempenho](../profiling/performance-report-views.md)   
 [Noções básicas sobre valores de dados de instrumentação](../profiling/understanding-instrumentation-data-values.md)   
 [Noções básicas sobre valores de dados de amostragem](../profiling/understanding-sampling-data-values.md)