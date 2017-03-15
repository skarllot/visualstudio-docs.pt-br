---
title: "SendAndReceiveReply Template Designer | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.SendAndReceiveReply.UI"
  - "System.ServiceModel.Activities.ReceiveReply.UI"
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# SendAndReceiveReply Template Designer
O modelo de **SendAndReceiveReply** é usado para criar um par de <xref:System.ServiceModel.Activities.Send> pré\-compilação configurado e as atividades de <xref:System.ServiceModel.Activities.ReceiveReply> dentro de uma atividade de <xref:System.Activities.Statements.Sequence> que são correlacionadas como parte de um padrão de troca de solicitação\/resposta de mensagem no cliente.  
  
## O modelo de SendAndReceiveReply  
 Adicione o modelo de **SendAndReceiveReply** faz três coisas além de criar as atividades de <xref:System.ServiceModel.Activities.Send> e de <xref:System.ServiceModel.Activities.ReceiveReply> dentro de uma atividade de <xref:System.Activities.Statements.Sequence> :  
  
1.  Configurar <xref:System.ServiceModel.Activities.Send.OperationName%2A>, propriedades de <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> de atividade de <xref:System.ServiceModel.Activities.Send> .  
  
2.  Associa a propriedade de <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> de atividade de <xref:System.ServiceModel.Activities.ReceiveReply> a atividade de <xref:System.ServiceModel.Activities.Send> .  
  
3.  Cria <xref:System.ServiceModel.Activities.CorrelationHandle> como um variável na atividade pai.  
  
### Usando o designer do modelo de SendAndReceiveReply  
 O designer de atividade de **SendAndReceiveReply** pode ser encontrado na categoria de **Sistema de Mensagens** de **Caixa de Ferramentas**, que é acessada clicando na guia **Caixa de Ferramentas** em [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(como alternativa, **Barra de Ferramentas** partir do menu de **Modo de Visualização** , ou CTRL\+ALT\+X.\)  
  
 O designer de atividade de **SendAndReceiveReply** pode ser arrastado de **Caixa de Ferramentas** e ser solto sobre a superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] onde quer que as atividades são colocadas em geral.  Isso cria uma atividade de <xref:System.ServiceModel.Activities.Send> que pode ser configurada com o designer de atividade de **Enviar** e <xref:System.ServiceModel.Activities.ReceiveReply> correlacionado que podem ser configurados com o designer de **ReceiveReplyForSend** .  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)] utilizando o designer de **Enviar** para configurar a atividade de <xref:System.ServiceModel.Activities.Send> , consulte o tópico de [Send](../workflow-designer/send-activity-designer.md) .  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)] utilizando o designer de **ReceiveReplyForSend** para configurar a atividade de <xref:System.ServiceModel.Activities.ReceiveReply> , consulte a seção a seguir.  
  
### Propriedades de ReceiveReply  
 A tabela a seguir mostra as propriedades de <xref:System.ServiceModel.Activities.ReceiveReply> e descreve como elas são usadas no designer.  Essas propriedades podem ser editadas na grade de propriedades e alguns podem ser editados na superfície do designer de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] .  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável opcional de atividade de <xref:System.ServiceModel.Activities.ReceiveReply> .  O padrão é ReceiveReplyForSend.<br /><br /> Embora o uso de um valor não padrão para <xref:System.Activities.Activity.DisplayName%2A> amigável não é necessário restrita, é uma prática recomendada usar um valor.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>|True|Fazer referência a <xref:System.ServiceModel.Activities.Send> a atividade emparelhada com esta atividade de <xref:System.ServiceModel.Activities.ReceiveReply> .  Esta propriedade não deve ser **null**.  <xref:System.ServiceModel.Activities.Send> e as atividades de <xref:System.ServiceModel.Activities.ReceiveReply> são usados juntos no cliente para modelar um padrão de mensagem de solicitação\/resposta.  Esta propriedade especifica que a atividade de <xref:System.ServiceModel.Activities.Send> é emparelhada.  No designer, você não pode editar esta propriedade como é associada automaticamente a atividade de <xref:System.ServiceModel.Activities.Send> de que você criou a atividade de <xref:System.ServiceModel.Activities.ReceiveReply> .|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>|False|Especifica o conteúdo de mensagem ou de parâmetro para receber.  Pode ser uma atividade de <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou uma atividade de <xref:System.ServiceModel.Activities.ReceiveParametersContent> .  Editar esta propriedade clicando no botão da elipse ao lado do campo de **Conteúdo** na grade de propriedade ou clicando no botão de **Defina…** ao lado do rótulo de **Conteúdo** na superfície do designer de atividade de **Receber** .  Ambos exibe a caixa de diálogo **Conteúdo a definição** .  [!INCLUDE[crabout](../test/includes/crabout_md.md)] como usar essa caixa, consulte o tópico de [Content Definition Dialog Box](../workflow-designer/content-definition-dialog-box.md) .|  
|<xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A>|False|Especifica a coleção de objetos de <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializam vários objetos de <xref:System.ServiceModel.Activities.CorrelationHandle> que configuram esta atividade de <xref:System.ServiceModel.Activities.Receive> dentro de fluxo de trabalho.  Clique no botão de reticências próximo à propriedade de <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> na grade de propriedades para abrir a caixa de diálogo **Adicionar Inicializadores de Correlação** .  [!INCLUDE[crabout](../test/includes/crabout_md.md)] usando esta caixa, consulte o tópico de [Add CorrelationInitializers Dialog Box](../workflow-designer/add-correlationinitializers-dialog-box.md) .|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>|False|Especifica o cabeçalho da ação de mensagem.  Se não é explicitamente definida, seu valor por padrão:<br /><br />  **https:\/\/tempuri.org\/ {namespace do contrato de serviço} {}\/o nome do contrato de serviço\/{} nome da operação.**|  
  
## Consulte também  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)