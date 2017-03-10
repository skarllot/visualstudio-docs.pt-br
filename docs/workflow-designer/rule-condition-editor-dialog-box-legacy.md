---
title: "Rule Condition Editor Dialog Box (Legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI"
helpviewer_keywords: 
  - "Rule Condition dialog box"
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Rule Condition Editor Dialog Box (Legacy)
Este tópico descreve como usar a caixa de diálogo **Editor de Condição de Regra** em [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]herdado.  Use [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Você pode criar e modificar condições declarativas de regra usando a caixa de diálogo **Editor de Condição de Regra** .  Essas condições de regras são expostas como propriedades nas seguintes atividades de para fora da caixa do Windows Workflow Foundation:  
  
-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
 Você acessa a caixa de diálogo **Editor de Condição de Regra** usando [Select Condition Dialog Box \(Legacy\)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
 A tabela a seguir descreve os elementos de \(UI\) de interface de usuário da caixa de diálogo **Editor de Condição de Regra** .  
  
|Elemento da Interface do Usuário|Descrição|  
|--------------------------------------|---------------|  
|**Condição:**|Insira a expressão para a condição de regra.|  
|**OK**|Clique para salvar a condição de regra.|  
  
## Inserindo expressões de condição  
 Expressões de condição estão inseridos como texto.  Você pode digitar **this.** no editor para os campos de referência, a propriedades, e para os métodos usados no fluxo de trabalho, usar IntelliSense\- como o menu.  Ou você pode digitar um nome de membro de fluxo de trabalho diretamente.  Você pode adicionar operadores lógicos a condição, como AND, OU, e NOT.  Você também pode adicionar predicados.  Um predicado é um operador binário e dois operandos.  Os operadores binários suportados são **\=\=**, **\>**, **\<**, **\>\=**, e **\<\=**.  Os operandos são suportados valor constante, função aritmética, e membros públicos o escopo.  
  
 Você pode especificar o tipo para comparação, e você pode comparar a **null** ou cadeia de caracteres vazia.  Você pode fazer chamadas aninhados aos membros em uma variável que contém um tipo complexo, por exemplo, `this.Address.State == "WA"`.  
  
 O editor de condição de regra oferece suporte aos seguintes operadores:  
  
-   Operadores relacionais: \=\=, \=\! \=  
  
-   Operadores de comparação: \<, \< \=, \>, \> \=  
  
-   Operadores aritméticos: \+, \-, \*,\/, MODIFICAÇÃO  
  
-   Operadores lógicos: E, & &, OR, &#124; &#124;, não\!  
  
-   Operadores bit a bit: &, &#124;  
  
 Precedência de operadores de expressão segue regras de precedência de operador C\#.  
  
 O editor de condição de regra suporta as seguintes expressões numéricas:  
  
 \=\= 1D de this.i \(resoluções a 1,0\)  
  
 \=\= 1E1 de this.i \(resoluções a 10,0\)  
  
 \=\= 1L de this.i \(resoluções como um longo\)  
  
 \=\= 1M de this.i \(resoluções como um decimal\)  
  
 \=\= 1F de this.i \(resoluções como um único\)  
  
 \=\= 1U de this.i \(resoluções como um unsigned int\)  
  
 Para obter mais informações sobre condições, consulte [usando condições em fluxos de trabalho](http://go.microsoft.com/fwlink?LinkID=65009).  
  
## Consulte também  
 [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)   
 [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)   
 [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)   
 [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)   
 [Select Condition Dialog Box \(Legacy\)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Usando condições em fluxos de trabalho](http://go.microsoft.com/fwlink?LinkID=65009)   
 [Legacy Designer for Windows Workflow Foundation UI Help](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)