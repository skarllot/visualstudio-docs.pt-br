---
title: "Regras de desempenho de mem&#243;ria e pagina&#231;&#227;o | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Regras de desempenho de mem&#243;ria e pagina&#231;&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

As regras de desempenho na memória e na categoria de paginação identificam a atividade de paginação na execução do que pode afetar o desempenho do aplicativo e a resposta.  
  
|||  
|-|-|  
|[DA0014: taxas extremamente elevadas de paginação de memória ativa em disco](../Topic/DA0014:%20Extremely%20high%20rates%20of%20paging%20active%20memory%20to%20disk.md)|Uma taxa alta extremamente de paginação de memória ativa a e de disco durante todo analisar executado.  As taxas de paginação nesse nível geralmente afetam o desempenho do aplicativo e a resposta.  Considere revisar algoritmos para reduzir alocações de memória.  Você pode também ter que considerar os requisitos de memória do seu aplicativo.  Tente executar que analisa novamente em um computador que tenha mais memória.  Esta regra é disparada quando a quantidade de atividades de paginação exceder o limite superior da regra D0017.|  
|[DA0017: taxas elevadas de paginação de memória ativa em disco](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Uma taxa relativamente alta de paginação de memória ativa a e de disco durante todo analisar executado.  As taxas de paginação nesse nível geralmente afetam o desempenho do aplicativo e a resposta.  Considere revisar algoritmos para reduzir alocações de memória.  Você pode também ter que considerar os requisitos de memória do seu aplicativo.  Tente executar que analisa novamente em um computador que tenha mais memória.|