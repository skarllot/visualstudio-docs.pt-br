---
title: "InitializeCorrelation Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.InitializeCorrelation.UI"
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# InitializeCorrelation Activity Designer
O designer de atividade de **InitializeCorrelation** é usado para criar e configurar uma atividade de <xref:System.ServiceModel.Activities.InitializeCorrelation> que é usada para estabelecer uma correlação entre mensagens antes de enviar ou de receber.  
  
## A atividade de InitializeCorrelation  
 Uma atividade de <xref:System.ServiceModel.Activities.InitializeCorrelation> é usada para inicializar correlações sem enviar e receber uma mensagem.  Correlação é inicializada normalmente ao enviar ou para receber uma mensagem.  Se correlação deve ser estabelecida antes que uma mensagem ser enviada ou recebida, use <xref:System.ServiceModel.Activities.InitializeCorrelation> para inicializar correlação.  
  
### Usando o designer de atividade de InitializeCorrelation  
 O designer de atividade de **InitializeCorrelation** pode ser encontrado na categoria de **Sistema de Mensagens** de **Caixa de Ferramentas**, que é acessada clicando na guia **Caixa de Ferramentas** em [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(como alternativa, **Barra de Ferramentas** partir do menu de **Modo de Visualização** ou CTRL\+ALT\+X.\)  
  
 O designer de atividade de **InitializeCorrelation** pode ser arrastado de **Caixa de Ferramentas** e ser solto sobre a superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] .  Isso cria uma atividade de <xref:System.ServiceModel.Activities.InitializeCorrelation> com <xref:System.Activities.Activity.DisplayName%2A> padrão de InitializeCorrelation.  <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade de **InitializeCorrelation** ou na caixa de **DisplayName** da janela de **Propriedades** .  
  
 <xref:System.ServiceModel.Activities.CorrelationHandle> pode ser especificar no campo de **Correlação** na janela de **Propriedades** na superfície do designer de atividade de **InitializeCorrelation** .  
  
 Clicando no botão da elipse além do campo de **CorrelationData** na janela de **Propriedades** ou na exibição “…” o texto de dica na superfície do designer de atividade de **InitializeCorrelation** exibe a caixa de diálogo **Inicializar Correlação** em que você pode especificar o identificador de correlação e os pares chave\-valor usados para inicializar.  [!INCLUDE[crabout](../test/includes/crabout_md.md)] usando esta caixa de diálogo, consulte o tópico de [Type Collection Editor Dialog Box](../workflow-designer/type-collection-editor-dialog-box.md) .  
  
### As propriedades de InitializeCorrelation  
 A tabela a seguir mostra as propriedades de <xref:System.ServiceModel.Activities.InitializeCorrelation> e descreve como elas são usadas no designer.  Essas propriedades podem ser editadas na janela de **Propriedades** ou na superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] .  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.ServiceModel.Activities.InitializeCorrelation> .  O valor padrão é InitializeCorrelation.<br /><br /> Embora o uso de um valor não padrão para <xref:System.Activities.Activity.DisplayName%2A> amigável não é necessário restrita, é uma prática recomendada usar um valor.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> usado para associar atividades de fluxo de trabalho em correlação.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Um dicionário de dados de correlação que se relacionam mensagens ao fluxo de trabalho instância.<br /><br /> Use a caixa de diálogo **Inicializar Correlação** para configurar <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>.  [!INCLUDE[crabout](../test/includes/crabout_md.md)] o uso esta caixa de diálogo, consulte o tópico de [Type Collection Editor Dialog Box](../workflow-designer/type-collection-editor-dialog-box.md) .|  
  
## Consulte também  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)