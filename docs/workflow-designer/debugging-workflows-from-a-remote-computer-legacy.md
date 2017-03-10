---
title: "Debugging Workflows from a Remote Computer (Legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "workflows, debugging remotely"
  - "debugging workflows, remotely"
  - "remote debugging, workflows"
  - "debugging, remote"
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Debugging Workflows from a Remote Computer (Legacy)
Este tópico descreve como depurar aplicativos herdadas remotos de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] que são criados com [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]herdado.  Use [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado quando seu aplicativo precisa definir como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Quando você instala [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)], uma das opções componentes de instalação é instalar o depurador de [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] para [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)].  Isso instala os componentes de depuração remota.  Esses componentes de depuração remota devem ser instalados no computador que você está definido para depuração remota de fluxo de trabalho.  
  
 Além disso, o assembly que contém a definição de fluxo de trabalho de fluxo de trabalho herdado que você está depurando em um computador remoto deve ser instalado no cachê global de assemblies \(GAC\) do computador local que você está depurando de.  Por exemplo, se um fluxo de trabalho herdado está sendo executado em um computador remoto A, e você está depurada do computador local, B deve da definição de fluxo de trabalho estão presentes no GAC do computador B.  Isso permite que o designer para desserializar e exibir no computador B a marcação de fluxo de trabalho de fluxo de trabalho que está executando remotamente no computador A.  Para obter mais informações sobre o cachê global de assemblies, consulte Biblioteca MSDN.  
  
 depuração remota de[!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] funciona da mesma que a depuração remota para outros componentes de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  Depuração remota de Para obter mais informações, consulte [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] na Biblioteca MSDN.  
  
## Consulte também  
 [Debugging Legacy Workflows](../workflow-designer/debugging-legacy-workflows.md)