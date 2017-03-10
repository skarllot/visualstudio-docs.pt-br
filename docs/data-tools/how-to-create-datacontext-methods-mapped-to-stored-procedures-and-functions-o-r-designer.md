---
title: "Como: criar m&#233;todos DataContext mapeados para procedimentos armazenados e fun&#231;&#245;es (Object Relational Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Como: criar m&#233;todos DataContext mapeados para procedimentos armazenados e fun&#231;&#245;es (Object Relational Designer)
Os procedimentos e funções armazenados podem ser adicionados ao [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] como métodos <xref:System.Data.Linq.DataContext>.  Chamar o método e passar os parâmetros necessários leva à execução do procedimento ou da função armazenada no banco de dados e ao retorno dos dados no tipo de retorno do método <xref:System.Data.Linq.DataContext>.  Para obter informações detalhadas sobre métodos <xref:System.Data.Linq.DataContext>, consulte [DataContext Methods \(O\/R Designer\)](../data-tools/datacontext-methods-o-r-designer.md).  
  
> [!NOTE]
>  Os procedimentos armazenados também podem ser usados para substituir o comportamento padrão em tempo de execução de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] que executa inserções, atualizações e exclusões quando alterações são salvas de classes de entidade para um banco de dados.  Para obter mais informações, consulte [Como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões \(Object Relational Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## Criando métodos DataContext  
 Você pode criar métodos <xref:System.Data.Linq.DataContext> arrastando procedimentos ou funções armazenadas do **Gerenciador de Servidores\/Gerenciador de Banco de Dados** para o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
> [!NOTE]
>  O tipo de retorno do método <xref:System.Data.Linq.DataContext> gerado varia de acordo com o local onde você solta o procedimento armazenado ou a função no [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  Soltar itens diretamente em uma classe de entidade existente cria um método <xref:System.Data.Linq.DataContext> com o tipo de retorno da classe de entidade.  Soltar itens em uma área vazia do [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] cria um método <xref:System.Data.Linq.DataContext> que retorna um tipo gerado automaticamente.  Você pode alterar o tipo de retorno de um método <xref:System.Data.Linq.DataContext> após adicioná\-lo ao painel de métodos.  Para inspecionar ou alterar o tipo de retorno de um método <xref:System.Data.Linq.DataContext>, selecione\-o e inspecione a propriedade **Tipo de Retorno** na janela **Propriedades**.  Para obter mais informações, consulte [Como: alterar o tipo de retorno de um método DataContext \(Object Relational Designer\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Para criar métodos DataContext que retornam tipos gerados automaticamente  
  
1.  Em **Gerenciador de Servidores**\/**Gerenciador de Banco de Dados**, expanda o nó **Procedimentos Armazenados** do banco de dados em que você está trabalhando.  
  
2.  Localize o procedimento armazenado desejado e arraste\-o para uma área vazia do [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     O método <xref:System.Data.Linq.DataContext> é criado com um tipo de retorno gerado automaticamente e aparece no painel **Métodos**.  
  
#### Para criar métodos DataContext com o tipo de retorno de uma classe de entidade  
  
1.  Em **Gerenciador de Servidores**\/**Gerenciador de Banco de Dados**, expanda o nó **Procedimentos Armazenados** do banco de dados em que você está trabalhando.  
  
2.  Localize o procedimento armazenado desejado e arraste\-o para uma classe de entidade existente no [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     O método <xref:System.Data.Linq.DataContext> é criado com o tipo de retorno da classe de entidade selecionada e aparece no painel **Métodos**.  
  
> [!NOTE]
>  Para obter informações sobre como alterar o tipo de retorno de métodos <xref:System.Data.Linq.DataContext> existentes, consulte [Como: alterar o tipo de retorno de um método DataContext \(Object Relational Designer\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
## Consulte também  
 [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext Methods \(O\/R Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Introdução a LINQ no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [Como escrever consultas LINQ em C\#](../Topic/How%20to:%20Write%20LINQ%20Queries%20in%20C%23.md)