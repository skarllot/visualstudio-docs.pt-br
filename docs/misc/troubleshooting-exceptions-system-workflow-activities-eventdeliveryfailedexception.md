---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Workflow.Activities.EventDeliveryFailedException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHWAEventDeliveryFailed"
helpviewer_keywords: 
  - "Exceção System.Workflow.Activities.EventDeliveryFailedException"
  - "Exceção EventDeliveryFailedException"
ms.assetid: 85ee2cb8-5cd1-4878-9421-2a78614e819f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Workflow.Activities.EventDeliveryFailedException
Um <xref:System.Workflow.Activities.EventDeliveryFailedException> exceção é lançada quando um evento é gerado do host não pode ser entregue para a instância de fluxo de trabalho. Normalmente, o evento é gerado por uma <xref:System.Workflow.Activities.ExternalDataExchangeService> em uma instância de fluxo de trabalho. Essa classe não pode ser herdada.  
  
## Comentários  
 A seguinte cadeia de caracteres é adicionada ao log de eventos quando essa exceção é lançada: `Event '{1}' on interface type '{0}' for instance id '{2}' cannot be delivered`.  
  
 Ao usar um fluxo de trabalho de máquina de estado, você pode receber uma exceção com a mensagem `Queue '{0}' is not enabled`. Isso acontece quando o estado atual da máquina de estado não é capaz de manipular um evento específico. Por exemplo, a mensagem ocorre quando um estado diferente do estado atual contém o <xref:System.Workflow.Activities.EventDrivenActivity> que contém o <xref:System.Workflow.Activities.HandleExternalEventActivity> que é representado pela fila `'{0}'`.  
  
## Consulte também  
 <xref:System.Workflow.Activities.EventDeliveryFailedException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)