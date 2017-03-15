---
title: "TerminateWorkflow Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TerminateWorkflow.UI"
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# TerminateWorkflow Activity Designer
O designer de atividade de **TerminateWorkflow** é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.TerminateWorkflow> .  
  
## A atividade de TerminateWorkflow  
 A atividade de <xref:System.Activities.Statements.TerminateWorkflow> finaliza a execução de um fluxo de trabalho.  
  
### Usando o designer de atividade de TerminateWorkflow  
 O designer de atividade de **TerminateWorkflow** pode ser encontrado na categoria de **Tempo de execução** de **Caixa de Ferramentas**, que é acessada clicando na guia **Caixa de Ferramentas** \(como alternativa, **Caixa de Ferramentas** partir do menu de **Modo de Visualização** ou CTRL\+ALT\+X.\)  
  
 O designer de atividade de **TerminateWorkflow** pode ser arrastado de **Caixa de Ferramentas** e ser solto sobre a superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] onde quer que as atividades são colocadas em geral, como em <xref:System.Activities.Statements.Sequence>.  Isso cria uma atividade de <xref:System.Activities.Statements.TerminateWorkflow> com **DisplayName** padrão de TerminateWorkflow.  <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade de **TerminateWorkflow** ou na caixa de **DisplayName** da grade de propriedade.  
  
### As propriedades de TerminateWorkflow  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.TerminateWorkflow> e descreve como elas são usadas no designer.  Essas propriedades podem ser editadas na grade de propriedade e algumas delass podem ser editadas na superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] .  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.TerminateWorkflow> .  O padrão é TerminateWorkflow.  Embora o nome para exibição não é necessário restrita, é uma prática recomendada usar um nome para exibição.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|A exceção para indicar quando o fluxo de trabalho é encerrado.  Defina essa propriedade na grade de propriedade.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|A razão que explica como o fluxo de trabalho foi encerrado.  Defina essa propriedade na grade de propriedade.|  
  
## Consulte também  
 [Runtime](../workflow-designer/runtime-activity-designers.md)   
 [Persist](../workflow-designer/persist-activity-designer.md)