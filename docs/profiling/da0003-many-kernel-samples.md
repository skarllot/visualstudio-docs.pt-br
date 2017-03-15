---
title: 'DA0003: muitas amostras de kernel | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.rules.DA0003
- vs.performance.DA0003
- vs.performance.3
- vs.performance.rules.DAManyKernelSamples
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
caps.latest.revision: 11
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
ms.openlocfilehash: 5de841783139d5a8cf23c18e3b52f6d107cf2ab2
ms.lasthandoff: 02/22/2017

---
# <a name="da0003-many-kernel-samples"></a>DA0003: muitas amostras de kernel
|||  
|-|-|  
|ID de regra|DA0003|  
|Categoria|Uso das ferramentas de criação de perfil|  
|Métodos de criação de perfil|Amostragem|  
|Mensagem|Há uma grande proporção de exemplos no Modo Kernel. Isso pode indicar um alto volume de atividade de E/S ou uma taxa alta de alternância de contexto. Considere criar um novo perfil para o aplicativo usando o Modo de Instrumentação.|  
|Tipo de regra|Informações|  
  
## <a name="cause"></a>Causa  
 Uma parte significativa dos exemplos de pilha de chamadas coletados para o aplicativo estavam sendo executados em modo kernel. Considere a criação de perfil para o aplicativo usando um método de criação de perfil diferente.  
  
## <a name="rule-description"></a>Descrição da Regra  
 No Windows, o código pode ser executado no modo kernel ou no modo de usuário. (o modo kernel também é conhecido como modo privilegiado.) Somente o código de sistema de baixo nível, como drivers de dispositivo, executa no modo kernel. Um aplicativo de modo de usuário pode fazer a transição para o modo kernel para executar operações de E/S, aguardar os primitivos de sincronização de thread ou de processo ou fazer chamadas do sistema.  
  
 A amostragem é a maneira mais eficaz ao criar perfis para aplicativos que passam a maior parte do tempo em modo de usuário. O número de amostras coletadas quando o aplicativo estava sendo executado no modo kernel pode indicar operações de E/S frequentes ou que esse alternâncias de contexto estão ocorrendo. Nenhuma dessas operações podem ser investigadas usando o método de amostragem. Caso muitas amostras do modo kernel forem usadas, os dados de amostragem podem não conter amostras suficientes de modo de usuário para serem estatisticamente significativos.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Considere criar um novo perfil para o aplicativo usando uma das opções a seguir:  
  
-   Crie perfis usando o método de instrumentação.  
  
-   Aumente a taxa de amostragem para coletar mais amostras no modo de usuário.
