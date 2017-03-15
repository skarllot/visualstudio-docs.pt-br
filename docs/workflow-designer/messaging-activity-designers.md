---
title: "Messaging Activity Designers | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 897e63cf-a42f-4edd-876f-c4ccfffaf6d6
caps.latest.revision: 7
caps.handback.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Messaging Activity Designers
Os designers de atividade de mensagem são usados para criar e configurar as atividades de mensagem que enviam e recebem mensagens de [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] de dentro de um aplicativo de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] .  [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] apresenta cinco atividades de mensagem e [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] fornece dois novos designer do modelo que permitem a você gerenciar a mensagem em um fluxo de trabalho.  Os tópicos contidos nesta seção e listados na tabela a seguir fornecem orientação sobre como usar o designer de atividade e modelo de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] .  
  
## Nesta seção  
  
|Atividade de mensagem|Descrição|  
|---------------------------|---------------|  
|[CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)|Cria e configura uma atividade de <xref:System.ServiceModel.Activities.CorrelationScope> que fornece gerenciamento implícito de atividades filhos de mensagem com um objeto de <xref:System.ServiceModel.Activities.CorrelationHandle> .|  
|[InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)|Cria e configura uma atividade de <xref:System.ServiceModel.Activities.InitializeCorrelation> que é usada para inicializar correlação sem enviar e receber uma mensagem.|  
|[Receive](../workflow-designer/receive-activity-designer.md)|Cria e configura uma atividade de <xref:System.ServiceModel.Activities.Receive> que receberá uma mensagem de um serviço.|  
|[ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)|Cria um par de pré\-compilação configurado <xref:System.ServiceModel.Activities.Send> e atividades de <xref:System.ServiceModel.Activities.ReceiveReply> dentro de uma atividade de <xref:System.Activities.Statements.Sequence> .|  
|[Send](../workflow-designer/send-activity-designer.md)|Cria e configura uma atividade de <xref:System.ServiceModel.Activities.Send> que enviar uma mensagem a um serviço.|  
|[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)|Cria um par de pré\-compilação configurado <xref:System.ServiceModel.Activities.Receive> e atividades de <xref:System.ServiceModel.Activities.SendReply> dentro de uma atividade de <xref:System.Activities.Statements.Sequence> .|  
|[TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)|Cria e configura uma atividade de <xref:System.ServiceModel.Activities.TransactedReceiveScope> que permite ao fluxo de transações em um fluxo de trabalho.|  
  
## Referência  
 <xref:System.Activities.Activity>  
  
 <xref:System.ServiceModel.Activities.CorrelationScope>  
  
 <xref:System.ServiceModel.Activities.Receive>  
  
 <xref:System.ServiceModel.Activities.Send>  
  
 <xref:System.ServiceModel.Activities.ReceiveReply>  
  
 <xref:System.ServiceModel.Activities.SendReply>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope>  
  
## Seções relacionadas  
 Para outros tipos de designer de atividade, consulte os seguintes tópicos.  
  
 [Control Flow](../workflow-designer/control-flow-activity-designers.md)  
  
 [Using the Activity Designers](../workflow-designer/using-the-activity-designers.md)  
  
 [Flowchart](../workflow-designer/flowchart-activity-designers.md)  
  
 [Runtime](../workflow-designer/runtime-activity-designers.md)  
  
 [Primitives](../workflow-designer/primitives-activity-designers.md)  
  
 [Transaction](../workflow-designer/transaction-activity-designers.md)  
  
 [Collection](../workflow-designer/collection-activity-designers.md)  
  
 [Error Handling](../workflow-designer/error-handling-activity-designers.md)  
  
## Recursos externos  
 [Using the Activity Designers](../workflow-designer/using-the-activity-designers.md)