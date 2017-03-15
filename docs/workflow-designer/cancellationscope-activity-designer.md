---
title: "CancellationScope Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.CancellationScope.UI"
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# CancellationScope Activity Designer
O designer de atividade de **CancellationScope** é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.CancellationScope> .  
  
## A atividade de CancellationScope  
 A atividade de <xref:System.Activities.Statements.CancellationScope> permite que você especifique uma atividade para a lógica de execução e cancelar para a atividade.  
  
### Usando o designer de atividade de CancellationScope  
 O designer de atividade de **CancellationScope** pode ser encontrado na categoria de **Transação** de **Caixa de Ferramentas**, que é acessada clicando na guia **Caixa de Ferramentas** de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(como alternativa, **Barra de Ferramentas** partir do menu de **Modo de Visualização** , ou CTRL\+ALT\+X.\)  
  
 O designer de atividade de **CancellationScope** pode ser arrastado de **Caixa de Ferramentas** e ser solto sobre a superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] onde quer que as atividades são colocadas em geral, como em <xref:System.Activities.Statements.Sequence>.  Isso cria uma atividade de <xref:System.Activities.Statements.CancellationScope> com <xref:System.Activities.Activity.DisplayName%2A> padrão de CancellationScope.  O valor de <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade de **CancellationScope** ou na caixa de **DisplayName** da grade de propriedade.  
  
### As propriedades de CancellationScope  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.CancellationScope> e descreve como elas são usadas no designer.  A propriedade de <xref:System.Activities.Activity.DisplayName%2A> pode ser editada na grade de propriedade mas outras propriedades devem ser editadas na superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] .  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável opcional de atividade de <xref:System.Activities.Statements.CancellationScope> .  O padrão é CancellationScope.  Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|  
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Especifica a atividade para que a lógica cancelar é fornecida.  Para adicionar a atividade de <xref:System.Activities.Statements.CancellationScope.Body%2A> , soltar uma atividade de **Caixa de Ferramentas** na caixa de **Corpo** no designer de atividade de **CancellationScope** com texto “atividade de dica operação aqui”.|  
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|Especifica a atividade que é executado no caso de cancelamento.  Para adicionar a atividade de <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> , soltar uma atividade de **Caixa de Ferramentas** na caixa de **CancellationHandler** no designer de atividade de **CancellationScope** com texto “atividade de dica operação aqui”.|  
  
## Consulte também  
 [Transaction](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)