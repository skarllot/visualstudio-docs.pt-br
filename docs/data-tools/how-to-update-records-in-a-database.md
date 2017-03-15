---
title: "Como atualizar registros em um banco de dados | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "dados [Visual Studio], salvar"
  - "bancos de dados, atualizando"
  - "registros, edição"
  - "registros, atualizando"
  - "Método TableAdapter.Update"
ms.assetid: cdc8a8e4-a5fa-40dd-9221-97b8571d802a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Como atualizar registros em um banco de dados
Você pode usar o método `TableAdapter.Update` para atualizar \(editar\) registros em um banco de dados.  O `TableAdapter.Update` método fornece várias sobrecargas que realizam operações diferentes, dependendo dos parâmetros passados.  É importante entender os resultados da chamada essas assinaturas de método diferente.  
  
> [!NOTE]
>  Se seu aplicativo não usa TableAdapters, então você pode usar objetos de comando para atualizar registros em seu banco de dados \(por exemplo, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>\).  Para obter mais informações sobre a atualização de dados com objetos de comando, consulte "Atualizar registros usando objetos de comando" abaixo.  
  
 A tabela a seguir descreve o comportamento dos diversos métodos `TableAdapter.Update`:  
  
|Método|Descrição|  
|------------|---------------|  
|`TableAdapter.Update(DataTable)`|Tenta salvar todas as alterações em <xref:System.Data.DataTable> ao banco de dados.  \(Isso inclui remover quaisquer linhas excluídas da tabela, adicionar linhas inseridas na tabela e atualizar quaisquer linhas na tabela que foram alteradas.\)|  
|`TableAdapter.Update(DataSet)`|Embora o parâmetro leve um dataset, o TableAdapter tenta salvar todas as alterações na <xref:System.Data.DataTable> associada do TableAdapter para o banco de dados.  \(Isso inclui remover quaisquer linhas excluídas da tabela, adicionar linhas inseridas na tabela e atualizar quaisquer linhas na tabela que foram alteradas.\) **Note:**  A <xref:System.Data.DataTable> associada de um TableAdapter é a <xref:System.Data.DataTable> criada quando o TableAdapter foi originalmente configurado.|  
|`TableAdapter.Update(DataRow)`|Tenta salvar alterações na <xref:System.Data.DataRow> indicada para o banco de dados.|  
|`TableAdapter.Update(DataRows())`|Tenta salvar as alterações em qualquer linha na matriz de <xref:System.Data.DataRow>s para o banco de dados.|  
|`TableAdapter.Update("new column values", "original column values")`|Tenta salvar as alterações em uma única linha que é identificada pelos valores da coluna original.|  
  
 Você normalmente usa o método `TableAdapter.Update` que recebe um <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, ou <xref:System.Data.DataRow>\(s\) quando seu aplicativo usa conjuntos de dados exclusivamente para armazenar dados.  
  
 Normalmente você utiliza o método `TableAdapter.Update` que recebe valores de coluna quando seu aplicativo usa objetos para armazenar dados.  
  
 Se seu TableAdapter não tem um método `Update` que recebe valores de coluna, significa que ou o TableAdapter está configurado para usar procedimentos armazenados ou sua propriedade `GenerateDBDirectMethods` está definida como `false`.  Try setting the TableAdapter's `GenerateDBDirectMethods` property to `true` from within the [Dataset Designer](../data-tools/creating-and-editing-typed-datasets.md) and then save the dataset to regenerate the TableAdapter.  Se o TableAdapter ainda não tem um método `Update` que recebe valores de coluna, então a tabela provavelmente não fornece informações de esquema suficientes para distinguir entre linhas individuais \(por exemplo, nenhuma chave primária está definida na tabela\).  
  
## Atualizar registros existentes usando TableAdapters  
 TableAdapters fornecem maneiras diferentes para atualizar registros em um banco dados dependendo dos requisitos do seu aplicativo.  
  
 Se seu aplicativo utiliza datasets para armazenar dados, você pode simplesmente atualizar os registros em que o desejado <xref:System.Data.DataTable> e, em seguida, chame o `TableAdapter.Update` método e passar de uma a <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, ou matriz de <xref:System.Data.DataRow>s.  A tabela acima descreve os diferentes `Update` métodos.  
  
#### Para atualizar registros em um banco de dados com o método TableAdapter.Update que recebe DataSet, DataTable, DataRow ou DataRows\(\)  
  
1.  Editar registros na <xref:System.Data.DataTable> desejada editando diretamente o <xref:System.Data.DataRow> na <xref:System.Data.DataTable>.  Para obter mais informações, consulte [Como editar linhas em um DataTable](../Topic/How%20to:%20Edit%20Rows%20in%20a%20DataTable.md).  
  
2.  Após as linhas serem editadas na <xref:System.Data.DataTable>, chame o método `TableAdapter.Update`.  You can control the amount of data to update by passing in either an entire <xref:System.Data.DataSet>, a <xref:System.Data.DataTable>, an array of <xref:System.Data.DataRow>s, or a single <xref:System.Data.DataRow>.  
  
     O código a seguir mostra como editar um registro em um <xref:System.Data.DataTable> e, em seguida, chamar o método `TableAdapter.Update` para salvar as alterações para o banco de dados.  \(Este exemplo usa a tabela Region do banco de dados Northwind.\)  
  
     [!code-vb[VbRaddataSaving#17](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_1.vb)]
     [!code-cs[VbRaddataSaving#17](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_1.cs)]  
  
 Se seu aplicativo usa objetos para armazenar os dados em seu aplicativo, você pode utilizar os métodos`DBDirect` do TableAdapter para enviar dados de seus objetos diretamente para o banco de dados.  Esses métodos permitem que você passe valores individuais para cada coluna como parâmetros de método.  Chamar esse método atualiza um registro existente no banco de dados com os valores de coluna passados para o método.  
  
 O procedimento a seguir usa a tabela `Region` do banco de dados Northwind como um exemplo.  
  
#### Para atualizar registros em um banco de dados usando o método TableAdapter.Update que recebe valores de coluna  
  
-   Chame o método `Update` do TableAdapter, passando os valores novos e originais para cada coluna como parâmetros.  
  
    > [!NOTE]
    >  Se você não tiver uma instância disponível, crie a instância no TableAdapter que você deseja usar.  
  
     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_2.vb)]
     [!code-cs[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_2.cs)]  
  
## Atualizar Registros Usando Objetos de Comando  
 O exemplo a seguir atualiza registros existentes diretamente em um banco de dados usando objetos de comando.  For more information on using command objects to execute commands and stored procedures, see [Buscando dados no aplicativo](../data-tools/fetching-data-into-your-application.md).  
  
 O procedimento a seguir usa a tabela `Region` do banco de dados Northwind como um exemplo.  
  
#### Para atualizar registros existentes em um banco de dados usando objetos de comando  
  
-   Crie um novo objeto de comando; defina suas propriedades `Connection`, `CommandType` e `CommandText`; em seguida, abra uma conexão e execute o comando.  
  
     [!code-vb[VbRaddataSaving#19](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_3.vb)]
     [!code-cs[VbRaddataSaving#19](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_3.cs)]  
  
## Segurança do .NET Framework  
 Você deve ter acesso ao banco de dados ao qual você está tentando se conectar, bem como permissão para atualizar registros na tabela desejada.  
  
## Consulte também  
 [Visão geral de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Como excluir registros em um banco de dados](../Topic/How%20to:%20Delete%20Records%20in%20a%20Database.md)   
 [Como inserir novos registros em um banco de dados](../data-tools/insert-new-records-into-a-database.md)   
 [Como salvar dados de um objeto em um banco de dados](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Visão geral de aplicativos de dados no Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Conectando a dados no Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparando o aplicativo para receber dados](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscando dados no aplicativo](../data-tools/fetching-data-into-your-application.md)   
 [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Editando dados no aplicativo](../data-tools/editing-data-in-your-application.md)   
 [Validando dados](../Topic/Validating%20Data.md)   
 [Salvando dados](../data-tools/saving-data.md)