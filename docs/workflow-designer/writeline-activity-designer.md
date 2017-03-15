---
title: "WriteLine Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.WriteLine.UI"
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# WriteLine Activity Designer
O designer de atividade de **WriteLine** é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.WriteLine> .  
  
## A atividade WriteLine  
 Grava de atividade de <xref:System.Activities.Statements.Writeline> texto a <xref:System.IO.TextWriter> um objeto especificado.  Se nenhum <xref:System.IO.TextWriter> é especificado, <xref:System.Activities.Statements.Writeline> grava o texto no console.  
  
### Usando o designer de atividade WriteLine  
 O designer de atividade de **WriteLine** pode ser encontrado na categoria de **Primitivas** de **Caixa de Ferramentas**, que é acessada clicando na guia **Caixa de Ferramentas** de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(como alternativa, **Barra de Ferramentas** partir do menu de **Modo de Visualização** , ou CTRL\+ALT\+X.\)  
  
 O designer de atividade de **WriteLine** pode ser arrastado de **Caixa de Ferramentas** e ser solto sobre a superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] onde quer que as atividades são colocadas em geral, como em <xref:System.Activities.Statements.Sequence>.  Isso cria uma atividade de <xref:System.Activities.Statements.WriteLine> com <xref:System.Activities.Activity.DisplayName%2A> padrão WriteLine.  <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade de **WriteLine** ou na caixa de **DisplayName** da grade de propriedade.  
  
### As propriedades WriteLine  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.WriteLine> e descreve como elas são usadas no designer.  Essas propriedades podem ser editadas na grade de propriedade e algumas delass podem ser editadas na superfície do designer de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.WriteLine> .  O padrão é WriteLine.  Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é prática recomendada usar esse.|  
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|O texto a gravação.  Para definir a propriedade, digite uma expressão do Visual Basic na caixa de **Texto** no designer de atividade de **WriteLine** ou na grade de propriedade.|  
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|<xref:System.IO.TextWriter> a <xref:System.Activities.Statements.WriteLine> que grava <xref:System.Activities.Statements.WriteLine.Text%2A>.  O padrão é o console.|  
  
## Consulte também  
 [Primitives](../workflow-designer/primitives-activity-designers.md)   
 [Assign](../workflow-designer/assign-activity-designer.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)