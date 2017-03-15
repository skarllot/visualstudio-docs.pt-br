---
title: "Changing the return type of a DataContext method cannot be undone | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Changing the return type of a DataContext method cannot be undone
Alterar o tipo de retorno de um método DataContext não pode ser desfeita. Para reverter para o tipo gerado automaticamente, você deve arrastar o item do Server Explorer\/Database Explorer para o Object Relational Designer novamente. Tem certeza de que deseja alterar o tipo de retorno?  
  
 O tipo de retorno de um <xref:System.Data.Linq.DataContext> método difere dependendo de onde você solta o item [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Se você soltar um item diretamente em uma classe de entidade existente, um <xref:System.Data.Linq.DataContext> método que tem o tipo de retorno da classe de entidade é criado. Se você soltar um item em uma área vazia do [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], um <xref:System.Data.Linq.DataContext> método que retorna um tipo gerado automaticamente é criado. Você pode alterar o tipo de retorno de um <xref:System.Data.Linq.DataContext> método depois de adicioná\-lo ao painel de métodos. Para verificar ou alterar o tipo de retorno de um <xref:System.Data.Linq.DataContext> método, selecione\-o e clique no **tipo de retorno** propriedade no **propriedades** janela.  
  
### Para alterar o tipo de retorno de um DataContext  
  
-   Clique em **Sim**.  
  
### Para sair da caixa de mensagem e deixar o tipo de retorno inalterado  
  
-   Clique em **não**.  
  
### Para reverter para o tipo de retorno original após alterar o tipo de retorno  
  
1.  Selecione o <xref:System.Data.Linq.DataContext> método o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] e excluí\-lo.  
  
2.  Localize o item na **Server Explorer\/Database Explorer** e arraste\-a para o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Um <xref:System.Data.Linq.DataContext> método é criado com o tipo de retorno padrão original.  
  
## Consulte também  
 [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext Methods \(O\/R Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Como: criar métodos DataContext mapeados para procedimentos armazenados e funções \(Object Relational Designer\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)