---
title: "You have selected a database object from an unsupported database provider | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# You have selected a database object from an unsupported database provider
O [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\) suporta apenas o .NET Framework Data Provider para SQL Server \(<xref:System.Data.SqlClient>\). Embora você possa clicar em **OK** e continuar a trabalhar com objetos de provedores de banco de dados sem suporte, você pode enfrentar um comportamento inesperado em tempo de execução.  
  
> [!NOTE]
>  Somente conexões de dados que usam o .NET Framework Data Provider para SQL Server são suportadas.  
  
### Para corrigir este erro  
  
-   Clique em **OK** para continuar a criar classes de entidade que mapeiam para a conexão que usa o provedor de banco de dados sem suporte. Você pode enfrentar um comportamento inesperado quando você usa provedores de banco de dados sem suporte.  
  
     \- ou \-  
  
-   Clique em **Cancelar**.  
  
     A ação é interrompida. Criar ou usar uma conexão de dados que usa o provedor do .NET Framework para SQL Server.  
  
## Consulte também  
 [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Provedores de dados .NET Framework](../Topic/.NET%20Framework%20Data%20Providers.md)   
 [Conectando a dados no Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)