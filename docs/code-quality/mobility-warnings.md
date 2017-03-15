---
title: "Avisos de mobilidade | Microsoft Docs"
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
  - "vs.codeanalysis.MobilityRules"
helpviewer_keywords: 
  - "avisos da análise de código gerenciado, avisos de mobilidade"
  - "avisos de mobilidade"
  - "avisos de mobilidade"
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Avisos de mobilidade
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Os avisos da portabilidade dão suporte ao consumo de energia eficiente.  
  
## Nesta seção  
  
|Regra|Descrição|  
|-----------|---------------|  
|[CA1600: não usar a prioridade de processo ociosa](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Não defina a prioridade de processamento para executar em estado ocioso.  Os processos que têm System.Diagnostics.ProcessPriorityClass.Idle ocuparão a CPU quando seria de outra forma ociosa, e podem bloquear consequentemente o suporte.|  
|[CA1601: não usar temporizadores que impeçam alterações no estado de energia](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|a atividade periódica de alta frequência pelo ocupação e interferirá com os timers ocioso da placa\-mãe salvando que desativa a exibição e os discos rígidos.|