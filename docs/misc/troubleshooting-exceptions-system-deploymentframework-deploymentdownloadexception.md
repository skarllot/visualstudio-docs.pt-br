---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.DeploymentFramework.DeploymentDownloadException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Classe DeploymentDownloadException"
  - "implantação de aplicativos [c#], classe DeploymentDownloadException"
  - "Implantando aplicativos [c#], classe DeploymentDownloadException"
ms.assetid: 55ec7af5-b1d1-4db2-8af8-3c708f521cc7
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.DeploymentFramework.DeploymentDownloadException
A `T:System.DeploymentFramework.DeploymentDownloadException` ocorre se uma exceção de qualquer tipo de rede ocorre quando uma atualização do aplicativo está sendo baixada.  
  
## Dicas associadas  
 **Examine InnerException para determinar a exceção System.Net ou System.IO subjacente.**  
 Essa exceção ocorre sempre que há uma exceção de rede quando uma atualização do aplicativo está sendo carregada. Examinar a exceção <xref:System.Exception.InnerException%2A> propriedade para determinar a exceção subjacente.  
  
## Consulte também  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Instrução Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)