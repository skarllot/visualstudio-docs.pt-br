---
title: "CorrelationScope Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.CorrelationScope.UI"
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# CorrelationScope Activity Designer
O designer de atividade de **CorrelationScope** é usado para criar e configurar uma atividade de <xref:System.ServiceModel.Activities.CorrelationScope> que fornece gerenciamento implícito de atividades filhos de mensagem usando um objeto de <xref:System.ServiceModel.Activities.CorrelationHandle> .  
  
## A atividade de CorrelationScope  
 A propriedade de <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> especifica <xref:System.ServiceModel.Activities.CorrelationHandle> usado para gerenciar atividades filhos de mensagem.  As atividades de <xref:System.ServiceModel.Activities.Send> e de <xref:System.ServiceModel.Activities.Receive> contidas em <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> são configurados para usar a propriedade de <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> de atividade de conteúdo da <xref:System.ServiceModel.Activities.CorrelationScope> para executar correlação.  
  
### Usando o designer de atividade de CorrelationScope  
 O designer de atividade de **CorrelationScope** pode ser encontrado na categoria de **Sistema de Mensagens** de **Caixa de Ferramentas**, que é acessada clicando na guia **Caixa de Ferramentas** no lado esquerdo de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(como alternativa, **Barra de Ferramentas** partir do menu de **Modo de Visualização** , ou CTRL\+ALT\+X.\)  
  
 O designer de atividade de **CorrelationScope** pode ser arrastado de **Caixa de Ferramentas** e ser solto sobre a superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] .  Isso cria uma atividade de <xref:System.ServiceModel.Activities.CorrelationScope> com **DisplayName** padrão de CorrelationScope.  <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade de **CorrelationScope** ou na caixa de **DisplayName** da janela de **Propriedades** .  
  
 Para especificar <xref:System.ServiceModel.Activities.CorrelationHandle> usado por atividades filhos de mensagem, clique no botão da elipse ao lado do campo de **CorrelatesWith** na janela de **Propriedades** para exibir a caixa de diálogo **Editor de Expressão** .  Esta propriedade pode também ser definida na superfície do designer de atividade.  
  
 As atividades o escopo dentro de correlação são especificadas soltando seus designers dentro da caixa de **Corpo** dentro do designer de **CorrelationScope** .  
  
### As propriedades de CorrelationScope  
 A tabela a seguir mostra as propriedades de <xref:System.ServiceModel.Activities.CorrelationScope> e descreve como elas são usadas no designer.  Essas propriedades podem ser editadas na janela de **Propriedades** ou na superfície do designer de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] , e frequentemente em ambos.  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável opcional de atividade de <xref:System.ServiceModel.Activities.InitializeCorrelation> .|  
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Especifica <xref:System.ServiceModel.Activities.CorrelationHandle> usado para gerenciar atividades filhos de mensagem.  Se você não definir essa propriedade, <xref:System.ServiceModel.Activities.CorrelationScope> <xref:System.ServiceModel.Activities.CorrelationHandle> implícito cria automaticamente.|  
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Especifica as atividades no escopo de correlação.|  
  
## Consulte também  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)