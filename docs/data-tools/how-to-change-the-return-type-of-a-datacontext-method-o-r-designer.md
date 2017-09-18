---
title: "Como: alterar o tipo de retorno de um m&#233;todo DataContext (Object Relational Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Como: alterar o tipo de retorno de um m&#233;todo DataContext (Object Relational Designer)
O tipo de retorno de um método de <xref:System.Data.Linq.DataContext> \(criado com base em um procedimento ou uma função armazenadas\) diferem dependendo de onde você ignora o procedimento ou a função em [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  Se você soltar um item diretamente em uma classe existente de entidade, um método de <xref:System.Data.Linq.DataContext> que tem o tipo de retorno de classe de entidade é criado \(se o esquema dos dados retornados por correspondências armazenadas do procedimento ou função a forma de classe de entidade\).  Se você soltar um item em uma área vazia de [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], um método de <xref:System.Data.Linq.DataContext> que retorna um tipo gerado automaticamente é criado.  Você pode alterar o tipo de retorno de um método de <xref:System.Data.Linq.DataContext> depois de adicioná\-lo ao painel de métodos.  Verificar ou altere o tipo de retorno de um método de <xref:System.Data.Linq.DataContext>, selecione\-o e clique na propriedade de **Tipo de Retorno** na janela de **Propriedades** .  
  
> [!NOTE]
>  Você não pode reverter os métodos de <xref:System.Data.Linq.DataContext> que tem um tipo de retorno definida como uma classe de entidade para retornar o tipo gerado automaticamente usando a janela de **Propriedades** .  Para reverter um método de <xref:System.Data.Linq.DataContext> para retornar um tipo gerado automaticamente, você deve arraste o objeto de base de dados original em object relational Designer de Objetos novamente.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Para alterar o tipo de retorno de um método DataContext do tipo gerado automaticamente a uma entidade  
  
1.  Selecione o método de <xref:System.Data.Linq.DataContext> no painel de métodos.  
  
2.  Selecione **Tipo de Retorno** na janela de **Propriedades** e então seleciona uma classe de entidade disponível na lista de **Tipo de Retorno** .  Se a classe desejada de entidade não estiver na lista, ou adicioná\-lo a crie\-a em [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] para adicioná\-lo à lista.  
  
3.  Salve o arquivo. dbml.  
  
### Para alterar o tipo de retorno de um método DataContext de uma classe de entidade de volta para o tipo gerado automaticamente  
  
1.  Selecione o método de <xref:System.Data.Linq.DataContext> no painel de métodos e exclua\-o.  
  
2.  Arraste o objeto de base de dados de **Gerenciador de Servidores**\/**Gerenciador de Banco de Dados** em uma área vazia de object relational Designer de Objetos.  
  
3.  Salve o arquivo. dbml.  
  
## Consulte também  
 [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [DataContext Methods \(O\/R Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Como: criar métodos DataContext mapeados para procedimentos armazenados e funções \(Object Relational Designer\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)