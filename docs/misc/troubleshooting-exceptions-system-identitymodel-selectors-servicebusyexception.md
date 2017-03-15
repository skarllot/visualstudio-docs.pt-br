---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.IdentityModel.Selectors.ServiceBusyException | Microsoft Docs"
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
  - "Exceção ServiceBusyException"
  - "Exceção System.IdentityModel.Selectors.ServiceBusyException"
ms.assetid: 88acdc6b-45ad-40c6-aa5c-3b56244edcee
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.IdentityModel.Selectors.ServiceBusyException
Um <xref:System.IdentityModel.Selectors.ServiceBusyException> exceção é gerada para indicar que o serviço CardSpace está ocupado processando outras solicitações. CardSpace não enfileira solicitações e pode atender a apenas uma solicitação por vez.  
  
 Determine se outra instância do CardSpace está em execução. Se não houver outra instância em execução, finalizá\-la interrompendo o processo de icardagt.exe no Gerenciador de tarefas.  
  
## Consulte também  
 <xref:System.IdentityModel.Selectors.ServiceBusyException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)