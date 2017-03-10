---
title: "Como executar um procedimento armazenado que retorna um &#250;nico valor | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CommandType.StoredProcedure"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "exemplo de método ExecuteReader [Visual Basic]"
  - "procedimentos armazenados, exemplos"
  - "procedimentos armazenados, executando"
ms.assetid: ecf8c262-58ca-4a69-a82c-916c0c061422
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Como executar um procedimento armazenado que retorna um &#250;nico valor
To execute a stored procedure that returns a single value, you can run TableAdapter query that is configured to run a stored procedure \(for example, `CustomersTableAdapter.CustomerCount()`\).  
  
 Se seu aplicativo não usa TableAdapters, chame o método `ExecuteScalar` em um objeto de comando, definindo sua propriedade `CommandType` como <xref:System.Data.CommandType>.  \("Objeto de comando" refere\-se ao comando específico para o [.NET Framework Data Provider](../Topic/.NET%20Framework%20Data%20Providers.md) que seu aplicativo está usando.  Por exemplo, se seu aplicativo estiver usando provedor de dados do .NET Framework para SQL Server, o objeto de comando seria <xref:System.Data.SqlClient.SqlCommand>.\)  
  
 Os exemplos a seguir mostram como executar procedimentos armazenados que retornem valores únicos de um banco de dados usando o TableAdapters ou os objetos Command.  Para obter mais informações sobre como consultar com TableAdapters e comandos, consulte [Preencher datasets usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Executando procedimentos armazenados que retornam valores únicos usando um TableAdapter  
 Este exemplo mostra como criar uma consulta TableAdapter usando o [Editando TableAdapters](../data-tools/editing-tableadapters.md), e em seguida, ele fornece informações sobre como declarar uma instância do TableAdapter e executar a consulta.  
  
#### Para executar um procedimento armazenado que retorna um valor único usando um TableAdapter  
  
1.  Abra um dataset no **Dataset Designer**.  Para obter mais informações, consulte [Como abrir um conjunto de dados no Designer de Conjunto de Dados](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Se você não tiver um, crie um TableAdapter.  Para obter mais informações sobre como criar TableAdapters, consulte [Criar e configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Se você tiver uma consulta no seu TableAdapter que usa um procedimento armazenado para retornar um único valor, vá para o procedimento seguinte, &quot;Para declarar uma instância do TableAdapter e executar a consulta&quot;. Caso contrário, prossiga com a etapa 4 para criar uma nova consulta que retorna um único valor.  
  
4.  Clique com o botão direito do mouse no TableAdapter que você deseja, e use o menu de atalho para adicionar uma consulta.  
  
     O **TableAdapter Query Configuration Wizard** abre.  
  
5.  Selecione **Use existing stored procedure**, e clique em **Next**.  
  
6.  Selecione um procedimento armazenado na lista suspensa, e clique em **Next**.  
  
7.  Selecione a opção para retornar **A single value**, e clique em **Next**.  
  
8.  Forneça um nome para a consulta.  
  
9. Clique em **Next** ou **Finish** para concluir o assistente; a consulta é adicionada ao TableAdapter.  
  
10. Crie o seu projeto.  
  
#### Para declarar uma instância do TableAdapter e executar a consulta  
  
1.  Declare uma instância do TableAdapter que contém a consulta que você deseja executar.  
  
    -   Para criar uma instância usando ferramentas em tempo de design, arraste o TableAdapter que você deseja a partir da **Toolbox**.  \(Os componentes no seu projeto agora aparecem no **Toolbox** sob um título que coincide com o nome do projeto.\) Se o TableAdapter não aparecer no **Toolbox**, então você talvez precise criar seu projeto.  
  
         \- ou \-  
  
    -   Para criar uma instância no código, substitua o código a seguir pelos nomes de seu <xref:System.Data.DataSet> e TableAdapter.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  Na verdade os TableAdapters não estão localizados dentro de suas classes dataset associadas.  Cada dataset tem uma coleção correspondente de TableAdapters no seu próprio namespace.  Por exemplo, se você tiver um dataset chamado `SalesDataSet`, então haveria um namespace `SalesDataSetTableAdapters` contendo seus TableAdapters.  
  
2.  Chame sua consulta como você chamaria qualquer outro método no código.  Sua consulta é um método no TableAdapter.  Substitua o código a seguir pelos nomes de seu TableAdapter e de sua consulta.  Também será necessário passar quaisquer parâmetros necessários para sua consulta.  Se você não tiver certeza se sua consulta requer parâmetros, ou que parâmetros requer, então, verifique o IntelliSense para a assinatura necessária da consulta.  Dependendo se sua consulta usa parâmetros ou não, o código seria de aparência semelhante a um dos exemplos a seguir:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     O código completo para declarar uma instância do TableAdapter e executar a consulta deve ser semelhante ao seguinte:  
  
     [!code-cs[VbRaddataFillingAndExecuting#9](../data-tools/codesnippet/CSharp/how-to-execute-a-stored-procedure-that-returns-a-single-value_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#9](../data-tools/codesnippet/VisualBasic/how-to-execute-a-stored-procedure-that-returns-a-single-value_1.vb)]  
  
## Executar procedimentos armazenados que retornam valores únicos usando um objeto Command  
 O exemplo a seguir mostra como criar um comando e executar um procedimento armazenado que retorna um único valor.  Para obter informações sobre configurar e obter valores de parâmetro para um comando, consulte [Como definir e obter parâmetros para objetos de comando](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md).  
  
 Este exemplo usa o objeto <xref:System.Data.SqlClient.SqlCommand> e requer:  
  
-   Referências aos namespaces <xref:System>, <xref:System.Data> e <xref:System.Xml>.  
  
-   Uma conexão de dados denominada `SqlConnection1`.  
  
-   Uma tabela denominada `Customers` na fonte de dados à qual `SqlConnection1` se conecta.  \(Caso contrário, você precisa de uma instrução SQL válida para sua fonte de dados\).  
  
#### Para executar um procedimento armazenado que retorna um valor único usando um DataCommand  
  
-   Adicione o seguinte código para um método a partir do código que você deseja executar.  You return single values by calling the `ExecuteScalar` method of a command \(for example, <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>\).  The data is returned in an `object`.  
  
     [!code-cs[VbRaddataFillingAndExecuting#14](../data-tools/codesnippet/CSharp/how-to-execute-a-stored-procedure-that-returns-a-single-value_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#14](../data-tools/codesnippet/VisualBasic/how-to-execute-a-stored-procedure-that-returns-a-single-value_2.vb)]  
  
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