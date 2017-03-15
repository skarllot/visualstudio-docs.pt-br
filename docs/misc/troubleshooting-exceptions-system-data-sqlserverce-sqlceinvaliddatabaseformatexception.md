---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Data.SqlServerCe.SqlCeInvalidDatabaseFormatException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Exceção SqlCeInvalidDatabaseFormatException"
  - "Exceção System.Data.SqlServerCe.SqlCeInvalidDatabaseFormatException"
ms.assetid: f5ca1f40-4619-4523-807e-d5b20bfb05b0
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Data.SqlServerCe.SqlCeInvalidDatabaseFormatException
Um `System.Data.SqlServerCe.SqlCeInvalidDatabaseFormatException` exceção ocorre quando o SQL Server Compact abre um arquivo de banco de dados que foi criado em uma versão anterior do produto.  
  
## Comentários  
 Você pode atualizar o arquivo de banco de dados usando [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] ou usando a API `System.Data.SqlServerCe.SqlCeEngine.Upgrade`.  
  
 Para obter mais informações, consulte [SQL Server Compact 3.5 Class Library](http://go.microsoft.com/fwlink/?LinkID=102595).  
  
## Consulte também  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)