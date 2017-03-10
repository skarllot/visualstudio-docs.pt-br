---
title: "TransactionScope Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TransactionScope.UI"
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# TransactionScope Activity Designer
O designer de atividade de **TransactionScope** é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.TransactionScope> .  
  
## A atividade de TransactionScope  
 A atividade de <xref:System.Activities.Statements.TransactionScope> executa a atividade contida em uma única transação.  As confirmações de transação quando a atividade de <xref:System.Activities.Statements.TransactionScope.Body%2A> e todos outros participantes na transação tiver terminado com êxito.  
  
### Usando o designer de atividade de TransactionScope  
 O designer de atividade de **TransactionScope** pode ser encontrado na categoria de **Transação** de **Caixa de Ferramentas**, que é acessada clicando na guia **Caixa de Ferramentas** de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(como alternativa, **Barra de Ferramentas** partir do menu de **Modo de Visualização** ou CTRL\+ALT\+X.\)  
  
 O designer de atividade de **TransactionScope** pode ser arrastado de **Caixa de Ferramentas** e ser solto sobre a superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] onde quer que as atividades são colocadas em geral, como em <xref:System.Activities.Statements.Sequence>.  Isso cria uma atividade de <xref:System.Activities.Statements.TransactionScope> com <xref:System.Activities.Activity.DisplayName%2A> padrão de TransactionScope.  O valor de <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade de **TransactionScope** ou na caixa de **DisplayName** da grade de propriedade.  
  
### As propriedades de TransactionScope  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.TransactionScope> e descreve como elas são usadas no designer.  As propriedades de <xref:System.Activities.Activity.DisplayName%2A> e de <xref:System.Activities.Statements.TransactionScope.Body%2A> podem ser editadas na superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] .  Mas as outras propriedades devem ser editadas na grade de propriedade.  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável opcional de atividade de <xref:System.Activities.Statements.TransactionScope> .  O padrão é TransactionScope.  Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|  
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|Especifica a atividade para executar em uma única transação.  Para adicionar a atividade de <xref:System.Activities.Statements.TransactionScope.Body%2A> , soltar uma atividade de **Caixa de Ferramentas** na caixa de **Corpo** no designer de atividade de **TransactionScope** com texto “atividade de dica operação aqui”.|  
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|True|Especifica <xref:System.Transactions.IsolationLevel> para este <xref:System.Activities.Statements.TransactionScope>.|  
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Especifica o intervalo de tempo \(formatados como o 00:00: 00, que indica horas: minutos: segundos\) que a transação precisará concluir.  O valor padrão é 1 \(00:01 minuto: 00\).|  
|<xref:System.Activities.Statements.TransactionScope>|True|Especifica o valor que indica se o fluxo de trabalho deve ser anuladas se a transação nulos.|  
  
## Consulte também  
 [Transaction](../workflow-designer/transaction-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)