---
title: "DataContext Methods (O/R Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DataContext Methods (O/R Designer)
<xref:System.Data.Linq.DataContext> métodos \(no contexto do [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)\) são métodos da <xref:System.Data.Linq.DataContext> classe que executam procedimentos armazenados e funções em um banco de dados.  
  
 O <xref:System.Data.Linq.DataContext> classe é um [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] classe que atua como um canal entre um banco de dados do SQL Server e o [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] classes de entidade mapeados para esse banco de dados. O <xref:System.Data.Linq.DataContext> classe contém as informações de cadeia de caracteres de conexão e os métodos para se conectar a um banco de dados e manipular os dados no banco de dados. Por padrão, a <xref:System.Data.Linq.DataContext> classe contém vários métodos que você pode chamar, como o <xref:System.Data.Linq.DataContext.SubmitChanges%2A> método envia dados atualizados de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] classes para o banco de dados. Você também pode criar adicionais <xref:System.Data.Linq.DataContext> métodos que mapeiam para procedimentos armazenados e funções. Em outras palavras, chamar esses métodos personalizados executará a função ou procedimento armazenado no banco de dados que o <xref:System.Data.Linq.DataContext> método é mapeado para. Você pode adicionar novos métodos para o <xref:System.Data.Linq.DataContext> classe exatamente como você adicionará métodos para estender qualquer classe. No entanto, em discussões sobre <xref:System.Data.Linq.DataContext> métodos no contexto do [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], é o <xref:System.Data.Linq.DataContext> métodos que mapeiam para procedimentos armazenados e funções que estão sendo discutidas.  
  
## Painel de métodos  
 <xref:System.Data.Linq.DataContext> métodos que mapeiam para procedimentos armazenados e funções são exibidos no painel dos métodos de [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. O painel de métodos é o lado do **entidades** painel \(a superfície de design principal\). O painel de métodos lista todos os <xref:System.Data.Linq.DataContext> métodos que você criou usando o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Por padrão, o painel de métodos está vazio. Arraste procedimentos armazenados ou funções de **Server Explorer**\/**Database Explorer** até o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] criar <xref:System.Data.Linq.DataContext> métodos e preencher o painel de métodos. Para obter mais informações, consulte [Como: criar métodos DataContext mapeados para procedimentos armazenados e funções \(Object Relational Designer\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).  
  
> [!NOTE]
>  Abrir e fechar o painel de métodos clicando com o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] e, em seguida, clicando em **ocultar painel de métodos** ou **Mostrar painel de métodos**, ou use o atalho de teclado CTRL \+ 1.  
  
## Dois tipos de métodos de DataContext  
 Métodos de DataContext são os métodos que mapeiam para procedimentos armazenados e funções no banco de dados. Você pode criar e adicionar métodos de DataContext no painel dos métodos de [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Há dois tipos distintos de <xref:System.Data.Linq.DataContext> métodos; aqueles que retornam um ou mais conjuntos de resultados e os que não:  
  
-   <xref:System.Data.Linq.DataContext> métodos que retornam um ou mais conjuntos de resultados:  
  
     Crie esse tipo de <xref:System.Data.Linq.DataContext> método quando seu aplicativo precisa apenas para executar procedimentos armazenados e funções no banco de dados e retornar os resultados. Para obter mais informações, consulte [Como: criar métodos DataContext mapeados para procedimentos armazenados e funções \(Object Relational Designer\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System.Data.Linq.ISingleResult \< T \>, e <xref:System.Data.Linq.IMultipleResults>.  
  
-   <xref:System.Data.Linq.DataContext> métodos que não retornam conjuntos de resultados: como inserções, atualizações e exclusões para uma classe de entidade específica.  
  
     Crie esse tipo de <xref:System.Data.Linq.DataContext> método quando seu aplicativo precisa executar procedimentos armazenados em vez de usar o padrão [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] comportamento para salvar dados modificados entre uma classe de entidade e o banco de dados. Para obter mais informações, consulte [Como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões \(Object Relational Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## Tipos de retorno dos métodos DataContext  
 Quando você arrasta procedimentos armazenados e funções de **Server Explorer**\/**Database Explorer** até o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], o tipo de retorno de gerado <xref:System.Data.Linq.DataContext> método difere dependendo de onde você solta o item. Soltar itens diretamente em uma classe de entidade existente cria um <xref:System.Data.Linq.DataContext> método com o tipo de retorno da classe de entidade; soltar item em uma área vazia do [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] \(em qualquer painel\) cria um <xref:System.Data.Linq.DataContext> método que retorna um tipo gerado automaticamente. O tipo gerado automaticamente criado tem um nome que corresponda ao procedimento armazenado ou nome da função e propriedades que mapeiam para os campos retornados pelo procedimento armazenado ou função.  
  
> [!NOTE]
>  Você pode alterar o tipo de retorno de um <xref:System.Data.Linq.DataContext> método depois de adicioná\-lo ao painel de métodos. Para verificar ou alterar o tipo de retorno de um <xref:System.Data.Linq.DataContext> método, selecione\-o e inspecione o **tipo de retorno** propriedade no **propriedades** janela. Para obter mais informações, consulte [Como: alterar o tipo de retorno de um método DataContext \(Object Relational Designer\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 Arraste do banco de dados para a superfície de Object Relational Designer de objetos serão nomeados automaticamente, com base no nome dos objetos no banco de dados. Se você arrastar o mesmo objeto mais de uma vez, um número será acrescentado ao final do nome do novo que diferencia os nomes. Quando os nomes de objeto de banco de dados contêm espaços ou caracteres que não são suportados no Visual Basic ou c\#, o espaço ou caractere inválido é substituído por um sublinhado.  
  
## Consulte também  
 [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Stored Procedures](../Topic/Stored%20Procedures.md)   
 [Como: criar métodos DataContext mapeados para procedimentos armazenados e funções \(Object Relational Designer\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [Como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões \(Object Relational Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Passo a passo: Personalizando a inserção, atualização e exclusão de comportamento de classes de entidade](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
 [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)