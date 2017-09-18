---
title: "The property &lt;property name&gt; cannot be deleted because it is participating in the association &lt;association name&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# The property &lt;property name&gt; cannot be deleted because it is participating in the association &lt;association name&gt;
A propriedade selecionada é definida como o **Propriedades de associação** para a associação entre as classes mencionadas na mensagem de erro. Propriedades não podem ser excluídas estão participando em uma associação entre classes de dados.  
  
 Definir o **Propriedades de associação** a uma propriedade diferente da classe de dados para habilitar a exclusão com êxito da propriedade desejada.  
  
### Para corrigir este erro  
  
1.  Selecione a linha de associação em Object Relational Designer que conecta as classes de dados indicadas na mensagem de erro.  
  
2.  Clique duas vezes na linha para abrir o **Editor de associação** caixa de diálogo.  
  
3.  Remova a propriedade do **Propriedades de associação**.  
  
4.  Tente excluir novamente a propriedade.  
  
## Consulte também  
 [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Como: criar uma associação \(relação\) entre classes LINQ to SQL \(Object Relational Designer\)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)