---
title: "Sequence Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Sequence.UI"
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Sequence Activity Designer
A atividade de <xref:System.Activities.Statements.Sequence> contém uma coleção ordenada de atividades filhos que executa em ordem.  
  
 Outra maneira de executar um conjunto de atividades em ordem é usar uma atividade de <xref:System.Activities.Statements.Flowchart> .  Considere usar [Flowchart](../workflow-designer/flowchart-activity-designer.md) quando você tiver uma ramificação simples ou um fluxo de programa loop que você deseja modelagem esquematicamente.  
  
## Usando o designer de atividade de sequência  
 Para adicionar uma atividade de <xref:System.Activities.Statements.Sequence> , arraste o designer de atividade de **Sequência** de **Caixa de Ferramentas** e solte\-o sobre a superfície de [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] .  Para adicionar uma atividade filho para esta atividade de <xref:System.Activities.Statements.Sequence> , arraste alguma outra atividade de **Caixa de Ferramentas** e soltar\-la no triângulo na caixa com o texto “atividade de dica operação aqui”.  
  
### Propriedades de atividade da sequência em Designer de Fluxo de Trabalho  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Sequence> e descreve como elas são usadas no designer.  Essas propriedades podem ser editadas na grade de propriedade ou na superfície de designer.  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável do designer de atividade de <xref:System.Activities.Statements.Sequence> no cabeçalho.  O valor padrão é sequência.  O valor pode ser editado na grade de propriedade ou diretamente no cabeçalho do designer de atividade.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|  
  
## Consulte também  
 [Flowchart](../workflow-designer/flowchart-activity-designer.md)   
 [Control Flow](../workflow-designer/control-flow-activity-designers.md)