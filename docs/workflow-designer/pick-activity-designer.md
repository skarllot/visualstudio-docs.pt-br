---
title: "Pick Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "11/29/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Pick.UI"
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
caps.handback.revision: 9
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Pick Activity Designer
A atividade de <xref:System.Activities.Statements.Pick> fornece o fluxo de controle baseado.  A atividade executa um dos vários ramificações em resposta a um evento disparando.  
  
## A atividade de picareta  
 Uma atividade de <xref:System.Activities.Statements.Pick> contém uma coleção de objetos <xref:System.Activities.Statements.PickBranch> , uma que a atividade de <xref:System.Activities.Statements.Pick> pode executar devido a qualquer evento de entrada que serve como um disparador.  Dessa forma [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] fornece a modelagem com base em eventos de fluxo de controle.  Cada <xref:System.Activities.Statements.PickBranch> contém <xref:System.Activities.Statements.PickBranch.Trigger%2A> e <xref:System.Activities.Statements.PickBranch.Action%2A>.  No início da execução de uma atividade de <xref:System.Activities.Statements.Pick> , todas as atividades do disparador de elementos de <xref:System.Activities.Statements.PickBranch> são agendadas.  Quando a primeira atividade concluir, a atividade correspondente de ação está agendada, e quaisquer atividades restantes do disparador serão canceladas.  
  
### Como usar o designer de atividade de picareta  
 O designer de atividade de **Escolher** pode ser encontrado na categoria de **Fluxo de Controle** de **Caixa de Ferramentas**, que é acessada clicando na guia **Caixa de Ferramentas** em [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(como alternativa, **Barra de Ferramentas** partir do menu de **Modo de Visualização** ou CTRL\+ALT\+X.\)  
  
 O designer de atividade de **Escolher** pode ser arrastado de **Caixa de Ferramentas** e ser solto sobre a superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] onde quer que os designers de atividade são colocados normalmente, por exemplo em um designer de atividade de **Sequência** .  Após solto na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], cria uma atividade de <xref:System.Activities.Statements.Pick> , que contém por padrão duas atividades vazios de <xref:System.Activities.Statements.PickBranch> como elementos com nomes para exibição de Branch1 e de Branch2.  Esses valores de propriedade respectivos de <xref:System.Activities.Statements.PickBranch.DisplayName%2A> podem ser editados no cabeçalho do designer de atividade de **PickBranch** ou dentro da janela de **Propriedades** para cada ramificação.  
  
 Há duas maneiras de adicionar atividades de <xref:System.Activities.Statements.PickBranch> à coleção de um objeto de <xref:System.Activities.Statements.Pick> : arrastando e soltando\-os o designer de **PickBranch** de **Caixa de Ferramentas** ou usando o menu de contexto na superfície de design de **Escolher** .  Para obter detalhes, consulte o tópico de [PickBranch](../workflow-designer/pickbranch-activity-designer.md) .  Observe que o único item que pode ser colocado dentro um designer de atividade de **Escolher** é um designer de atividade de **PickBranch** .  
  
### Escolha propriedades de atividade em Designer de Fluxo de Trabalho  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Pick> e descreve como elas são usadas no designer.  Essas propriedades podem ser editadas na grade de propriedade ou na superfície de designer.  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável do designer de atividade de <xref:System.Activities.Statements.Pick> no cabeçalho.  O valor padrão é picareta.  O valor pode ser editado na grade de propriedade ou diretamente no cabeçalho do designer de atividade.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|  
  
## Consulte também  
 [Control Flow](../workflow-designer/control-flow-activity-designers.md)   
 [Escolha de atividade](../Topic/Pick%20Activity.md)   
 [Usando a escolha de atividade](../Topic/Using%20the%20Pick%20Activity.md)