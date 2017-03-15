---
title: "The objects you are adding to the designer use a different data connection than the designer is currently using | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# The objects you are adding to the designer use a different data connection than the designer is currently using
Os objetos que você está adicionando ao designer de usam uma conexão de dados diferentes, o designer está usando atualmente. Você deseja substituir a conexão usada pelo designer?  
  
 Quando você adiciona itens a [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\), todos os itens usam uma conexão de dados compartilhados. \(A superfície de design representa a <xref:System.Data.Linq.DataContext>, que usa uma única conexão para todos os objetos na superfície.\) Se você adicionar um objeto para o designer que usa uma conexão de dados é diferente da conexão de dados que está sendo usado atualmente pelo designer, essa mensagem será exibida. Para resolver esse erro, você pode optar por manter a conexão existente. Se você fizer essa opção, o objeto selecionado não será adicionado. Como alternativa, você pode optar por adicionar o objeto e redefinir a <xref:System.Data.Linq.DataContext> conexão para a nova conexão.  
  
> [!NOTE]
>  Se você clicar em **Sim**, classes de entidade todas no [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] são mapeados para a nova conexão.  
  
### Para substituir a conexão existente com a conexão usada pelo objeto selecionado  
  
-   Clique em **Sim**.  
  
     O objeto selecionado é adicionado para o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], e o DataContext é definido para a nova conexão.  
  
### Para continuar a usar a conexão existente e cancelar a adição do objeto selecionado  
  
-   Clique em **não**.  
  
     A ação foi cancelada. O DataContext permanece definido para a conexão existente.  
  
## Consulte também  
 [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Conectando a dados no Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)