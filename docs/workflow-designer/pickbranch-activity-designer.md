---
title: "PickBranch Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "11/29/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.PickBranch.UI"
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 10
caps.handback.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# PickBranch Activity Designer
<xref:System.Activities.Statements.PickBranch> fornece um caminho de execução baseado em uma atividade de <xref:System.Activities.Statements.Pick> que pode ser acionada por um evento de entrada.  
  
## PickBranch  
 os objetos de<xref:System.Activities.Statements.PickBranch> estão contidos na coleção de <xref:System.Activities.Statements.Pick.Branches%2A> de uma atividade de <xref:System.Activities.Statements.Pick> .  Cada <xref:System.Activities.Statements.PickBranch> está contido em uma ramificação de atividade de <xref:System.Activities.Statements.Pick> e pode ser executado devido a qualquer evento de entrada que serve como um disparador.  Dessa forma [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] fornece a modelagem com base em eventos de fluxo de controle.  Cada <xref:System.Activities.Statements.PickBranch> contém <xref:System.Activities.Statements.PickBranch.Trigger%2A> e <xref:System.Activities.Statements.PickBranch.Action%2A>.  
  
### Como usar o designer de atividade de picareta  
 O designer de **PickBranch** pode ser encontrado na categoria de **Fluxo de Controle** de **Caixa de Ferramentas**, que é acessada clicando na guia **Caixa de Ferramentas** em [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(como alternativa, **Barra de Ferramentas** partir do menu de **Modo de Visualização** , ou CTRL\+ALT\+X\).  
  
 Dois objetos vazios de <xref:System.Activities.Statements.PickBranch> com nomes para exibição de **Branch1** e **Branch2** são criados por padrão como os elementos de uma atividade de <xref:System.Activities.Statements.Pick> quando o designer de atividade de **Escolher** é solto inicialmente sobre a [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  Esses valores de propriedade respectivos de <xref:System.Activities.Statements.PickBranch.DisplayName%2A> podem ser editados no cabeçalho do designer de **PickBranch** ou dentro da janela de **Propriedades** para cada ramificação.  
  
 Há duas maneiras de adicionar objetos de <xref:System.Activities.Statements.PickBranch> à coleção de um objeto de <xref:System.Activities.Statements.Pick> : arrastando e soltando\-os o designer de **PickBranch** de **Caixa de Ferramentas** ou usando o menu de contexto na superfície de design de **Escolher** :  
  
1.  O designer de **PickBranch** cria <xref:System.Activities.Statements.PickBranch> quando é arrastada de **Caixa de Ferramentas** e arrastada em um dos ramificações de um designer de atividade de **Escolher** na superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] .  Novos objetos de <xref:System.Activities.Statements.PickBranch> podem ser colocados dentro do designer de <xref:System.Activities.Statements.Pick> para a esquerda ou direita de todos os elementos existentes de <xref:System.Activities.Statements.PickBranch> já contidos na coleção.  Ao arrastar um designer de **PickBranch** no designer de **Escolher** com um mouse, o designer de **Escolher** usa uma faixa azul cinza vertical para indicar onde <xref:System.Activities.Statements.PickBranch> é adicionado para uma determinada posicionamento do mouse.  
  
2.  Clique com o botão direito do mouse no designer de atividade de **Escolher** \(mas não o designer de **PickBranch** \) de dentro para obter um menu de contexto e selecione **Crie a ramificação** para adicionar novo <xref:System.Activities.Statements.PickBranch>.  Observe que novo <xref:System.Activities.Statements.PickBranch> é adicionado à direita dos objetos existentes de <xref:System.Activities.Statements.PickBranch> no designer de **Escolher** .  
  
 O designer de **PickBranch** pode ser expandido para revelar as caixas de **Disparador** e de **Ação** ou ser recolhido clicando nos sinais de interpolação duplas no lado direito dos cabeçalhos.  Editar <xref:System.Activities.Statements.PickBranch.Trigger%2A> e <xref:System.Activities.Statements.PickBranch.Action%2A> de cada <xref:System.Activities.Statements.PickBranch> soltando atividades nas caixas de **Disparador** e de **Ação** de seus designers.  
  
 Os objetos de <xref:System.Activities.Statements.PickBranch> na coleção de <xref:System.Activities.Statements.Pick.Branches%2A> de <xref:System.Activities.Statements.Pick> objeto, podem ser reorganizados arrastando os e soltando\-os para um novo local dentro do designer de **Escolher** .  O designer de **Escolher** usa uma faixa azul cinza vertical para indicar onde <xref:System.Activities.Statements.PickBranch> é adicionado para uma determinada posicionamento do mouse.  
  
 Há duas maneiras para excluir <xref:System.Activities.Statements.PickBranch>:  
  
1.  Selecione o designer de **PickBranch** e exclua\-o.  
  
2.  Selecione o designer de **PickBranch** , clique com o botão direito do mouse para obter o menu de contexto e selecione **Excluir**.  
  
 Certifique\-se de selecione o designer de **PickBranch** , como selecione uma das atividades em seu **Disparador** ou **Ação** encaixota exclui por engano uma dessas atividades e não do objeto de <xref:System.Activities.Statements.PickBranch> .  
  
### Propriedades de PickBranch em Designer de Fluxo de Trabalho  
 A tabela a seguir mostra as propriedades mais úteis de <xref:System.Activities.Statements.PickBranch> e descreve como usá\-los em [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|O nome amigável exibido no cabeçalho do designer de **PickBranch** .  O valor padrão é ramificação.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|  
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|Cada <xref:System.Activities.Statements.PickBranch> contém uma ação de <xref:System.Activities.Statements.PickBranch.Trigger%2A> que pode chamar <xref:System.Activities.Statements.PickBranch.Action%2A>.|  
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Cada <xref:System.Activities.Statements.PickBranch> contém <xref:System.Activities.Statements.PickBranch.Action%2A> que é executado se disparado.|  
  
## Consulte também  
 [Control Flow](../workflow-designer/control-flow-activity-designers.md)   
 [Escolha de atividade](../Topic/Pick%20Activity.md)   
 [Usando a escolha de atividade](../Topic/Using%20the%20Pick%20Activity.md)