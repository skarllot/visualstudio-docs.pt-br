---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Workflow.Runtime.Hosting.PersistenceException | Microsoft Docs"
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
  - "EHWRHPersistence"
helpviewer_keywords: 
  - "Exceção PersistenceException"
  - "Exceção System.Workflow.Runtime.Hosting.PersistenceException"
ms.assetid: cb2fb820-f990-4728-9a7f-5ec6fd8d5b10
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Workflow.Runtime.Hosting.PersistenceException
Um <xref:System.Workflow.Runtime.Hosting.PersistenceException> exceção é lançada quando o serviço de persistência não pode atender uma solicitação.  
  
## Comentários  
 O <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> lança um <xref:System.Workflow.Runtime.Hosting.PersistenceException> se não puder concluir uma solicitação para confirmar um escopo concluído ou o estado da instância de fluxo de trabalho para seu banco de dados.  
  
 Se você implementar um serviço de persistência derivando de <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> classe ou o <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> classe, você pode lançar o <xref:System.Workflow.Runtime.Hosting.PersistenceException> com uma mensagem apropriada para indicar qualquer condição de erro encontrada pelo serviço que impede que atenda a uma solicitação feita pelo mecanismo de tempo de execução de fluxo de trabalho.  
  
 Consulte <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> para obter mais informações.  
  
## Consulte também  
 <xref:System.Workflow.Runtime.Hosting.PersistenceException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)