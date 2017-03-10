---
title: "How to: Change the Debug Stepping Option (Legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "branch stepping"
  - "debugging, stepping options"
  - "debugging workflows, stepping options"
  - "stepping, changing options"
  - "instance stepping"
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# How to: Change the Debug Stepping Option (Legacy)
Este tópico descreve como modificar a opção de avançar de depuração para aplicativos de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] em novas [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] que têm ações simultâneas.  Use [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Quando você está depurando as atividades herdados que possuem a execução simultânea, como **ParallelActivity** ou **ConditionedActivityGroup**, você pode usar uma das duas opções depurar seu código.  
  
 Siga estas etapas para alterar a opção de avançar de depuração no seu projeto herdado de fluxo de trabalho.  
  
## Procedimentos  
  
#### Para alterar a opção de avançar de depuração  
  
1.  Inicie o Visual Studio.  
  
2.  Abrir um projeto existente herdado de fluxo de trabalho ou criar um novo projeto que empreguem atividades simultâneas e que tem como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
3.  No menu de **Fluxo de Trabalho** em novas [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], aponte para **Depurar**, e ele na **Opções de avançar**.  
  
4.  Selecione **Instância** ou **Ramificação**.  
  
## Consulte também  
 [Debugging Legacy Workflows](../workflow-designer/debugging-legacy-workflows.md)   
 [Debug Stepping Options \(Legacy\)](../workflow-designer/debug-stepping-options-legacy.md)