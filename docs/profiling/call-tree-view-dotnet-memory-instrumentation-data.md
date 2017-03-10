---
title: "Exibi&#231;&#227;o de &#225;rvore de chamadas - dados de instrumenta&#231;&#227;o da mem&#243;ria do .NET do criador de perfil | Microsoft Docs"
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
ms.assetid: dd359707-245a-4a36-8305-2e980b9edd53
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Exibi&#231;&#227;o de &#225;rvore de chamadas - dados de instrumenta&#231;&#227;o da mem&#243;ria do .NET do criador de perfil
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A exibição de árvore da chamada de dados de perfil de alocação de memória .NET que foram coletados por meio do método da instrumentação exibe os caminhos de execução da função que foram atravessados no aplicativo analisado.  A raiz da árvore é o ponto de entrada no aplicativo ou no componente.  Cada nó da função lista todas as funções que chamou, e memória de .NET e dados de controle de tempo para a função.  
  
 Os valores na exibição de árvore de chamada são para as instâncias da função que eram chamadas pela função pai da árvore de chamada.  Os valores de porcentagem são calculados comparando o valor da instância da função ao número total ou ao tamanho das alocações em analisar executado.  
  
## Destacando o Caminho Mais Ativo de Execução  
 A exibição de árvore de chamada pode expandir e realce o caminho de execução do processo ou função que criou o maior ou a maioria dos objetos de memória.  Para exibir o caminho o mais ativa, clique com o botão direito do mouse no processo ou da função, e clique em **Expanda o caminho quente**.  
  
## Definindo o nó raiz da árvore de chamada  
 Cada processo de analisar executado é exibido como um nó raiz.  Você pode definir o nó a partir da exibição de árvore de chamada clique com o botão direito do mouse no nó que você deseja definir como o nó de início, e selecionando **Raiz de conjunto**.  
  
 Quando você define o nó raiz, você eliminar todas as outras entradas da exibição exceto a subárvore do nó selecionado.  Você pode redefinir o nó raiz de volta ao nó que você estivesse exibindo; clique com o botão direito do mouse na janela de exibição de árvore de chamada e selecione **Raiz de redefinição**.  
  
## Geral  
  
|Coluna|Descrição|  
|------------|---------------|  
|**Nome da Função**|O nome da função.|  
|**Endereço da função**|O endereço da função.|  
|**Número de Linha da Função**|O número de linhas do início desta função no arquivo fonte.|  
|**Número de Chamadas**|O número total de chamadas feitas à essa função.|  
|**Source File**|O arquivo de origem contendo a definição para essa função.|  
|**Nome do Módulo**|O nome do módulo que contém a função.|  
|**Caminho do Módulo**|O caminho do módulo que contém a função.|  
|**Identificação do Processo**|A identificação do processo \(PID\) da execução de criação de perfil.|  
|**Nome do Processo**|O nome atribuído ao processo.|  
|**Sobrecarga de Sondagem Exclusiva de Tempo**|A sobrecarga de tempo para essa função que é gerada por WMI.  A sondagem da sobrecarga foi subtraída de todos os tempos exclusivos.|  
|**Sobrecarga de Sondagem Inclusiva de Tempo**|A sobrecarga de tempo para essa função e suas funções filhos que é gerada por WMI.  A sobrecarga de sondagem foi subtraída de todos os tempos inclusivos.|  
|**Tipo**|O contexto da função:<br /><br /> -   **0** \- a função atual<br />-   **1** \- uma função que chama a função atual<br />-   **2** \- uma função que é chamada pela função atual<br /><br /> Somente nos relatórios de linha de comando [VSPerfReport](../profiling/vsperfreport.md).|  
|**Nome da Função Raiz**|O nome da função atual.  Somente nos relatórios de linha de comando [VSPerfReport](../profiling/vsperfreport.md).|  
  
## Valores de memória .NET  
 Os valores inclusivos de memória .NET de uma função indicam o número \(alocações\) e o tamanho \(bytes\) dos objetos criados pela função e a funções que eram chamadas pela função.  
  
 Os valores exclusivos de memória indicam o número e o tamanho dos objetos criados pelo código no corpo da função e não por funções que eram chamadas pela função.  
  
|Coluna|Descrição|  
|------------|---------------|  
|**Alocações Inclusivas**|O número de objetos que foram atribuídos por instâncias dessa função que eram chamadas pela função pai da árvore de chamada.  Esse número inclui as alocações que foram feitas por funções filhos.|  
|**% de Alocações Inclusivas**|A porcentagem de todos os objetos que foram criados em que foi executado analisar alocações inclusivo de instâncias de função que eram chamadas pela função pai da árvore de chamada.|  
|**Alocações Exclusivas**|O número de objetos que foram atribuídos por instâncias dessa função que eram chamadas pela função pai da árvore de chamada.  Esse número não inclui as alocações que foram feitas por funções filhos.|  
|**% de Alocações Exclusivas**|A porcentagem de todos os objetos que foram criados em que foi executado analisar alocações exclusivas de instâncias de função que eram chamadas pela função pai da árvore de chamada.|  
  
## Valores Inclusivos Decorridos  
 Os valores inclusivos decorridos indicam o tempo que uma função estava na pilha de chamada.  A hora que incluem tempo gasto esteve em funções que eram chamadas pela função e em chamadas para o sistema operacional, como alternar o contexto e as operações de entrada\/saída.  
  
|Coluna|Descrição|  
|------------|---------------|  
|**Tempo Inclusivo Decorrido**|O tempo decorrido total inclusivo de todas as chamadas a essa função quando foi chamado pela função pai da árvore de chamada.|  
|**Tempo Inclusivo Decorrido %**|A porcentagem do total decorrido vezes inclusivo de analisar executado que foi gasto no tempo decorrido total inclusivo dessa função quando foi chamado pela função pai da árvore de chamada.|  
|**Tempo Inclusivo Decorrido Médio**|A média tempo decorrido inclusivo de uma chamada à função quando foi chamado pela função pai da árvore de chamada.|  
|**Tempo Inclusivo Decorrido Máximo**|O tempo máximo decorrido inclusivo de uma chamada à função quando foi chamado pela função pai da árvore de chamada.|  
|**Tempo Inclusivo Decorrido Mínimo**|O tempo decorrido mínimo inclusivo de uma chamada à função quando foi chamado pela função pai da árvore de chamada.|  
  
## Valores Exclusivos Decorridos  
 Os valores exclusivos decorridos indicam o tempo que uma função estava executando diretamente na parte superior da pilha de chamadas.  O tempo incluem tempo em chamadas para o sistema operacional, como alternâncias de contexto e operações de entrada\/saída.  No entanto, o tempo não incluem o tempo que foram gasto em funções que eram chamadas pela função.  
  
|Coluna|Descrição|  
|------------|---------------|  
|**Tempo Exclusivo Decorrido**|O tempo decorrido total exclusivas de todas as chamadas a essa função quando foi chamado pela função pai da árvore de chamada.|  
|**Tempo Exclusivo Decorrido %**|A porcentagem do total decorrido vezes exclusivas de analisar executado que foi gasto no tempo total decorrido exclusivas dessa função quando foi chamado pela função pai da árvore de chamada.|  
|**Tempo Exclusivo Decorrido Médio**|A média tempo decorrido exclusivas de uma chamada para essa função quando foi chamado pela função pai da árvore de chamada.|  
|**Tempo Exclusivo Decorrido Máximo**|O tempo máximo decorrido exclusivas de uma chamada para essa função quando foi chamado pela função pai da árvore de chamada.|  
|**Tempo Exclusivo Decorrido Mínimo**|O tempo decorrido mínimo exclusivas de uma chamada para essa função quando foi chamado pela função pai da árvore de chamada.|  
  
## Valores Inclusivos do Aplicativo  
 Os valores inclusivos do aplicativo indicam o tempo que uma função ficou na pilha de chamadas.  A hora não incluem o tempo que foram gasto em chamadas para o sistema operacional, como alternâncias de contexto e operações de entrada\/saída.  O tempo incluem o tempo gasto em funções que foram filhos que eram chamadas pela função.  
  
|Coluna|Descrição|  
|------------|---------------|  
|**Tempo Inclusivo do Aplicativo**|As vezes inclusivo do aplicativo total de todas as chamadas a essa função quando foi chamado pela função pai da árvore de chamada.|  
|**Tempo Inclusivo do Aplicativo %**|A porcentagem do total decorrido vezes inclusivo de analisar executado que foi gasto durante inclusivo do aplicativo total dessa função quando foi chamado pela função pai da árvore de chamada.|  
|**Tempo Inclusivo Médio do Aplicativo**|As vezes inclusivo do aplicativo médio de uma chamada para essa função quando foi chamado pela função pai da árvore de chamada.|  
|**Tempo Inclusivo Máximo do Aplicativo**|A hora do aplicativo inclusivo máximo de uma chamada para essa função quando foi chamado pela função pai da árvore de chamada.|  
|**Tempo Inclusivo Mínimo do Aplicativo**|A hora do aplicativo inclusivo mínimo de uma chamada para essa função quando foi chamado pela função pai da árvore de chamada.|  
  
## Valores Exclusivos do Aplicativo  
 Os valores exclusivos de aplicativo indicam a hora que foram gasto na função, com exceção de que foram tempo gasto em funções filhos que eram chamadas pela função.  O tempo também exclui as chamadas para o sistema operacional, como alternâncias de contexto e operações de entrada\/saída.  
  
|Coluna|Descrição|  
|------------|---------------|  
|**Tempo Exclusivo do Aplicativo**|As vezes exclusivas do aplicativo total de todas as chamadas a essa função quando foi chamado pela função pai da árvore de chamada.|  
|**Tempo Exclusivo do Aplicativo %**|A porcentagem do total decorrido vezes exclusivas de analisar executado que foi gasto durante exclusivas do aplicativo total dessa função quando foi chamado pela função pai da árvore de chamada.|  
|**Tempo Exclusivo Médio do Aplicativo**|As vezes exclusivas do aplicativo médio de uma chamada para essa função quando foi chamado pela função pai da árvore de chamada.|  
|**Tempo Exclusivo Máximo do Aplicativo**|As vezes exclusivas do aplicativo máximo de uma chamada para essa função quando foi chamado pela função pai da árvore de chamada.|  
|**Tempo Exclusivo Mínimo do Aplicativo**|As vezes exclusivas do aplicativo mínimo de uma chamada para essa função quando foi chamado pela função pai da árvore de chamada.|