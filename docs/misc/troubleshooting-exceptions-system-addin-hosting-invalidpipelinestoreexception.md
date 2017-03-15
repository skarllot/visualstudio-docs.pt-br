---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.AddIn.Hosting.InvalidPipelineStoreException | Microsoft Docs"
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
  - "Exceção InvalidPipelineStoreException"
  - "Exceção System.AddIn.Hosting.InvalidPipelineStoreException"
ms.assetid: d12556bc-5cfd-481c-a27b-46ee2571e646
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.AddIn.Hosting.InvalidPipelineStoreException
O <xref:System.AddIn.Hosting.InvalidPipelineStoreException> exceção é lançada quando um diretório não foi encontrado e o usuário não tem permissão para acessar o caminho raiz do pipeline ou um caminho de suplemento.  
  
## Comentários  
 Ao contrário de <xref:System.IO.DirectoryNotFoundException>, essa exceção não fornece nenhuma informação de caminho. Isso impede que um usuário mal\-intencionado deliberadamente especifique caminhos incorretos e usar as informações retornadas pela exceção para determinar os caminhos reais.  
  
 A exceção é gerada pelos seguintes métodos de descoberta que criam e atualizam o armazenamento de informações do suplemento e pipeline: <xref:System.AddIn.Hosting.AddInStore.FindAddIns%2A>,<xref:System.AddIn.Hosting.AddInStore.Rebuild%2A>, <xref:System.AddIn.Hosting.AddInStore.RebuildAddIns%2A>, <xref:System.AddIn.Hosting.AddInStore.Update%2A>, e <xref:System.AddIn.Hosting.AddInStore.UpdateAddIns%2A>.  
  
## Consulte também  
 <xref:System.AddIn.Hosting.InvalidPipelineStoreException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)