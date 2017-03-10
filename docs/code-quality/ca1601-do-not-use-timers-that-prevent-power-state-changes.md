---
title: "CA1601: n&#227;o usar temporizadores que impe&#231;am altera&#231;&#245;es no estado de energia | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1601"
  - "DoNotUseTimersThatPreventPowerStateChanges"
helpviewer_keywords: 
  - "CA1601"
  - "DoNotUseTimersThatPreventPowerStateChanges"
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1601: n&#227;o usar temporizadores que impe&#231;am altera&#231;&#245;es no estado de energia
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|  
|CheckId|CA1601|  
|Categoria|Microsoft.Mobility|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um timer tem um intervalo definido para ocorrer mais de um por segundo de tempo.  
  
## Descrição da Regra  
 Não sondar com mais frequência de um por segundo de tempo nem use os timers que ocorrem com mais frequência de um por segundo de tempo.  a atividade periódica de alta frequência pelo ocupação e interferirá com os timers ocioso da placa\-mãe salvando que desativa a exibição e os discos rígidos.  
  
## Como Corrigir Violações  
 Definir intervalos de timer para ocorrer pelo menos de um segundo de tempo.  
  
## Quando Suprimir Alertas  
 Esta regra deve ser suprimida apenas se acionando o timer mais de um por segundo de tempo é necessário e considerações a portabilidade pode seguramente ser ignorada.