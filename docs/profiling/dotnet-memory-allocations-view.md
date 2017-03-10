---
title: "Exibi&#231;&#227;o de aloca&#231;&#245;es da mem&#243;ria do .NET | Microsoft Docs"
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
  - "vs.performance.view.allocation"
helpviewer_keywords: 
  - "exibição Alocações"
  - "relatório de desempenho, exibição Alocação"
  - "relatórios de ferramentas de criação de perfil, exibição Alocação"
  - "ferramentas de criação de perfil, exibição Alocação"
ms.assetid: 01eb876e-c413-4516-977b-4f896929e8a6
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Exibi&#231;&#227;o de aloca&#231;&#245;es da mem&#243;ria do .NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A exibição de Alocações lista os tipos que foram criados durante sessão de análise.  Cada tipo é o nó raiz de uma árvore de chamada que exibe os caminhos de execução da função que resultaram nas alocações do tipo.  
  
 Os dados em uma linha de tipo mostram o número total de objetos do tipo que foram criados na análise e o número total de bytes atribuído para os objetos daquele tipo.  Os valores inclusivos e exclusivos para um tipo são sempre os mesmo.  
  
-   Valores inclusivos são para objetos criados nas instâncias da função e para suas funções filho que foram chamados pela função pai na árvore de chamada.  
  
-   Valores exclusivos são para objetos que foram criados diretamente pela função quando foram chamados pela função pai.  Os objetos criados em funções filho não são incluídos.  
  
 Os dados para uma função exibem o número de objetos criados e o número de bytes atribuídos para objetos do tipo pai.  
  
## Destacando o Caminho Mais Ativo de Execução  
 Você pode localizar o caminho de execução da árvore de chamada que criou a maioria dos objetos do tipo pai.  
  
-   Para exibir o caminho mais ativo, clique com o botão direito do mouse no tipo ou função, e depois clique em **Expandir o Caminho Mais Ativo**.  
  
|Coluna|Descrição|  
|------------|---------------|  
|**Nome**|O nome do tipo alocado ou função.|  
|**Identificação do Processo**|A identificação do processo \(PID\) da execução de criação de perfil.|  
|**Nome do Processo**|O nome do processo.|  
|**Nome do Módulo**|O nome do módulo que contém o tipo ou função.|  
|**Caminho do Módulo**|O caminho do módulo que contém o tipo ou função.|  
|**Source File**|O arquivo\-fonte que contém a definição para o tipo ou função.|  
|**Número de Linha da Função**|O número da linha inicial da definição deste tipo ou função no arquivo de origem.|  
|**Nível**|Indica se os dados são para um tipo ou função.|  
|**Alocações Inclusivas**|-   Para uma função, o número total de objetos do tipo pai que foram criados pela função.  Esse número inclui os objetos criados em funções filhas.<br />-   Para um tipo, o número total de instâncias deste tipo que foram criadas.|  
|**% de Alocações Inclusivas**|-   Para uma função, a porcentagem de todos os objetos criados na análise que eram alocações inclusivas do tipo pai pela função.<br />-   Para um tipo, a porcentagem do número total de objetos que foram criados na análise que eram instâncias do tipo.|  
|**Alocações Exclusivas**|-   Para uma função, o número de objetos que foram criados quando a função estava executando diretamente no topo da pilha de chamadas.  Esse número não inclui os objetos criados em funções filhas.<br />-   Para um tipo, o número total de instâncias deste tipo que foram criadas.|  
|**% de Alocações Exclusivas**|-   Para uma função, a porcentagem de todos os objetos criados na análise que eram alocações inclusivas do tipo pai pela função.<br />-   Para um tipo, a porcentagem do número total de objetos que foram criados na análise que eram instâncias do tipo.|  
|**Bytes Inclusivos**|-   Para uma função, o número de bytes de memória que foram alocados pela função para objetos do tipo pai.  Este número inclui a memória que foi atribuída por suas funções filhas.<br />-   Para um tipo, o número total de bytes que foi atribuído na análise para as instâncias do tipo.|  
|**% de Bytes Inclusivos**|-   Para uma função, a porcentagem da memória alocada na análise que representava alocações inclusivas do tipo pai pela função.<br />-   Para um tipo, a porcentagem da memória alocada na análise que foi alocada para instâncias do tipo.|  
|**Bytes Exclusivos**|-   Para uma função, o número de bytes de memória que foram alocados pela função para objetos do tipo pai.  Esse número não inclui a memória que foi atribuída por suas funções filhas.<br />-   Para um tipo, o número total de bytes que foi atribuído na análise para as instâncias do tipo.|  
|**% de Bytes Exclusivos**|-   Para uma função, a porcentagem de toda a memória alocada na análise que representava alocações exclusivas do tipo pai pela função.<br />-   Para um tipo, a porcentagem da memória alocada na análise que foi alocada para instâncias do tipo.|