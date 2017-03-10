---
title: "How to: Create a Declarative Rule Condition (Legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "declarative rule conditions"
  - "condition statements, declarative rule conditions"
  - "Rule Condition Editor dialog box"
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# How to: Create a Declarative Rule Condition (Legacy)
Este tópico descreve como declarar uma condição de regra usando o novas [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] que direciona [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Uma instrução de condição for avaliada como **True** ou a **False**.  Uma condição declarativa de regra é uma declaração de condição que é criada usando [Rule Condition Editor Dialog Box \(Legacy\)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) e armazenadas como XML com o fluxo de trabalho.  Pode incluir os predicados que comparam o estado de fluxo de trabalho e a algebra booleano que combina vários predicados.  
  
 As condições declarativas de regras são usadas nas seguintes atividades de para fora da caixa do Windows Workflow Foundation:  
  
-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
### Para criar uma condição de regra declarativamente usando o editor de condição de regra  
  
1.  Na janela de **Propriedades** de atividade, clique na propriedade de **Condição** ou propriedade de **UntilCondition** , dependendo da atividade.  
  
2.  **Condição de Regra Declarativa** A partir da lista para a propriedade.  
  
3.  Expanda a propriedade de **Condição** ou de **UntilCondition** .  
  
4.  Clique na propriedade de **ConditionName** .  
  
5.  Clique nas reticências **\[…\]** de **ConditionName** para abrir a caixa de diálogo **Selecionar Condição**.  
  
6.  Clique **Nova condição** para abrir a caixa de diálogo **Editor de Condição de Regra** .  
  
7.  Digite a expressão para a condição na caixa de texto **Condição** .  
  
     Para obter informações sobre como criar expressões de condição, consulte [Rule Condition Editor Dialog Box \(Legacy\)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).  
  
8.  Quando você terminou de criar a expressão de condição, clique **OK** para fechar a caixa de diálogo e criar a condição de regra com um nome atribuído.  
  
     A caixa de diálogo **Selecionar Condição** abre.  
  
     Para obter informações sobre como usar a caixa de diálogo **Selecionar Condição** , consulte [Select Condition Dialog Box \(Legacy\)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
## Consulte também  
 [Legacy Workflow Activities](../workflow-designer/legacy-workflow-activities.md)   
 [Usando o ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066)   
 [Usando a atividade de IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075)   
 [Usando a atividade Replicator](http://go.microsoft.com/fwlink?LinkID=65080)   
 [Usando While atividade](http://go.microsoft.com/fwlink?LinkID=65091)   
 [Rule Condition Editor Dialog Box \(Legacy\)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)   
 [Select Condition Dialog Box \(Legacy\)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Usando condições em fluxos de trabalho](http://go.microsoft.com/fwlink?LinkID=65009)