---
title: "How to: Use Breadcrumb Navigation | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# How to: Use Breadcrumb Navigation
Existem três maneiras principais de alterar o conjunto de atividades que são exibidas em [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]:  
  
1.  Clique duas vezes para furar na uma atividade filho.  
  
2.  Clique em um botão na barra de rastreamento para navegar em uma atividade de ancestral.  
  
3.  Expandir ou recolher atividades no lugar.  
  
### Usando a navegação de rastreamento  
  
1.  Clique duas vezes em uma atividade de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] para alterar a atividade raiz a atividade clicado.  A atividade clicada completa é expandida na raiz e seus ancestrais são mostrados na barra de rastreamento.  Isso é às vezes chamado perfuração ou de uma atividade.  
  
2.  Para navegar a um predecessor de atividade atual da raiz, clique na atividade na barra de rastreamento.  
  
### Expandindo ou recolhendo uma atividade no lugar  
  
1.  Clique nas vigas em uma atividade expande ou recolhe a atividade no lugar.  
  
2.  Quando o estado do estado de expansão é alterado clicando no botão, o novo estado de expansão é salvo em XAML.  
  
    > [!WARNING]
    >  Nem todas as atividades podem ser expandidos no lugar.  Há dois casos quando uma atividade não pode ser expandida no local: ou o pai da atividade não permite seus filhos sejam expandidos no lugar, \(por exemplo, as atividades em um fluxograma não podem ser expandidos no local\), ou o designer de atividade não se permite que é expandido no lugar.  Embora nenhum dos designers atividade estão incluídos em [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] tenham o último comportamento, quaisquer atividades personalizados podem exibir esse comportamento.  
  
### Tudo expandir ou recolher todas as atividades  
  
1.  Use os botões de **Expandir Tudo** e de **Recolher Tudo** na interface do usuário para expandir ou recolher todas as atividades na raiz atual do rastreamento.  Observe que expande todas e recolhe todo é estados globais.  Isso significa que quando você altera a atividade raiz usando a navegação de rastreamento, qualquer expandir ou recolhe qualquer estado persiste até que você tenha **Restaurar**.  
  
2.  Depois que você aplicar qualquer expandir ou recolhe qualquer estado, você pode clicar no botão de **Restaurar** que aparece para voltar ao estado ser aplicado a cada atividade anteriormente.  
  
    > [!WARNING]
    >  Se uma atividade, como <xref:System.Activities.Statements.Flowchart>, optou fora de expanda local, a funcionalidade associada com **Expandir Tudo** e botões de **Recolher Tudo** estão desativados no designer de **Fluxograma** .  [!INCLUDE[crabout](../test/includes/crabout_md.md)] o designer de **Fluxograma** , consulte o tópico de [Flowchart](../workflow-designer/flowchart-activity-designer.md) .  
  
    > [!WARNING]
    >  Expanda tudo também tem um efeito especial em **Opção** e no designer de atividade de **TryCatch** .  Quando você clica em **Expandir Tudo**, todos os casos de opção e qualquer try\/catch\/blocos finally são exibidos.  Clicando **Restaurar** ou **Recolher Tudo** retorna esses designers para seu estado padrão, que você pode clicar em casos\/bloco individuais para exibir seu conteúdo.