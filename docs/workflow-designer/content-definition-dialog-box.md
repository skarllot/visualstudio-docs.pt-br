---
title: "Content Definition Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "MessageContent.UI"
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: 3
caps.handback.revision: 3
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Content Definition Dialog Box
A caixa de diálogo **Definição de conteúdo** é usada em [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] para configurar as propriedades de **Content** de <xref:System.ServiceModel.Activities.Send>, de <xref:System.ServiceModel.Activities.Receive>, de <xref:System.ServiceModel.Activities.SendReply>, e de atividades de <xref:System.ServiceModel.Activities.ReceiveReply> .  [!INCLUDE[crabout](../test/includes/crabout_md.md)] os designers de atividade usando esta caixa, consulte os tópicos de [Send](../workflow-designer/send-activity-designer.md), de [Receive](../workflow-designer/receive-activity-designer.md), de [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), e de [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .  
  
 A tabela a seguir descreve os elementos de \(UI\) de interface de usuário da caixa de diálogo **Inicializar Correlação** .  
  
|Elemento da Interface do Usuário|Descrição|  
|--------------------------------------|---------------|  
|**Mensagem**|Especifica o conteúdo de mensagem com a caixa de texto expressão de **Data da mensagem** e o tipo usando a caixa de listagem suspensa de **Tipo de mensagem** .  Por padrão, **Definição de conteúdo** usa <xref:System.ServiceModel.Activities.ReceiveMessageContent>, que espera <xref:System.ServiceModel.Channels.Message> ou um tipo de contrato de mensagem dentro da definição de serviço de fluxo de trabalho.|  
|**Parâmetros**|Clique no botão de opção de **Parâmetros** para usar <xref:System.ServiceModel.Activities.ReceiveParametersContent>, que espera um contrato de dados.  Use a grade de dados para definir uma coleção genérica de pares chave\/valor de <xref:System.Activities.OutArgument> cujos valores são atribuídos aos parâmetros variáveis no fluxo de trabalho atual.|  
  
 A caixa de diálogo **Conteúdo a definição** é usada por **Enviar**, por **Receber**, por **ReceiveAndSendReply**, e por designer de **SendAndReceiveReply** .  Acessá\-lo é semelhante em cada caso e exemplos de receptor são usados aqui para ilustrar o procedimento.  
  
 O designer de atividade de **Receber** pode ser arrastado de **Caixa de Ferramentas** e ser solto sobre a superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] onde quer que as atividades são colocadas em geral.  Isso cria uma atividade de <xref:System.ServiceModel.Activities.Receive> com <xref:System.Activities.Activity.DisplayName%2A> padrão Receive.  Selecione o designer de atividade de **Receber** e clique no botão de reticências ao lado do texto de conteúdo \(\) para a propriedade de **Conteúdo** na grade de propriedade para que a caixa de diálogo **Definição de conteúdo** aparece.  
  
 O conteúdo pode ser especificado dentro da seção de **Mensagem** para uma atividade de <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou dentro da seção de **Parâmetro** para uma atividade de <xref:System.ServiceModel.Activities.ReceiveParametersContent> .  
  
## Consulte também  
 [Workflow Designer UI Help](../workflow-designer/workflow-designer-ui-help.md)