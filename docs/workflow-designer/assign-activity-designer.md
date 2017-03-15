---
title: "Assign Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Assign.UI"
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Assign Activity Designer
O designer de atividade de **Atribuir** é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.Assign> .  
  
## A atividade atribuir  
 A atividade de <xref:System.Activities.Statements.Assign> atribui um valor a uma variável ou um argumento.  
  
### Usando o designer de atividade atribuir  
 O designer de atividade de **Atribuir** pode ser encontrado na categoria de **Primitivas** de **Caixa de Ferramentas**, que é acessada clicando na guia **Caixa de Ferramentas** \(como alternativa, **Caixa de Ferramentas** partir do menu de **Modo de Visualização** ou CTRL\+ALT\+X.\)  
  
 O designer de atividade de **Atribuir** pode ser arrastado de **Caixa de Ferramentas** e ser solto sobre a superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] onde as atividades nunca são colocadas em geral, como em <xref:System.Activities.Statements.Sequence>.  Isso cria uma atividade de <xref:System.Activities.Statements.Assign> com **DisplayName** padrão Atribua.  <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade de **Atribuir** ou na caixa de **DisplayName** da grade de propriedade.  
  
### As propriedades atribuir  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Assign> e descreve como elas são usadas no designer.  Essas propriedades podem ser editadas na grade de propriedade e algumas delass podem ser editadas na superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] .  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.Assign> .  O padrão é atribui.  Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|  
|<xref:System.Activities.Statements.Assign.To%2A>|True|A variável ou o argumento para que <xref:System.Activities.Statements.Assign.Value%2A> é atribuído.  Isso deve ser um identificador válido Visual Basic.  Para definir a propriedade, digite uma expressão do Visual Basic na caixa de **A** no designer de atividade de **Atribuir** ou na grade de propriedade.|  
|<xref:System.Activities.Statements.Assign.Value%2A>|True|O valor que é atribuído à variável.  Para definir <xref:System.Activities.Statements.Assign.Value%2A>, digite uma expressão do Visual Basic na caixa de **Valor** no designer de atividade de **Atribuir** ou na grade de propriedade.|  
  
## Consulte também  
 [Primitives](../workflow-designer/primitives-activity-designers.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)