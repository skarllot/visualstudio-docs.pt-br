---
title: "Parallel Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Parallel.UI"
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
caps.latest.revision: 10
caps.handback.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Parallel Activity Designer
A atividade de <xref:System.Activities.Statements.Parallel> executa uma coleção de filhos atividades simultaneamente.  
  
## A atividade paralela  
 A atividade de <xref:System.Activities.Statements.Parallel> armazena as atividades filho em uma coleção de <xref:System.Activities.Statements.Parallel.Branches%2A> .  Use a atividade de <xref:System.Activities.Statements.Parallel> em vez de atividade de <xref:System.Activities.Statements.Sequence> se algumas das atividades filho podem ir ociosa.  
  
 A atividade de <xref:System.Activities.Statements.Parallel> tem uma propriedade de <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> que contém uma expressão especificada usuário de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] .  A atividade de <xref:System.Activities.Statements.Parallel> avalia essa propriedade após cada ramificação completa.  Se for avaliada como **True**, então a atividade de <xref:System.Activities.Statements.Parallel> concluída sem executar outros ramificações.  Se <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> não for avaliada como **True**, então a atividade de <xref:System.Activities.Statements.Parallel> termina quando todas as atividades filhos terminar.  
  
### Usando o designer paralelo de atividades  
 O designer de atividade de **Paralelo** pode ser encontrado na categoria de **Fluxo de Controle** de **Caixa de Ferramentas**, que é acessada clicando na guia **Caixa de Ferramentas** no lado esquerdo de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(como alternativa, **Barra de Ferramentas** partir do menu de **Modo de Visualização** , ou CTRL\+ALT\+X.\)  
  
 O designer de atividade de **Paralelo** pode ser arrastado de **Caixa de Ferramentas** e ser solto sobre a superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] onde quer que os designers de atividade são colocados normalmente, por exemplo, em um designer de atividade de **Sequência** .  Após solto na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], cria uma atividade de <xref:System.Activities.Statements.Parallel>, que contém por padrão <xref:System.Activities.Activity.DisplayName%2A> de **Parallel**  
  
 Para adicionar uma atividade à coleção de <xref:System.Activities.Statements.Parallel.Branches%2A> de atividade paralela, arraste outro designer de atividade de **Caixa de Ferramentas** e solte\-o triângulo no designer de atividade de **Paralelo** .  Os triângulos flanqueiam as atividades contidas em ramificações.  As atividades adicionais podem ser adicionadas repetindo este procedimento.  As atividades podem ser reorganizadas arrastando e soltando\-os os dentro do designer de atividade de **Paralelo** .  
  
### Propriedades paralelas de atividade em Designer de Fluxo de Trabalho  
 A tabela a seguir mostra as propriedades paralelas de atividade e descreve como elas são usadas no designer.  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável para exibição do designer de atividade no cabeçalho.  O valor padrão é **Parallel**.  O valor opcionalmente pode ser editado na grade de **Propriedades** ou diretamente no cabeçalho do designer de atividade.|  
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|Contém a coleção de atividades filhos sejam executadas.|  
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Avaliado após uma ramificação completa.  Se for avaliada como **True**, então o agendada em ramificações é cancelado.  Se esta propriedade não for definida ou não for avaliada como **False**, a atividade termina quando todas as atividades filhos terminar.  O valor padrão é **null**.|  
  
## Consulte também  
 [Sequence](../workflow-designer/sequence-activity-designer.md)   
 [ParallelForEach\<T\>](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Control Flow](../workflow-designer/control-flow-activity-designers.md)