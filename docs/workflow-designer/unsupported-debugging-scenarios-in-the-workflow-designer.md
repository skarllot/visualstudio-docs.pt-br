---
title: "Unsupported debugging scenarios in the Workflow Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "sdanie"
manager: "erikre"
---
# Unsupported debugging scenarios in the Workflow Designer
Designer de Fluxo de Trabalho em [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] adicionou muitos novos recursos, mas ainda há alguns cenários de depuração que não oferece suporte.  Este documento detalha Designer de Fluxo de Trabalho sem suporte a depuração cenários.  
  
-   A execução não pode ser continuada após o código foi editado.  
  
-   A execução não pode ser continuada de um ponto arbitrário no fluxo de trabalho \(definido em seguida\).  
  
-   A execução não pode ser continuada até que o cursor seja alcançado \(execução ao cursor\).  
  
-   O designer de fluxo de trabalho não pode ser usado para criar fluxos de trabalho criados em código sem o uso de designer.  
  
-   Fluxos de trabalho criados em versões anteriores de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] não podem ser depurado no designer de [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] .  
  
-   Os pontos de interrupção não podem ser definidos nos links entre atividades ou nós de <xref:System.Activities.Statements.Flowchart> .  
  
-   A área de transferência não estão disponíveis durante a depuração.  
  
-   Os pontos de interrupção não são mantidas quando as atividades são copiadas ou coladas.  
  
-   Os pontos de interrupção de fluxo de trabalho não podem ser definidos na janela de pilha de chamadas.  
  
-   Ao criar pontos de interrupção no designer, **Linha** e as configurações de **Caractere** na caixa de diálogo **Novo Ponto de Interrupção** não são usados.  
  
-   A janela ou o menu de atalho do ponto de interrupção não suportam as seguintes colunas ou opções para depuração de fluxo de trabalho:  
  
    -   Condição  
  
    -   Contagem de acertos  
  
    -   Quando atingido  
  
    -   Função  
  
    -   Dados  
  
    -   Processo  
  
    -   Vá para a desmontagem