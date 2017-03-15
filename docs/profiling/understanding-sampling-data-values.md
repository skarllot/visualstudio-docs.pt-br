---
title: "Noções básicas sobre valores de dados de amostragem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sampling profiling method
- Profiling Tools, sampling
ms.assetid: fad540a8-24b6-4ff9-91ce-e67e9a58399d
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
ms.openlocfilehash: e5da15afad275b789af821ac528062556acdd69d

---
# <a name="understanding-sampling-data-values"></a>Noções básicas sobre valores de dados de amostragem
O método de criação de perfil de *amostragem* das [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ferramentas de criação de perfil interrompe o processador do computador em intervalos definidos e coleta a pilha de chamadas de função. Uma *pilha de chamadas* é uma estrutura dinâmica que armazena informações sobre as funções que estão em execução no processador.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 A análise do criador de perfil determina se o processador está executando código no processo de destino. Se o processador não está executando código no processo de destino, o exemplo é descartado.  
  
 Se o processador está executando o código de destino, o criador de perfil incrementa as contagens de amostragem para cada função na pilha de chamadas. No momento em que a amostra é coletada, apenas uma função na pilha de chamadas está executando código. As outras funções na pilha são pais na hierarquia de chamadas de função que estão aguardando para seus filhos retornarem.  
  
 Para o evento de exemplo, o criador de perfil incrementa a contagem de exemplo *exclusiva* da função que está executando as instruções de exemplo. Como um exemplo exclusivo também é parte do total de exemplos (*inclusivo*) da função, a contagem inclusiva de amostras da função atualmente ativa também será incrementada.  
  
 O criador de perfil incrementa a contagem inclusiva de exemplo de todas as outras funções na pilha de chamadas.  
  
## <a name="inclusive-samples"></a>Amostras inclusivas  
 O número total de amostras que são coletadas durante a execução da função de destino.  
  
 Isso inclui exemplos que são coletados durante a execução direta de código da função e exemplos que são coletados durante a execução de funções filho que são chamadas pela função de destino.  
  
## <a name="exclusive-samples"></a>Amostras exclusivas  
 O número de amostras que são coletadas durante a execução direta de instruções da função de destino.  
  
 Amostras exclusivas não incluem exemplos que são coletados durante a execução de funções que são chamadas pela função de destino.  
  
## <a name="inclusive-percent"></a>Porcentagem Inclusiva  
 O percentual do número total de amostras inclusivas na criação de perfil que são amostras inclusivas do intervalo de dados ou função.  
  
## <a name="exclusive-percent"></a>Porcentagem Exclusiva  
 O percentual do número total de amostras exclusivas na criação de perfil que são amostras exclusivas do intervalo de dados ou função.  
  
## <a name="see-also"></a>Consulte também  
 [Como escolher métodos de coleta](../profiling/how-to-choose-collection-methods.md)   
 [Analisando dados de ferramentas de desempenho](../profiling/analyzing-performance-tools-data.md)


<!--HONumber=Feb17_HO4-->


