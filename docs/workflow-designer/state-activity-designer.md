---
title: "State Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.State.UI"
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "sdanie"
manager: "erikre"
---
# State Activity Designer
<xref:System.Activities.Statements.State> representa um estado em que um computador de estado pode estar.  
  
## Usando o designer de atividade de estado  
 Para adicionar <xref:System.Activities.Statements.State> a um fluxo de trabalho, arraste o designer de atividade de **Estado** da seção de **Computador de Estado** de **Caixa de Ferramentas** e solte\-o sobre a uma atividade de <xref:System.Activities.Statements.StateMachine> na superfície de [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] .  Uma atividade de <xref:System.Activities.Statements.State> pode ser arrastada em <xref:System.Activities.Statements.StateMachine> e as transições adicionados posteriormente; ou uma transição pode ser criada como a atividade de <xref:System.Activities.Statements.State> é descartada.  Para adicionar uma atividade de <xref:System.Activities.Statements.State> e criar uma transição em uma etapa, arraste uma atividade de **Estado** da seção de **Computador de Estado** de **Caixa de Ferramentas** e focalizar\-la sobre outro estado no designer de fluxo de trabalho.  Quando <xref:System.Activities.Statements.State> arrastado está sobre um outro <xref:System.Activities.Statements.State>, quatro triângulos aparecerão em torno do outro <xref:System.Activities.Statements.State>.  Se <xref:System.Activities.Statements.State> é solto em um dos quatro triângulos, é adicionado ao computador de estado e uma transição é criada de origem <xref:System.Activities.Statements.State> ao destino solto <xref:System.Activities.Statements.State>.  Para obter mais informações, consulte [Transition](../workflow-designer/transition-activity-designer.md).  
  
### Propriedades de atividade do estado em Designer de Fluxo de Trabalho  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.State> que podem ser definidas usando o designer de fluxo de trabalho e descreve como elas são usadas no designer.  Algumas dessas propriedades podem ser editadas na grade de propriedade e alguns podem ser editados na superfície de designer.  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Especifica o nome amigável do designer de atividade de <xref:System.Activities.Statements.State> no cabeçalho.  O valor padrão é **Estado**.  O valor pode ser editado na grade de propriedade ou diretamente no cabeçalho do designer de atividade.  <xref:System.Activities.Statements.State.DisplayName%2A> é usado em navegação de rastreamento que é exibida na parte superior do designer de fluxo de trabalho.<br /><br /> Embora não seja necessário <xref:System.Activities.Statements.State.DisplayName%2A> restrita, é uma prática recomendada usar um.|  
|<xref:System.Activities.Statements.State.Entry%2A>|False|Especifica a ação que ocorre quando esse estado é feito a transição para.  Quando a atividade de <xref:System.Activities.Statements.State> é expandida, esse valor pode ser definido arrastar uma atividade de **Caixa de Ferramentas** e soltando\-os à seção de **Entrada** de estado.|  
|<xref:System.Activities.Statements.State.Exit%2A>|False|Especifica a ação que ocorre quando esse estado é feito a transição fora.  Quando a atividade de <xref:System.Activities.Statements.State> é expandida, esse valor pode ser definido arrastar uma atividade de **Caixa de Ferramentas** e soltando\-os à seção de **Sair** de estado.|  
|<xref:System.Activities.Statements.State.Transitions%2A>|False|Lista as transições possíveis que originam de <xref:System.Activities.Statements.State>.  Cada item na lista possui um link a <xref:System.Activities.Statements.Transition> associado e de destino <xref:System.Activities.Statements.State>.  Clicar no link alternará o designer para uma exibição expandida de <xref:System.Activities.Statements.Transition> ou de <xref:System.Activities.Statements.State>.|  
  
## Consulte também  
 [StateMachine](../workflow-designer/statemachine-activity-designer.md)   
 [FinalState](../workflow-designer/finalstate-activity-designer.md)   
 [Transition](../workflow-designer/transition-activity-designer.md)