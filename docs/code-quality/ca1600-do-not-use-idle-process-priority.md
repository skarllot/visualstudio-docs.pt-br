---
title: "CA1600: n&#227;o usar a prioridade de processo ociosa | Microsoft Docs"
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
  - "DoNotUseIdleProcessPriority"
  - "CA1600"
helpviewer_keywords: 
  - "CA1600"
  - "DoNotUseIdleProcessPriority"
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1600: n&#227;o usar a prioridade de processo ociosa
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseIdleProcessPriority|  
|CheckId|CA1600|  
|Categoria|Microsoft.Mobility|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Esta regra ocorre quando os processos são definidos como `ProcessPriorityClass.Idle`.  
  
## Descrição da Regra  
 Não defina a prioridade de processamento para executar em estado ocioso.  Os processos que têm `System.Diagnostics.ProcessPriorityClass.Idle` ocuparão a CPU quando seria de outra forma ociosa, e podem bloquear consequentemente o suporte.  
  
## Como Corrigir Violações  
 Processos de cluster a `ProcessPriorityClass.BelowNormal`.  
  
## Quando Suprimir Alertas  
 Esta regra deve ser suprimida somente quando a prioridade de ociosidade de processo é necessária e considerações a portabilidade pode ser ignorada com segurança.