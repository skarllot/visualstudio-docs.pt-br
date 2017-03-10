---
title: "Conjuntos de dados de consulta | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
caps.latest.revision: 8
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Conjuntos de dados de consulta
Para procurar por registros específicos em um conjunto de dados, use o método FindBy na DataTable, ou você pode escrever seu próprio loop foreach sobre a coleção de linhas da tabela ou você pode usar [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md). LINQ to DataSet.  
  
## Sensibilidade de caso do conjunto de dados  
 Dentro de um conjunto de dados, nomes de tabela e coluna são por padrão de maiúsculas e minúsculas — ou seja, uma tabela em um conjunto de dados chamado "Clientes" também pode ser chamada como "customers". Isso coincide com as convenções de nomenclatura em vários bancos de dados, incluindo o comportamento padrão do SQL Server, onde os nomes dos elementos de dados não podem ser diferenciados apenas por caso.  
  
> [!NOTE]
>  Ao contrário de conjuntos de dados, documentos XML diferenciam maiúsculas de minúsculas, para que os nomes de elementos de dados definidos em esquemas diferenciam maiúsculas de minúsculas. Por exemplo, o protocolo de esquema permite que o esquema definir uma tabela chamada "Clientes" e uma tabela diferente chamada "clientes". Isso pode resultar em conflitos de nome quando um esquema que contém elementos que diferem somente no caso é usado para gerar uma classe de conjunto de dados.  
  
 No entanto, diferenciação de maiúscula e minúsculas pode ser um fator de como os dados são interpretados no conjunto de dados. Por exemplo, se você filtrar dados em uma tabela de conjunto de dados, os critérios de pesquisa podem retornar resultados diferentes dependendo se a comparação diferencia maiúsculas de minúsculas ou não. Você pode controlar as maiúsculas e minúsculas de filtragem, pesquisa e classificação definindo o conjunto de dados <xref:System.Data.DataSet.CaseSensitive%2A> propriedade. Todas as tabelas no dataset herdam o valor dessa propriedade por padrão. \(Você pode substituir essa propriedade para cada tabela individual, definindo a tabela <xref:System.Data.DataTable.CaseSensitive%2A> propriedade.\)  
  
## Para localizar uma linha específica em uma tabela de dados  
  
#### Para localizar uma linha em um dataset digitado com um valor de chave primária  
  
-   Chamar fortemente tipado `FindBy` método que usa a chave primária da tabela para localizar uma linha.  
  
     No exemplo a seguir, o `CustomerID` coluna é a chave primária da `Customers` tabela isso gerado `FindBy` método é `FindByCustomerID`. O exemplo mostra como atribuir um determinado <xref:System.Data.DataRow> a uma variável usando gerado `FindBy` método.  
  
     [!CODE [VbRaddataEditing#18](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataEditing#18)]  
  
#### Para localizar uma linha em um dataset não tipado com um valor de chave primária  
  
-   Chamar o <xref:System.Data.DataRowCollection.Find%2A> método de um <xref:System.Data.DataRowCollection> coleção, passando a chave primária como um parâmetro.  
  
     O exemplo a seguir mostra como declarar uma nova linha chamada `foundRow` e atribua a ela o valor de retorno de <xref:System.Data.DataRowCollection.Find%2A> método. Se a chave primária for encontrada, o conteúdo do índice da coluna 1 é exibido em uma caixa de mensagem.  
  
     [!CODE [VbRaddataEditing#19](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataEditing#19)]  
  
## Localizando linhas por valores de coluna  
  
#### Para localizar linhas com base nos valores em qualquer coluna  
  
-   Tabelas de dados são criadas com um <xref:System.Data.DataTable.Select%2A> método que retorna uma matriz de <xref:System.Data.DataRow>s com base na expressão passada para o <xref:System.Data.DataTable.Select%2A> método. Para obter mais informações sobre como criar expressões válidas, consulte a seção "Sintaxe de expressões" da página a <xref:System.Data.DataColumn.Expression%2A> propriedade.  
  
     O exemplo a seguir mostra como usar o <xref:System.Data.DataTable.Select%2A> método o <xref:System.Data.DataTable> para localizar linhas específicas.  
  
     [!CODE [VbRaddataEditing#20](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataEditing#20)]  
  
## Acessando registros relacionados  
 Quando tabelas em um dataset estão relacionadas, um <xref:System.Data.DataRelation> objeto pode tornar disponíveis os registros relacionados em outra tabela. Por exemplo, um conjunto de dados que contém `Customers` e `Orders` tabelas podem ser disponibilizadas.  
  
 Você pode usar um <xref:System.Data.DataRelation> objeto para localizar registros relacionados chamando o <xref:System.Data.DataRow.GetChildRows%2A> método de um <xref:System.Data.DataRow> na tabela pai; esse método retorna uma matriz de registros filho relacionados. Ou você pode chamar o <xref:System.Data.DataRow.GetParentRow%2A> método de um <xref:System.Data.DataRow> na tabela filho; esse método retorna uma única <xref:System.Data.DataRow> da tabela pai.  
  
 Esta página de Ajuda fornece exemplos usando datasets tipados. Para obter informações sobre navegar em relações em datasets não tipados, consulte [Navegando em DataRelations](../Topic/Navigating%20DataRelations.md).  
  
> [!NOTE]
>  Se você estiver trabalhando em um aplicativo Windows Forms e usando os recursos de associação de dados para exibir dados, o formulário gerado pelo designer pode fornecer funcionalidade suficiente para seu aplicativo. Para obter mais informações, consulte as páginas no [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md), especificamente [Como exibir dados relacionados em um Aplicativo do Windows Forms](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md) e [Instruções passo a passo: exibindo dados relacionados em um Windows Form](../Topic/Walkthrough:%20Displaying%20Related%20Data%20on%20a%20Windows%20Form.md).  
  
 Os exemplos de código a seguir demonstram navegando para cima e para relações em datasets tipados. Eles use tipado <xref:System.Data.DataRow>s \(`NorthwindDataSet.OrdersRow`\) e gerado `FindBy`*PrimaryKey* \(`FindByCustomerID`\) métodos para localizar uma linha desejada e retornar os registros relacionados. Os exemplos compilam e executam corretamente somente se você tiver:  
  
-   Uma instância de um dataset chamado `NorthwindDataSet` com um `Customers` tabela  
  
-   Um `Orders` tabela  
  
-   Uma relação nomeada `FK_Orders_Customers` relacionando as duas tabelas disponíveis ao escopo do seu código  
  
 Além disso, ambas as tabelas precisam ser preenchidas com dados para quaisquer registros a serem retornados.  
  
#### Para retornar os registros de um registro pai selecionado filho  
  
-   Chamar o <xref:System.Data.DataRow.GetChildRows%2A> método de um determinado `Customers` dados de linha e retornar uma matriz de linhas do `Orders` tabela:  
  
     [!CODE [VbRaddataDatasets#6](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#6)]  
  
#### Para retornar o registro pai de um registro filho selecionado  
  
-   Chamar o <xref:System.Data.DataRow.GetParentRow%2A> método de um determinado `Orders` dados de linha e retornar uma única linha do `Customers` tabela:  
  
     [!CODE [VbRaddataDatasets#7](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#7)]