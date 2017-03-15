---
title: "If Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.If.UI"
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# If Activity Designer
A atividade de <xref:System.Activities.Statements.If> avalia uma condição e executa uma atividade dependendo dos resultados da avaliação.  Esta atividade é mais útil ao usar um estilo modelando procedural de programação.  Uma atividade de <xref:System.Activities.Statements.If> pode ser aninhadas dentro de uma atividade de <xref:System.Activities.Statements.Sequence> ou uma atividade de <xref:System.Activities.Statements.Parallel> , por exemplo.  Se você estiver usando uma atividade de <xref:System.Activities.Statements.Flowchart> , considere usar uma atividade de <xref:System.Activities.Statements.FlowDecision> em vez disso.  
  
## Se as propriedades em Designer de Fluxo de Trabalho  
 A tabela a seguir mostra as propriedades mais úteis de atividade de <xref:System.Activities.Statements.If> e descreve como usá\-los no designer.  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Statements.If.Condition%2A>|True|A condição que determina que atividade filho para executar.  Para definir <xref:System.Activities.Statements.If.Condition%2A>, digite uma expressão de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] na caixa de **Condição** no designer de atividade de **Se** ou na grade de propriedade.|  
|<xref:System.Activities.Statements.If.Else%2A>|False|A atividade a executar se <xref:System.Activities.Statements.If.Condition%2A> é **false**.  Para adicionar uma atividade que é executada pelo ramificação de <xref:System.Activities.Statements.If.Else%2A> , soltar uma atividade de **Caixa de Ferramentas** na caixa de **Mais** no designer de atividade de **Se** com texto “atividade de dica operação aqui”.|  
|<xref:System.Activities.Statements.If.Then%2A>|False|A atividade a executar se <xref:System.Activities.Statements.If.Condition%2A> é **true**.  Para adicionar uma atividade que é executada pelo ramificação de <xref:System.Activities.Statements.If.Then%2A> , soltar uma atividade de **Caixa de Ferramentas** na caixa de **Em seguida** no designer de atividade de **Se** com texto “atividade de dica operação aqui”.|  
  
## Consulte também  
 [Sequence](../workflow-designer/sequence-activity-designer.md)   
 [Parallel](../workflow-designer/parallel-activity-designer.md)   
 [Control Flow](../workflow-designer/control-flow-activity-designers.md)