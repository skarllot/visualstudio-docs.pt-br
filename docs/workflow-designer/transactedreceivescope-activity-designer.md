---
title: "TransactedReceiveScope Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.TransactedReceiveScope.UI"
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# TransactedReceiveScope Activity Designer
O designer de **TransactedReceiveScope** é usado para criar e configurar uma atividade de <xref:System.ServiceModel.Activities.TransactedReceiveScope> .  
  
## A atividade de TransactedReceiveScope  
 A atividade de <xref:System.ServiceModel.Activities.TransactedReceiveScope> permite que você fluxo uma transação nas transações de servidor criadas por um fluxo de trabalho ou por um distribuidor.  
  
### Usando o designer de atividade de TransactedReceiveScope  
 O designer de atividade de **TransactedReceiveScope** pode ser encontrado na categoria de **Sistema de Mensagens** de **Caixa de Ferramentas**, que é acessada clicando na guia **Caixa de Ferramentas** em [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(como alternativa, **Barra de Ferramentas** partir do menu de **Modo de Visualização** , ou CTRL\+ALT\+X.\)  
  
 O designer de atividade de **TransactedReceiveScope** pode ser arrastado de **Caixa de Ferramentas** e ser solto sobre a superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] onde quer que as atividades são colocadas em geral.  Isso cria uma atividade de <xref:System.ServiceModel.Activities.TransactedReceiveScope> com **DisplayName** padrão de TransactedReceiveScope.  <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade de **TransactedReceiveScope** ou na caixa de **DisplayName** da grade de propriedade.  
  
 O designer de **TransactedReceiveScope** contém **Solicitação** e caixas de **Corpo** .  Esses são usados para configurar a propriedade de <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> , que especifica uma atividade de <xref:System.ServiceModel.Activities.Receive> e uma propriedade de <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> , que especifica algum outro <xref:System.Activities.Activity>.  <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> cria uma transação.  A transação é feita em ambientes para o escopo de <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> de modo que quaisquer atividades dentro desse escopo seja executado dentro desta transação.  
  
### As propriedades de TransactedReceiveScope  
 A tabela a seguir mostra as propriedades de <xref:System.ServiceModel.Activities.TransactedReceiveScope> e descreve como elas são usadas no designer.  Esse a propriedade de <xref:System.Activities.Activity.DisplayName%2A> pode ser editada na grade de propriedade ou na superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] , mas a outro deve ser editada na superfície de design.  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável opcional de atividade de <xref:System.ServiceModel.Activities.TransactedReceiveScope> .  O padrão é TransactedReceiveScope.<br /><br /> Embora o nome de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um nome para exibição.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|Ignora uma atividade de <xref:System.ServiceModel.Activities.Receive> no bloco de **Solicitação** na superfície do designer de atividade.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|Ignora <xref:System.Activities.Activity> no bloco de **Corpo** na superfície do designer de atividade.|  
  
## Consulte também  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)