---
title: "Compensate Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Compensate.UI"
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Compensate Activity Designer
O designer de atividade de **Compensar** é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.Compensate> .  
  
## A atividade de compesação  
 A atividade de <xref:System.Activities.Statements.Compensate> chama explicitamente <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> para uma atividade contida em <xref:System.Activities.Statements.CompensableActivity>.  Se a atividade de <xref:System.Activities.Statements.Compensate> não é usada dentro de <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>, ou <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> de <xref:System.Activities.Statements.CompensableActivity>, então você deve especificar a propriedade de <xref:System.Activities.Statements.Compensate.Target%2A> .  
  
 <xref:System.Activities.Statements.CompensationToken> especificado por <xref:System.Activities.Statements.Compensate.Target%2A> fornece um meio para confirmar ou compensar explicitamente <xref:System.Activities.Statements.CompensableActivity> uma vez que <xref:System.Activities.Statements.CompensableActivity.Body%2A> de <xref:System.Activities.Statements.CompensableActivity> terminou com êxito.  
  
### Usando o designer de atividade de compesação  
 O designer de atividade de **Compensar** pode ser encontrado na categoria de **Transação** de **Caixa de Ferramentas**, que é acessada clicando na guia **Caixa de Ferramentas** no lado esquerdo de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(como alternativa, **Barra de Ferramentas** partir do menu de **Modo de Visualização** , ou CTRL\+ALT\+X.\)  
  
 O designer de atividade de **Compensar** pode ser arrastado de **Caixa de Ferramentas** e ser solto sobre a superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] onde quer que as atividades são colocadas em geral, como em <xref:System.Activities.Statements.Sequence>.  Isso cria uma atividade de <xref:System.Activities.Statements.Compensate> com <xref:System.Activities.Activity.DisplayName%2A> padrão Compensate.  O valor de <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade de **Compensar** ou na caixa de **DisplayName** da grade de propriedade.  
  
### As propriedades de compesação  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.CancellationScope> e descreve como elas são usadas no designer.  A propriedade de <xref:System.Activities.Activity.DisplayName%2A> pode ser editada na grade de propriedade ou na superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] , mas a propriedade de <xref:System.Activities.Statements.Compensate.Target%2A> deve ser editada na grade de propriedade.  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável opcional de atividade de <xref:System.Activities.Statements.Compensate> .  O padrão é compensa.|  
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|Especifica <xref:System.Activities.InArgument%601> que contém <xref:System.Activities.Statements.CompensationToken> para esta atividade de <xref:System.Activities.Statements.Compensate> .|  
  
## Consulte também  
 [Transaction](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate Activity Designer](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)