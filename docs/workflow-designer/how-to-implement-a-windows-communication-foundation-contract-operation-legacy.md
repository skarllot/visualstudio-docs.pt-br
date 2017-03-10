---
title: "How to: Implement a Windows Communication Foundation Contract Operation (Legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: 7
caps.handback.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# How to: Implement a Windows Communication Foundation Contract Operation (Legacy)
Este tópico descreve como implementar uma operação do contrato de [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] usando o novas [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] que direciona [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Após arrastar uma atividade de **ReceiveActivity** da caixa de ferramentas para a superfície de design de fluxo de trabalho, você criará um novo contrato de [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] ou irá importar um contrato existente e implementará operações.  Você seleciona e\/ou cria o contrato e as operações com [Choose Operation Dialog Box \(Legacy\)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
### Para implementar uma operação do contrato de WCF  
  
1.  Clique duas vezes na atividade de **ReceiveActivity** no designer ou clique nas reticências próximo à propriedade de **ServiceOperationInfo** no painel de **Propriedades** .  
  
2.  Siga um destes procedimentos:  
  
    -   Clique **Adicionar Contrato** no canto superior direito da caixa de diálogo.  Isso criará um novo contrato e operação de [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] para você.  
  
         \-ou\-  
  
    -   Clique **Importar** no canto superior direito da caixa de diálogo.  O [Browse and Select a .NET Type Dialog Box \(Legacy\)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) será aberto.  Pesquise por um assembly ou projeto que contém o contrato que você deseja.  Selecione o contrato e clique **OK**.  
  
     Depois que um contrato é criado ou importado, você pode adicionar novos operações ao contrato criado ou importou isso.  Para adicionar uma nova operação, selecione o contrato e clique **Adicionar Operação** no canto superior direito da caixa de diálogo.  Quando você tiver terminado de adicionar operações, vá para a etapa 3.  
  
3.  Selecione a operação que você deseja associar com a atividade de **ReceiveActivity** .  Você pode manipular a definição da operação alterar o nome, parâmetros, propriedades, e as configurações de permissão da operação.  
  
     Para alterar o nome, digite o novo nome na caixa de texto **Nome da Operação** .  
  
     Clique na guia **Parâmetros** para acessar os parâmetros da operação.  Você pode alterar o nome, tipo, ou a direção de um parâmetro assim como adicionar ou excluir parâmetros da operação.  
  
     Clique na guia **Propriedades** para acessar o nível de proteção da operação e funcionalidade suportada de troca de mensagem da operação.  
  
     Clique na guia **Permissões** para especificar são permitidos a grupos que implementar a operação.  
  
4.  Clique **OK** e a atividade de **ReceiveActivity** exibirá o nome da operação para a operação que está implementando.  
  
5.  Coloque as atividades de fluxo de trabalho você usará para a implementação da operação dentro de atividade de **ReceiveActivity** .  
  
## Consulte também  
 [Choose Operation Dialog Box \(Legacy\)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [How to: Invoke a WCF Contract Operation \(Legacy\)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Legacy Workflow Activities](../workflow-designer/legacy-workflow-activities.md)