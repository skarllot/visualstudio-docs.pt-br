---
title: "While Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.While.UI"
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# While Activity Designer
A atividade de <xref:System.Activities.Statements.While> executa a atividade contida em seu <xref:System.Activities.Statements.While.Body%2A> quando <xref:System.Activities.Statements.Condition%2A> especificado avaliar a **true**.  A atividade contida nunca pode executar.  Se você desejar que a atividade contida a ser executada pelo menos uma vez, use a atividade de <xref:System.Activities.Statements.DoWhile> em vez disso.  
  
## Quando propriedades em Designer de Fluxo de Trabalho  
 A tabela a seguir mostra as propriedades mais úteis de atividade de <xref:System.Activities.Statements.While> e descreve como elas são usadas no designer.  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável do designer de atividade de <xref:System.Activities.Statements.While> no cabeçalho.  O valor padrão é quando.  O valor pode ser editado na janela de **Propriedades** ou diretamente no cabeçalho do designer de atividade.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|  
|<xref:System.Activities.Statements.While.Body%2A>|False|Contém a atividade para executar quando <xref:System.Activities.Statements.Condition%2A> avaliar a **true**.|  
|<xref:System.Activities.Statements.Condition%2A>|True|Contém a expressão de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] que é avaliada para determinar se a atividade em <xref:System.Activities.Statements.While.Body%2A> deve ser executada.|  
  
## Consulte também  
 [Control Flow](../workflow-designer/control-flow-activity-designers.md)   
 [DoWhile](../workflow-designer/dowhile-activity-designer.md)