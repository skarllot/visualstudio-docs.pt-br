---
title: "This related method is the backing method for the following default insert, update, or delete methods | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# This related method is the backing method for the following default insert, update, or delete methods
Este método relacionado é o método subjacente para os padrões insert, update ou delete métodos. Se ele for excluído, esses métodos também serão excluídos. Deseja continuar?  
  
 Selecionado `DataContext` método atualmente é usado como um dos métodos Insert, Update ou Delete para uma das classes de entidade em Object Relational Designer. Exclua o método selecionado irá fazer com que a classe de entidade que estava usando este método para reverter para o comportamento de tempo de execução padrão para executar a inserção, atualização, ou excluir durante uma atualização.  
  
### Para excluir o método selecionado, fazendo com que a classe de entidade para usar atualizações de tempo de execução  
  
-   Clique em **Sim**.  
  
     O método selecionado será excluído e as classes que usam esse método para substituir o comportamento de atualização são revertidas para usar o padrão de LINQ ao comportamento de tempo de execução do SQL.  
  
### Para fechar a caixa de mensagem, deixando o método selecionado inalterado  
  
-   Clique em **não**.  
  
     A caixa de mensagem fecha e nenhuma alteração será feita.  
  
## Consulte também  
 [DataContext Methods \(O\/R Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões \(Object Relational Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)