---
title: "Como criar e executar uma instru&#231;&#227;o SQL que retorna um &#250;nico valor | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "leitor de dados"
  - "valores escalares"
  - "procedimentos armazenados, retornando um único valor"
  - "Instruções SQL, comandos de dados"
  - "Objeto DataReader"
  - "comandos de dados, retornando valores escalares"
ms.assetid: eb366496-69e5-4462-8683-653054165c5c
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Como criar e executar uma instru&#231;&#227;o SQL que retorna um &#250;nico valor
Para executar uma instrução SQL que retorna um único valor, você pode executar uma consulta TableAdapter que esteja configurada para executar uma instrução SQL \(por exemplo, `CustomersTableAdapter.CustomerCount()`\).  
  
 Se seu aplicativo não usar TableAdapters, chame o `ExecuteScalar` método em um objeto de comando, defina sua `CommandType` propriedade <xref:System.Data.CommandType>. \("Objeto command" se refere ao comando específico para o [.NET Framework Data Provider](../Topic/.NET%20Framework%20Data%20Providers.md) seu aplicativo está usando. Por exemplo, se seu aplicativo estiver usando o .NET Framework Data Provider para SQL Server, o objeto de comando seria <xref:System.Data.SqlClient.SqlCommand>.\)  
  
 Os exemplos a seguir mostram como executar instruções SQL que retornem valores únicos de um banco de dados usando o TableAdapters ou objetos de comando. Para obter mais informações sobre como consultar com TableAdapters e comandos, consulte [Preencher datasets usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Executar instruções SQL que retornam valores únicos usando um TableAdapter  
 Este exemplo mostra como criar uma consulta TableAdapter usando o [Editando TableAdapters](../data-tools/editing-tableadapters.md), e, em seguida, ele fornece informações sobre como declarar uma instância do TableAdapter e executar a consulta.  
  
#### Para criar uma instrução SQL que retornam um único valor usando um TableAdapter  
  
1.  Abra um conjunto de dados de **Dataset Designer**. Para obter mais informações, consulte [Como abrir um conjunto de dados no Designer de Conjunto de Dados](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Se você não tiver um, crie um TableAdapter. Para obter mais informações sobre como criar TableAdapters, consulte [Criar e configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Se você já tiver uma consulta no seu TableAdapter que usa uma instrução SQL para retornar um único valor, então vá para o próximo procedimento, "para"declarar uma instância do TableAdapter e executar a consulta. Caso contrário, continue na etapa 4 para criar uma nova consulta que retorna um único valor.  
  
4.  Clique com botão direito no TableAdapter que você deseja e use o menu de atalho para adicionar uma consulta.  
  
     O **Assistente de configuração de consulta do TableAdapter** é aberto.  
  
5.  Deixe o valor padrão de **usar instruções SQL**, e, em seguida, clique em **próximo**.  
  
6.  Escolha o **SELECT que retorna um único valor** opção e, em seguida, clique em **próximo**.  
  
7.  Digite sua instrução SQL, ou use o **Query Builder** para auxiliar na criação de uma e, em seguida, clique em **próximo**.  
  
8.  Forneça um nome para a consulta.  
  
9. Conclua o Assistente; a consulta é adicionada ao TableAdapter.  
  
10. Compile o projeto.  
  
#### Para declarar uma instância do TableAdapter e executar a consulta  
  
1.  Declare uma instância do TableAdapter que contém a consulta que você deseja executar.  
  
    -   Para criar uma instância usando ferramentas em tempo de design, arraste o TableAdapter que deseja o **Toolbox**. \(Os componentes no seu projeto agora aparecem no **Toolbox** sob um título que coincide com o nome do projeto.\) Se o TableAdapter não aparecer no **Toolbox**, em seguida, você talvez precise criar seu projeto.  
  
         \- ou \-  
  
    -   Para criar uma instância no código, substitua o código a seguir com os nomes de seu <xref:System.Data.DataSet> e TableAdapter.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  TableAdapters não são realmente localizados dentro de suas classes dataset associadas. Cada conjunto de dados tem uma coleção correspondente de TableAdapters em seu próprio namespace. Por exemplo, se você tiver um dataset chamado `SalesDataSet`, em seguida, deve haver um `SalesDataSetTableAdapters` namespace que contém seus TableAdapters.  
  
2.  Chame sua consulta como você chamaria qualquer outro método no código. Sua consulta é um método no TableAdapter. Substitua o código a seguir com os nomes de seu TableAdapter e de consulta. Você também precisa passar quaisquer parâmetros necessários para sua consulta e fazer algo com o valor de retorno \(por exemplo, atribuí\-la a uma variável\). Se você não tiver certeza se sua consulta requer parâmetros, ou que parâmetros requer, então, verifique o IntelliSense para a assinatura necessária da consulta. Dependendo se sua consulta usa parâmetros ou não, o código seria semelhante a um dos exemplos a seguir:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
3.  Você provavelmente precisará atribuir o valor retornado pela consulta a uma variável. Consultas TableAdapter que retornam um único valor retornam um tipo de dados com base na consulta \(em oposição ao `ExecuteScalar` método, que retorna um objeto\). Por exemplo, se sua consulta TableAdapter seleciona uma única coluna cujo tipo de dados é um inteiro, o valor de retorno da consulta é um inteiro. Se a coluna permitir valores nulos, o valor de retorno é um dos tipos anuláveis \(por exemplo, `Nullable(Of Integer)`\). Para obter mais informações sobre tipos anuláveis, consulte <xref:System.Nullable>. O código completo para declarar uma instância de um TableAdapter e executar uma consulta deve ser semelhante ao seguinte \(Este exemplo pressupõe que o retorno do valor é um inteiro; ajuste seu código de acordo com o tipo de dados retornado pela consulta\):  
  
     [!code-cs[VbRaddataFillingAndExecuting#9](../data-tools/codesnippet/CSharp/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#9](../data-tools/codesnippet/VisualBasic/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value_1.vb)]  
  
## Executar instruções SQL que retornam valores únicos usando um objeto de comando  
 O exemplo a seguir mostra como criar um comando e executar uma instrução SQL que retorna um único valor. Para obter informações sobre como definir e obter valores de parâmetro para um comando, consulte [Como definir e obter parâmetros para objetos de comando](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md).  
  
 Este exemplo usa o <xref:System.Data.SqlClient.SqlCommand> do objeto e requer:  
  
-   Referências a <xref:System>, <xref:System.Data>, e <xref:System.Xml> namespaces.  
  
-   Uma conexão de dados denominada `SqlConnection1`.  
  
-   Uma tabela chamada `Customers` na fonte de dados que `SqlConnection1` conecta\-se a. \(Caso contrário, será necessário uma instrução SQL válida para sua fonte de dados\).  
  
#### Para executar uma instrução SQL que retornam um único valor usando um DataCommand  
  
-   Adicione o seguinte código para um método que você deseja executar o código. Retorna um único valor chamando o `ExecuteScalar` método de um comando \(por exemplo, <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>\). Os dados são retornados em um <xref:System.Object>.  
  
     [!code-cs[VbRaddataFillingAndExecuting#10](../data-tools/codesnippet/CSharp/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#10](../data-tools/codesnippet/VisualBasic/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value_2.vb)]  
  
## Segurança do .NET Framework  
 O aplicativo requer permissão para acessar o banco de dados e executar a instrução SQL.  
  
## Consulte também  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteScalar%2A?displayProperty=fullName>   
 [Como criar consultas TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Como editar consultas TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Como: preencher um dataset com dados](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [Preencher datasets usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Como definir e obter parâmetros para objetos de comando](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)