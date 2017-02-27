---
title: "Como coletar dados de amostragem no nível de linha | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance tools, line-level sampling
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 5a53b8d381821f6bb85e4ad1730c43d80e4d75ba

---
# <a name="how-to-collect-line-level-sampling-data"></a>Como coletar dados de amostragem no nível da linha
A amostragem de nível de linha é a capacidade do criador de perfil para determinar o local no código de uma função de processamento intensivo em que o processador tem que gastar a maior parte de seu tempo, como uma função que tem amostras altamente exclusivas.  
  
## <a name="overview"></a>Visão Geral  
 Para amostragem de nível de linha, o criador de perfil percorre a pilha de chamadas do programa em intervalos definidos e agrega os resultados. Esses resultados mostram quais instruções o processador estava executando quando as amostras foram obtidas. Em seguida, os dados coletados sobre amostras exclusivas são analisados para identificar as linhas de código e o IP (ponteiro de instrução).  
  
 A amostragem de nível de linha funciona para código gerenciado e nativo. Os relatórios de desempenho que exibem esses dados incluem a exibição de Linhas e a exibição de Módulos.  
  
 Informações de início/término de caractere não estão disponíveis para código nativo. Para instruções de várias linhas, as informações de início da linha não estão disponível para código nativo. Somente informações de final da linha estão disponíveis.  
  
### <a name="available-data"></a>Dados disponíveis  
 Os dados de amostragem de nível de linha disponíveis incluem as seguintes informações:  
  
-   Nome da função.  
  
-   Endereço da função.  
  
-   Início da linha – número de linha do código do qual foi obtida a amostra.  
  
-   Fim da linha – número de linha de término do código-fonte. Esse geralmente é o mesmo que os dados do "Início da linha", exceto quando uma única instrução do programa abrange várias linhas do código-fonte.  
  
-   Início do caractere – coluna de início da amostra de agregação. É geralmente 0, exceto quando uma única linha contém várias instruções de programa.  
  
-   Final do caractere – coluna de término da amostra de agregação.  
  
-   IP – endereço em que a amostra de agregação foi obtida (somente em modo de exibição de IP).  
  
 Na exibição de **Módulos**, se uma função tiver estatísticas em nível de linha, as estatísticas estarão aninhadas em cada função. Além disso, são apresentadas as estatísticas no nível de IP que estão aninhadas em cada linha.  
  
### <a name="turn-off-line-level-sampling-for-managed-code"></a>Desligar a amostragem de nível de linha para código gerenciado  
 Por padrão, a amostragem de nível de linha está ativada. Você pode desligar a coleta de dados de nível de linha de código gerenciado, seguindo um destes procedimentos:  
  
-   Antes da criação de perfil, digite **VSPerfCLREnv /samplelineoff**. Isso afeta os aplicativos e os serviços.  
  
     – ou —  
  
-   Ao iniciar um aplicativo, digite **VSPerfCmd /lineoff \<outros argumentos>**.  
  
## <a name="see-also"></a>Consulte também  
 [Configurando sessões de desempenho](../profiling/configuring-performance-sessions.md)   
 [Analisando dados de ferramentas de desempenho](../profiling/analyzing-performance-tools-data.md)


<!--HONumber=Feb17_HO4-->


