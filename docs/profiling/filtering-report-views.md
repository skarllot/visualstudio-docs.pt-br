---
title: "Filtrando exibi&#231;&#245;es de relat&#243;rio de ferramentas de cria&#231;&#227;o de perfil | Microsoft Docs"
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
  - "ferramentas de criação de perfil, configurando"
ms.assetid: 820cf192-7fd6-4bee-9a51-aa69154aca85
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Filtrando exibi&#231;&#245;es de relat&#243;rio de ferramentas de cria&#231;&#227;o de perfil
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode aplicar filtros aos arquivos de dados de perfil para limitar os dados de perfil que são exibidos em visualizações de relatório de desempenho e exportados para arquivos de relatório.  Você pode limitar um relatório aos dados entre valores de carimbo de data\/hora, e você pode limitar os dados para os processos e a threads específicos.  Você pode salvar filtros em um arquivo e criar um filtro em um perfil de dados diferentes arquivo importando o filtro salvo.  
  
 Você também pode limitar um relatório em um segmento de tempo usando a linha de tempo gráfico na exibição resumida.  Consulte [Como filtrar exibições de relatório a partir da linha do tempo de resumo](../Topic/How%20to:%20Filter%20Report%20Views%20from%20the%20Summary%20Timeline.md).  
  
 Para excluir o sistema e o código de terceiros de um relatório, consulte [Como filtrar exibições de relatório para exibir apenas meu código](../Topic/How%20to:%20Filter%20Profiling%20Tools%20Report%20Views%20to%20Display%20Just%20My%20Code.md)  
  
## Procedimentos  
  
#### Para criar um filtro de relatório do profiler  
  
1.  Se a janela de filtro de visualização de relatório do desempenho não for exibida, clique em **Mostrar Filtro** na barra de ferramentas de visualização de relatório de desempenho.  
  
     O filtro de visualização de relatório de desempenho é uma tabela.  Cada linha da tabela representa uma cláusula de filtro.  Você pode adicionar tantas cláusulas como você deseja que a um filtro.  
  
2.  Para cada cláusula que você deseja adicionar a um filtro, selecione ou inserir valores nos seguintes campos de uma linha.  
  
    |Campo|Descrição|  
    |-----------|---------------|  
    |**E\/ou**|Escolha **E** se essa cláusula e a cláusula seguir devem ser verdadeiras corresponder a um resultado.  Escolha **Ou** se essa cláusula ou a cláusula seguir podem ser verdadeira corresponder a um resultado.|  
    |**Campo**|Selecione o campo de relatório a ser usado na cláusula de filtro exibida na lista de campos de dados.|  
    |**Operador**|Selecione o operador que especifica a relação que você deseja na cláusula entre o campo e o valor.<br /><br /> \= Iguais<br /><br /> \<\>  Não iguais<br /><br /> \<    Menor que<br /><br /> \>    Maior que<br /><br /> \<\= Menor que ou igual a<br /><br /> \>\= Maior que ou igual a|  
    |**Valor**|Selecione ou digite o valor para navegar.  Alguns campos listam os valores disponíveis para o campo.|  
  
#### Para criar um relatório do profiler filtro de visualização de relatório das marcas  
  
1.  **Marcas** Selecione na lista de **Modo de exibição atual** na barra de ferramentas de visualização de relatório de desempenho.  
  
     O relatório de perfil das marcas é exibido.  
  
2.  Selecione o ETW ou fazendo amostragem do mesmo que você deseja usar como ponto de partida do relatório.  
  
3.  Pressione e segure CTRL e clique no evento que deseja usar como o ponto final de relatório.  
  
4.  Clique com o botão direito do mouse em e clique em uma das seguintes opções:  
  
    -   **Adicionar o filtro nas marcas** cria as cláusulas de filtro que usam a coluna da marca como o campo de filtro.  
  
    -   **Adicionar o filtro em carimbos de data\/hora** cria as cláusulas de filtro que usam o carimbo de data\/hora na coluna de milissegundos desde que o campo de filtro.  
  
     As duas opções para o arquivo de dados em mesmos pontos iniciais e de extremidade.  Qualquer opção pode ser melhor se você exportar o filtro use em outros relatórios.  
  
#### Para carregar um filtro existente de um arquivo  
  
1.  Na barra de ferramentas de visualização de relatório de desempenho, clique em **Filtro de importação**.  
  
     A caixa de diálogo de **Filtro de carga** é exibida.  
  
2.  Especifique o local e o nome do arquivo de filtro \(.vspf\) para carregar.  
  
#### Para executar um filtro  
  
-   Na barra de ferramentas de visualização de relatório de desempenho, clique **Execute o filtro**.  
  
#### Para interromper um filtro que está demorando muito para executar  
  
-   Na barra de ferramentas de visualização de relatório de desempenho, clique em **Filtro de parada**.  
  
#### Para remover um filtro em uma visualização de relatório  
  
1.  Excluir linhas em cláusulas de filtro de visualização de relatório de desempenho.  
  
2.  Na barra de ferramentas de visualização de relatório de desempenho, clique **Execute o filtro**.  
  
#### Para salvar um filtro em um arquivo  
  
1.  Na barra de ferramentas de visualização de relatório de desempenho, clique em **Filtro de exportação**.  
  
     A caixa de diálogo de **Salvar o filtro** é exibida.  
  
2.  Especifique o local e o nome do arquivo de filtro \(.vspf\) para salvar.  
  
## Consulte também  
 [Personalizar o desempenho das ferramentas de modos de exibição de relatório](../profiling/customizing-performance-tools-report-views.md)