---
title: "How to: Create a PolicyActivity Rule Set (Legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "PolicyActivity activity, creating rule sets"
  - "Rule Set Editor dialog box"
  - "PolicyActivity activity, selecting rule sets"
  - "Select Rule Set dialog box"
  - "rule sets, creating for PolicyActivity"
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# How to: Create a PolicyActivity Rule Set (Legacy)
Este tópico descreve como criar um conjunto de regras de atividade de política usando o novas [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] que direciona [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Após você ter arrastado um **política** item de atividade do **Toolbox** à superfície de design de fluxo de trabalho, você deve selecionar uma regra existente ou criar uma nova regra definida para o [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) atividade.  Você seleciona uma regra existente definida usando [Select Rule Set Dialog Box \(Legacy\)](../workflow-designer/select-rule-set-dialog-box-legacy.md) e você cria conjuntos de regra usando [Rule Set Editor Dialog Box \(Legacy\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).  
  
> [!NOTE]
>  Você pode abrir o [Rule Set Editor Dialog Box \(Legacy\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) caixa de diálogo diretamente clicando duas vezes em uma [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) atividade na superfície de design de fluxo de trabalho.  
  
### Para selecionar ou criar uma regra definida para uma atividade de PolicyActivity  
  
1.  Com o botão direito do [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)e, em seguida, clique em **propriedades** para abrir o **propriedades** janela.  
  
2.  Clique na propriedade de **RuleSetReference** .  
  
3.  Siga um destes procedimentos:  
  
    -   Clique nas reticências **\[…\]** de **RuleSetReference** e selecione uma regra existente definida em [Select Rule Set Dialog Box \(Legacy\)](../workflow-designer/select-rule-set-dialog-box-legacy.md).  Então vá para a etapa 10.  
  
         \-ou\-  
  
    -   Digite um nome para um conjunto de regras.  Clique nas reticências **\[…\]** de **RuleSetReference**, selecione **Editar** em [Select Rule Set Dialog Box \(Legacy\)](../workflow-designer/select-rule-set-dialog-box-legacy.md).  
  
         \-ou\-  
  
    -   Digite um nome para um conjunto de regras.  Expanda a propriedade **RuleSetReference** e selecione as reticências **\[…\]** na propriedade **Definição de RuleSet**.  
  
         O [Rule Set Editor Dialog Box \(Legacy\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) será aberto.  
  
4.  Em [Rule Set Editor Dialog Box \(Legacy\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md), clique **Adicionar Regra** para adicionar uma nova regra ao conjunto de regras.  
  
5.  Entre em **Nome**, em **Prioridade**, e em propriedades de **Reavaliação** , ou manter os valores padrão.  
  
6.  Digite o texto para **Condição**.  
  
7.  Digite o texto para **Ações Then** e **Ações Else**.  
  
8.  Clique **Adicionar Regra** novamente para adicionar outra regra.  
  
9. Quando terminar, clique em **OK**.  
  
## Consulte também  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Select Rule Set Dialog Box \(Legacy\)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Rule Set Editor Dialog Box \(Legacy\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)   
 [Usando a atividade Policy](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Legacy Workflow Activities](../workflow-designer/legacy-workflow-activities.md)