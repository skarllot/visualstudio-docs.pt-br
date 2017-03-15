---
title: "Persist Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Persist.UI"
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Persist Activity Designer
O designer de atividade de **Persistir** é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.Persist> .  
  
## A atividade persistir  
 A atividade de <xref:System.Activities.Statements.Persist> salva um fluxo de trabalho em disco, se possível.  A atividade de <xref:System.Activities.Statements.Persist> não pode ser executada em uma zona de não persistência como, por exemplo, em uma atividade de <xref:System.Activities.Statements.TransactionScope> .  Se você usar uma atividade de <xref:System.Activities.Statements.Persist> em um escopo de não persistência, uma exceção é lançada em tempo de execução.  
  
### Usando o designer de atividade de persistir  
 O designer de atividade de **Persistir** pode ser encontrado na categoria de **Tempo de execução** de **Caixa de Ferramentas**, que é acessada clicando na guia **Caixa de Ferramentas** \(como alternativa, **Caixa de Ferramentas** partir do menu de **Modo de Visualização** ou CTRL\+ALT\+X.\)  
  
 O designer de atividade de **Persistir** pode ser arrastado de **Caixa de Ferramentas** e ser solto sobre a superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] onde quer que as atividades são colocadas em geral, como em <xref:System.Activities.Statements.Sequence>.  Isso cria uma atividade de <xref:System.Activities.Statements.Persist> com **DisplayName** padrão Persist.  <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade de **Persistir** ou na caixa de **DisplayName** da grade de propriedade.  
  
### As propriedades persistir  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Persist> e descreve como elas são usadas no designer.  Essas propriedades podem ser editadas na grade de propriedade e algumas delass podem ser editadas na superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] .  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.Persist> .  O padrão é persiste.  Embora o nome para exibição não é necessário restrita, é uma prática recomendada usar um nome para exibição.|  
  
## Consulte também  
 [Runtime](../workflow-designer/runtime-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)