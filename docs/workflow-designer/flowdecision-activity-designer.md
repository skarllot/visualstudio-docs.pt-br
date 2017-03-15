---
title: "FlowDecision Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.FlowDecision.UI"
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# FlowDecision Activity Designer
O nó de <xref:System.Activities.Statements.FlowDecision> é um nó condicional que fornece uma ramificação para o fluxo de controle em uma das duas alternativas com base em se uma condição especificada é satisfeita.  Se o fluxo requer mais de duas ramificações, use <xref:System.Activities.Statements.FlowSwitch%601> em vez disso.  
  
## O nó de FlowDecision  
 Use <xref:System.Activities.Statements.FlowDecision> quando o fluxo pode ser transformada em dois caminhos.  Um nó de <xref:System.Activities.Statements.FlowDecision> tem <xref:System.Activities.Statements.FlowDecision.Condition%2A> e <xref:System.Activities.Statements.FlowNode> associados a cada um dos dois resultados possíveis: <xref:System.Activities.Statements.FlowDecision.True%2A> ou <xref:System.Activities.Statements.FlowDecision.False%2A>.  <xref:System.Activities.Statements.FlowDecision.Condition%2A> é avaliado e o valor da avaliação determina <xref:System.Activities.Statements.FlowNode> a seguir seja processado dentro de <xref:System.Activities.Statements.Flowchart>.  
  
### Utilizando o designer de FlowDecision  
 O designer de **FlowDecision** pode ser encontrado na categoria de **Fluxograma** de **Caixa de Ferramentas**, que é acessada clicando na guia **Caixa de Ferramentas** em [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(como alternativa, **Barra de Ferramentas** partir do menu de **Modo de Visualização** , ou CTRL\+ALT\+X.\)  
  
 O designer de **FlowDecision** pode ser arrastado de **Caixa de Ferramentas** e ser solto sobre a superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] em um designer de atividade de **Fluxograma** .  Isso cria <xref:System.Activities.Statements.FlowDecision> rotulado **decisão** dentro de atividade de <xref:System.Activities.Statements.Flowchart> .  O mouse sobre o designer e o quadrado de **Verdadeiro** e de **False** para os dois ramificações aparecem.  
  
 Após arrastar o designer de **FlowDecision** e outros designers em **Fluxograma**, os nós podem ser associados juntos para especificar ordem de execução.  Para criar um link entre um nó de origem \(incluindo **Verdadeiro** e ramificações de **False** de **FlowDecision**\) e um nó de destino, o mouse sobre o designer do nó de origem e quadradas alças aparecem em cada lado deles.  Clique em uma das alças de quadradas e arraste\-a segurando o botão do mouse na uma das alças que aparece de maneira similar ao redor do nó de destino quando você o mouse sobre ele.  Liberar o botão do mouse e um link é criado no meio esses dois nós que é representado como uma seta do designer de origem para o designer de destino.  
  
 A expressão que indica <xref:System.Activities.Statements.FlowDecision.Condition%2A> pode ser digitada na caixa de **Condição** da janela de **Propriedades** clicando em onde o texto de dica diz “inserir uma expressão de VB”.  
  
### As propriedades de FlowDecision  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.FlowDecision> e descreve como elas são usadas no designer.  Essas propriedades podem ser editadas na grade de propriedade ou na superfície de designer.  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|True|A condição que determina que caminho o controle de fluxo leva.|  
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|O caminho tomada pelo controle de fluxo se <xref:System.Activities.Statements.FlowDecision.Condition%2A> estiver satisfeito.|  
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|O caminho tomada pelo controle de fluxo se <xref:System.Activities.Statements.FlowDecision.Condition%2A> não estiver satisfeito.|  
  
## Consulte também  
 [Flowchart](../workflow-designer/flowchart-activity-designers.md)   
 [Flowchart](../workflow-designer/flowchart-activity-designer.md)   
 [FlowSwitch\<T\>](../workflow-designer/flowswitch-t-activity-designer.md)