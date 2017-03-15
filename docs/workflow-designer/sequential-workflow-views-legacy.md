---
title: "Sequential Workflow Views (Legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "09/02/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "sequential workflow views"
  - "sequential workflows, views"
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
caps.latest.revision: 7
caps.handback.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Sequential Workflow Views (Legacy)
[!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] fornece [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] herdado que pode ser usado para direcionar [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] fornece uma maneira de criar aplicativos graficamente de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] usando a interface do usuário e de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  aplicativos de[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] são compostos das etapas do processo de fluxo de trabalho chamadas atividades.  Para criar um fluxo de trabalho, compor atividades na superfície de design arrastando seus respectivos designer de atividade de **Caixa de Ferramentas** na superfície de design.  
  
 Quando você cria um fluxo de trabalho sequencial, que é uma [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040), existem três modos de exibição do fluxo de trabalho.  Esses modos de exibição são acessíveis a partir do menu **Fluxo de Trabalho** e do menu de contexto na superfície de design.  
  
 A tabela a seguir lista o nome e a descrição de cada uma.  
  
|Opção de menu\/guia|Descrição|  
|-------------------------|---------------|  
|**Exibição SequentialWorkflow**|Clique com o botão direito do mouse na superfície de design e selecione a opção de **Exibição SequentialWorkflow** do menu de contexto exibir o modo de **Fluxo de Trabalho Sequencial** , que mostra a representação gráfica atividades base de fluxo de trabalho sequencial.  Ou **Exibir SequentialWorkflow** partir do menu de **Fluxo de Trabalho** .|  
|**Exibir Manipulador de Cancelamento**|Clique a superfície de design e selecione o **exibir manipulador de cancelamento** opção no menu de contexto para exibir o **fluxo de trabalho seqüencial** exibir, que mostra o [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) atividade associada com o fluxo de trabalho.  Ou **Exibir Manipulador de Cancelamento** partir do menu de **Fluxo de Trabalho** .|  
|**Manipulador de falha de exibição**|Clique a superfície de design e selecione o **exibir manipulador de falha** opção no menu de contexto para exibir o **falhas** exibir, que mostra o [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) atividade associada com o fluxo de trabalho.  Ou **Exibir o manipulador de falha** partir do menu de **Fluxo de Trabalho** .|  
  
 Para obter mais informações sobre modos semelhantes, consulte [Activity Views \(Legacy\)](../workflow-designer/activity-views-legacy.md).  
  
## Consulte também  
 [Activity Views \(Legacy\)](../workflow-designer/activity-views-legacy.md)   
 [Creating Legacy Workflow Projects](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Modos de criação de fluxo de trabalho](http://go.microsoft.com/fwlink?LinkID=65014)