---
title: "How to: Invoke a Windows Communication Foundation Contract Operation (Legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# How to: Invoke a Windows Communication Foundation Contract Operation (Legacy)
Este tópico descreve como chamar uma operação do contrato de [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] usando o novas [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] que direciona [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Após arrastar uma atividade de **SendActivity** da caixa de ferramentas para a superfície de design de fluxo de trabalho, você deve importar um contrato existente e determinar qual operação será chamada da atividade de **SendActivity** .  Você selecionar o contrato e as operações com [Choose Operation Dialog Box \(Legacy\)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
 Além disso, se você estiver usando um arquivo de configuração com o serviço, você precisará especificar <xref:System.Workflow.Activities.ChannelToken>.  <xref:System.Workflow.Activities.ChannelToken> identifica a configuração do ponto de extremidade a atividade de enviar usará para se conectar ao serviço de fluxo de trabalho.  
  
### Para chamar a reduzir a operação de uma atividade de SendActivity  
  
1.  Clique duas vezes na atividade de **SendActivity** no designer ou clique nas reticências próximo à propriedade de **ServiceOperationInfo** no painel de **Propriedades** .  
  
2.  Quando a caixa de diálogo **Escolher Operação** abre, clique **Importar** no canto superior direito da caixa de diálogo.  
  
     O [Browse and Select a .NET Type Dialog Box \(Legacy\)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) será aberto.  
  
3.  Pesquise por um assembly ou projeto que contém o contrato que você deseja.  
  
4.  Selecione o contrato e clique **OK**.  
  
5.  Em **Operações Disponíveis**, selecione a operação que você deseja chamar e clique **OK**.  
  
### Para especificar um token de canal  
  
1.  Selecione a atividade de <xref:System.Workflow.Activities.SendActivity> no designer.  
  
2.  No painel de **Propriedades** , especifique um nome para <xref:System.Workflow.Activities.ChannelToken>.  Este nome identifica unicamente o símbolo do canal.  
  
3.  Expanda o nó simbólico do canal e especifique um nome para o ponto final de cliente que você usará no campo de <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A> .  A configuração de ponto de extremidade de mesmo nome no arquivo de configuração será usada para configurar o canal.  
  
4.  Crie a configuração de ponto de extremidade no arquivo de configuração, se ele não existir.  Para obter mais informações sobre como configurar o cliente, consulte [Visão geral do cliente WCF](../Topic/WCF%20Client%20Overview.md).  
  
## Consulte também  
 [Choose Operation Dialog Box \(Legacy\)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [How to: Implement a WCF Contract Operation \(Legacy\)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Legacy Workflow Activities](../workflow-designer/legacy-workflow-activities.md)