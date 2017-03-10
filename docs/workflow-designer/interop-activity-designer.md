---
title: "Interop Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Interop.UI"
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Interop Activity Designer
O designer de atividade de **Interoperabilidade** é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.Interop> .  
  
## A atividade de Interoperabilidade  
 A atividade de <xref:System.Activities.Statements.Interop> gerencia a execução de tipos que derivam de <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> em um fluxo de trabalho.  
  
### Usando o designer de atividade de Interoperabilidade  
 O designer de atividade de **Interoperabilidade** pode ser encontrado na categoria de **Migração** de **Caixa de Ferramentas**, que é acessada clicando na guia **Caixa de Ferramentas** \(como alternativa, **Caixa de Ferramentas** partir do menu de **Modo de Visualização** ou CTRL\+ALT\+X.\)  
  
 A categoria de [Migration](../workflow-designer/migration-activity-designers.md) que contém a atividade de <xref:System.Activities.Statements.Interop> aparece apenas em **Caixa de Ferramentas** se seu projeto está definido [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)]completo.  
  
 Para projetos C\#, você pode novamente o destino o projeto para usar [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] completo clique com o botão direito do mouse no projeto em **Gerenciador de Soluções** e selecionando **Propriedades**.  Na guia de **Aplicativo** , selecione a opção de **NET Framework 4** em **Estrutura de Destino**.  Selecione o botão de **Sim** na caixa de diálogo **Modificação do Framework de Destino** que exibe solicitar que você confirme essa alteração.  
  
 Para projetos, você pode VB do destino novamente o projeto para usar [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] completo clique com o botão direito do mouse no projeto em **Gerenciador de Soluções** e selecionando **Propriedades**.  Na guia de **Compilar** , clique no botão de **Opções de Compilação Avançadas** .  Selecione **. Pesque Framework 4** de **Selecionar a lista de estrutura** e clique em **OK**.  Clique no botão de **Sim** na caixa de diálogo **Modificação do Framework de Destino** que exibe solicitar que você confirme essa alteração.  
  
 O designer de atividade de **Interoperabilidade** pode ser arrastado de **Caixa de Ferramentas** e ser solto sobre a superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] onde quer que as atividades são colocadas em geral, como em <xref:System.Activities.Statements.Sequence>.  Isso cria uma atividade de <xref:System.Activities.Statements.Interop> com **DisplayName** padrão de Interoperabilidade.  <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade de **Interoperabilidade** ou na caixa de **DisplayName** da grade de propriedade.  
  
 Clique no texto de **Clique em browse…** na caixa de **ActivityType** , no designer de atividade de **Interoperabilidade**  ou na grade de propriedade, para transferir anterior a caixa de diálogo **Procurar e selecione a. Pesque o tipo** .  Somente tipos para os trabalhos 3,0 ou o trabalho 3,5 atividades são mostrados \(isto é, somente os tipos derivados de <xref:System.Workflow.ComponentModel.Activity>\).  [!INCLUDE[crabout](../test/includes/crabout_md.md)] usando esta caixa para especificar um tipo, consulte o tópico de [Browse and Select a .NET Type Dialog Box](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) .  
  
### As propriedades de Interoperabilidade  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Interop> e descreve como elas são usadas no designer.  Essas propriedades podem ser editadas na grade de propriedade ou na superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] .  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.Interop> .  O padrão é Interoperabilidade.  Embora o nome para exibição não é necessário restrita, é uma prática recomendada usar um nome para exibição.|  
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|Especifica o tipo de atividade contida pela atividade de <xref:System.Activities.Statements.Interop> .  Este tipo especificado deve derivar de <xref:System.Workflow.ComponentModel.Activity>.|  
  
## Consulte também  
 [Migration](../workflow-designer/migration-activity-designers.md)