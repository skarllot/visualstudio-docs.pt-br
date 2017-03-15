---
title: "Regras de desempenho de memória e paginação | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
caps.latest.revision: 8
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
ms.openlocfilehash: dc6d03b40331d1160e41570984d51ceb04bd0f18
ms.lasthandoff: 02/22/2017

---
# <a name="memory-and-paging-performance-rules"></a>Regras de desempenho de memória e paginação
As regras de desempenho na memória e categoria de paginação identificam a atividade de paginação em uma execução de criação de perfil que pode afetar a capacidade de resposta e o desempenho do aplicativo.  
  
|||  
|-|-|  
|[DA0014: taxas extremamente elevadas de paginação de memória ativa para o disco](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Uma taxa extremamente alta de paginação de memória ativa de e para o disco ocorreu durante toda a execução de criação de perfil. Geralmente, taxas de paginação nesse nível afetam a capacidade de resposta e o desempenho do aplicativo. Considere a redução das alocações de memória revisando os algoritmos. Talvez você também precise considerar os requisitos de memória do aplicativo. Tente executar a criação de perfil novamente em um computador com mais memória. Essa regra é acionada quando a quantidade de atividade de paginação excede o limite superior de regra D0017.|  
|[DA0017: taxas elevadas de paginação de memória ativa para o disco](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Uma taxa relativamente alta de paginação de memória ativa de e para o disco ocorreu durante toda a execução de criação de perfil. Geralmente, taxas de paginação nesse nível afetam a capacidade de resposta e o desempenho do aplicativo. Considere a redução das alocações de memória revisando os algoritmos. Talvez você também precise considerar os requisitos de memória do aplicativo. Tente executar a criação de perfil novamente em um computador com mais memória.|
