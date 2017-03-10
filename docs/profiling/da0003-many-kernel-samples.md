---
title: "DA0003: muitas amostras de kernel | Microsoft Docs"
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
  - "vs.performance.rules.DA0003"
  - "vs.performance.DA0003"
  - "vs.performance.3"
  - "vs.performance.rules.DAManyKernelSamples"
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0003: muitas amostras de kernel
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificação da Regra|DA0003|  
|Categoria|Uso de Ferramentas de Criação de Perfil|  
|Analisando métodos|Preparação de exemplos|  
|Message \(Mensagem\)|Você tem uma porcentagem alta dos exemplos no modo kernel.  Isso pode indicar um alto volume de atividade de E\/S ou uma taxa alta de troca de contexto.  Considere analisar seu aplicativo que usa novamente o modo de instrumentação.|  
|Tipo de regra|Informações|  
  
## Causa  
 Uma proporção significativa dos exemplos de pilha de chamadas que foram coletados para o aplicativo estava sendo executada no modo kernel.  Considere analisar seu aplicativo usando um método analisando diferente.  
  
## Descrição da Regra  
 No windows, o código pode ser executado no modo ou no modo de usuário do kernel. \(Modo de kernel também é chamado para o privilégio.\) Somente código do sistema de baixo nível, como drivers de dispositivo, o é executado no modo kernel.  Um aplicativo de modo de usuário poderá fazer a transição para o modo de kernel para executar operações de E\/S, espere primitivos de sincronização de thread de processamento ou, ou fazer chamadas do sistema.  
  
 A amostragem é mais eficiente quando você estiver analisando os aplicativos que passam a maioria de seus tempo que fazem o trabalho no modo de usuário.  O número de casos que foram coletados enquanto o aplicativo estava sendo executada no modo kernel pode indicar frequentes operações de E\/S ou pode indicar que as alternâncias de contexto estão ocorrendo.  Nenhuma dessas operações podem ser investigadas usando o método de amostragem.  Se muitos exemplos do modo kernel são obtidos, os dados de maneira não podem conter suficiente exemplos do modo de usuário para ser estatisticamente significativos.  
  
## Como Corrigir Violações  
 Considere analisar seu aplicativo que usa novamente uma das seguintes opções:  
  
-   Perfil usando o método de gerenciamento.  
  
-   Aumente a taxa de amostragem para tentar coletar mais exemplos em modo de usuário.