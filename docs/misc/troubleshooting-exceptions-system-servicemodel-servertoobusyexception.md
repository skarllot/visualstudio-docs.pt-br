---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.ServiceModel.ServerTooBusyException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Exceção System.ServiceModel.ServerTooBusyException"
  - "Exceção ServerTooBusyException"
ms.assetid: 80eb606a-ab3c-48af-b747-c9902989a059
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.ServiceModel.ServerTooBusyException
Um <xref:System.ServiceModel.ServerTooBusyException> exceção é lançada quando um servidor está muito ocupado para aceitar uma mensagem.  
  
## Comentários  
 Esta exceção é derivada de <xref:System.ServiceModel.CommunicationException> que representa uma classe de erros recuperáveis que podem ser geradas durante a comunicação entre pontos de extremidade. Serviço e cliente robusto [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] aplicativos devem manipular essas exceções. Para impedir que um manipulador para <xref:System.ServiceModel.CommunicationException> capture o mais específico <xref:System.ServiceModel.ServerTooBusyException>, capture essa exceção antes de tratar <xref:System.ServiceModel.CommunicationException>.  
  
## Consulte também  
 <xref:System.ServiceModel.ServerTooBusyException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)