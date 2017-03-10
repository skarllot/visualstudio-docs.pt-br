---
title: "The selected connection uses an unsupported database provider | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# The selected connection uses an unsupported database provider
Esta mensagem aparece quando você arrasta itens que não usam o .NET Framework Data Provider para SQL Server na **Server Explorer**\/**Database Explorer** até o [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).  
  
 O [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] suporta apenas conexões de dados que usam o provedor do .NET Framework para SQL Server. Apenas as conexões com o Microsoft SQL Server ou o arquivo de banco de dados do Microsoft SQL Server são válidas.  
  
### Para corrigir este erro  
  
-   Adicionar itens somente as conexões de dados que usam o .NET Framework Data Provider para SQL Server para o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
## Consulte também  
 <xref:System.Data.SqlClient>   
 [Conectando a dados no Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Provedores de dados .NET Framework](../Topic/.NET%20Framework%20Data%20Providers.md)   
 [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [Criando aplicativos de dados](../data-tools/creating-data-applications.md)