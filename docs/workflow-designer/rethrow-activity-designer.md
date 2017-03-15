---
title: "Rethrow Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Rethrow.UI"
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Rethrow Activity Designer
O designer de atividade de **Relançar** é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.Rethrow> .  
  
## A atividade de Relançar  
 A atividade de <xref:System.Activities.Statements.Rethrow> lança uma exceção lançada anteriormente.  Esta atividade somente pode ser usada em um manipulador de <xref:System.Activities.Statements.Catch> na atividade de <xref:System.Activities.Statements.TryCatch> .  
  
### Usando o designer de atividade de Relançar  
 O designer de atividade de **Relançar** pode ser encontrado na categoria de **Tratamento de Erros** de **Caixa de Ferramentas**, que é acessada clicando na guia **Caixa de Ferramentas** no lado esquerdo de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(como alternativa, **Barra de Ferramentas** partir do menu de **Modo de Visualização** ou CTRL\+ALT\+X.\)  
  
 O designer de atividade de **Relançar** pode ser arrastado de **Caixa de Ferramentas** e ser solto sobre a superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] onde quer que as atividades são colocadas em geral, como em <xref:System.Activities.Statements.Sequence>.  Isso cria uma atividade de <xref:System.Activities.Statements.Rethrow> com uma opção **DisplayName** throw.  O valor de <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade de **Relançar** ou na caixa de **DisplayName** da grade de propriedade.  
  
### As propriedades de Relançar  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Rethrow> e descreve como elas são usadas no designer.  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável opcional de atividade de <xref:System.Activities.Statements.ReThrow> .  O padrão é Relançar.|  
  
## Consulte também  
 [Collection](../workflow-designer/collection-activity-designers.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)