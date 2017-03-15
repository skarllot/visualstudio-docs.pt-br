---
title: "Activity Views (Legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "09/02/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "activities, activity views"
  - "views, activity"
  - "activity views"
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Activity Views (Legacy)
Muitas das atividades fornecidas por [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)], que fluxos de trabalho são compostos, têm várias exibições de design disponíveis em [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]herdado.  Quando você arrasta um designer de atividade de **Caixa de Ferramentas** na superfície de design e depois disso, sempre que você seleciona a atividade, você pode alternar entre os modos diferentes de design usando o menu de **Fluxo de Trabalho** ou clique com o botão direito do mouse na atividade selecionada.  Além disso, quando você move o ponteiro sobre o nome de uma atividade selecionada, um conjunto lista suspensa de guias que aparece você pode usar para alternar entre modos de exibição diferentes.  
  
 Cada atividade tem pelo menos uma exibição; esta é a exibição padrão exibida quando você arrasta um designer de atividade de **Caixa de Ferramentas** na superfície de design.  Esta exibição de atividade de opção está disponível como a opção de **Exibição \[tipo de atividade\]** menus e na guia, por exemplo, **Exibição paralela**.  A maioria das atividades têm modos de exibição adicionais e as atividades diferentes podem ter diferentes modos de exibição.  Por exemplo, o [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) atividade tem o modo de exibição e o [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) atividade tem eventos de um modo de exibição.  Muitas das atividades que vêm com o Windows Workflow Foundation têm **exibir manipulador de cancelamento** e **View Faults** criar modos de exibição para exibir o [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) e um [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) associados a eles.  
  
 A tabela a seguir lista o nome e a descrição de cada uma.  
  
|Opção de menu\/guia|Descrição|  
|-------------------------|---------------|  
|**Exibição \[tipo de atividade\]**|Selecione este menu catalogue ou a opção para exibir a representação gráfica padrão de atividade selecionada.|  
|**Exibir Manipulador de Cancelamento**|Selecione esta opção de menu ou na guia exibição o [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) associado à atividade selecionada.|  
|**Manipulador de falha de exibição**|Selecione esta opção de menu ou na guia exibição o [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) associado à atividade selecionada.|  
|**Exibir Manipulador de Compensação**|Selecione esta opção de menu ou na guia exibição o [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) associado com selecionado [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093).|  
|**Exibir o manipulador de eventos**|Selecione esta opção de menu ou na guia exibição o [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) associado com selecionado o [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030).|  
  
 Para obter informações sobre modos semelhantes, consulte [Sequential Workflow Views \(Legacy\)](../workflow-designer/sequential-workflow-views-legacy.md).  
  
## Consulte também  
 [Legacy Workflow Activities](../workflow-designer/legacy-workflow-activities.md)   
 [Sequential Workflow Views \(Legacy\)](../workflow-designer/sequential-workflow-views-legacy.md)