---
title: "Delay Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Delay.UI"
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Delay Activity Designer
O designer de atividade de **Atraso** é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.Delay> .  
  
## A atividade do atraso  
 A atividade de <xref:System.Activities.Statements.Delay> atrasa a execução de um fluxo de trabalho para uma quantidade de tempo especificada.  
  
### Usando o designer de atividade do atraso  
 O designer de atividade de **Atraso** pode ser encontrado na categoria de **Primitivas** de **Caixa de Ferramentas**, que é acessada clicando na guia **Caixa de Ferramentas** de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(como alternativa, **Barra de Ferramentas** partir do menu de **Modo de Visualização** , ou CTRL\+ALT\+X.\)  
  
 O designer de atividade de **Atraso** pode ser arrastado de **Caixa de Ferramentas** e ser solto sobre a superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] onde quer que as atividades são colocadas em geral, como em <xref:System.Activities.Statements.Sequence>.  Isso cria uma atividade de <xref:System.Activities.Statements.Delay> com uma opção <xref:System.Activities.Activity.DisplayName%2A> de atraso.  <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade de **Atraso** ou na caixa de **DisplayName** da grade de propriedade.  
  
### As propriedades do atraso  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Delay> e descreve como elas são usadas no designer.  Essas propriedades podem ser editadas na grade de propriedade e alguns deless podem ser editados na superfície do designer de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.Delay> .  O padrão é atraso.  Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|  
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|A quantidade de tempo para atrasar o fluxo de trabalho.  Essa propriedade é definida na grade de propriedade.  Digite qualquer um <xref:System.TimeSpan> literal no 00:00 de formato: 00 ou uma expressão do Visual Basic para especificar a quantidade de tempo.|  
  
## Consulte também  
 [Primitives](../workflow-designer/primitives-activity-designers.md)   
 [Assign](../workflow-designer/assign-activity-designer.md)   
 [Delay Activity Designer](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)