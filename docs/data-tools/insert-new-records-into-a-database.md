---
title: "Como inserir novos registros em um banco de dados | Microsoft Docs"
ms.custom: ""
ms.date: "10/06/2016"
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
  - "bancos de dados, inserindo novos registros em"
  - "registros, inserindo"
  - "salvando dados"
  - "TableAdapters, inserindo novos registros em"
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Como inserir novos registros em um banco de dados
Para inserir novos registros em um banco de dados, você pode usar o `TableAdapter.Update` método ou um dos métodos DBDirect do TableAdapter \(especificamente o `TableAdapter.Insert` método\). Para obter mais informações, consulte [Visão geral de TableAdapter](../data-tools/tableadapter-overview.md).  
  
 Se seu aplicativo não usar TableAdapters, você pode usar objetos command para interagir e inserir novos registros no banco de dados \(por exemplo, <xref:System.Data.SqlClient.SqlCommand>\).  
  
 Use o `TableAdapter.Update` método quando seu aplicativo usa conjuntos de dados para armazenar dados. O `Update` método envia todas as alterações \(atualizações, inserções e exclusões\) para o banco de dados.  
  
 Use o `TableAdapter.Insert` método quando seu aplicativo usa objetos para armazenar dados, ou quando quiser um controle mais preciso sobre a criação de novos registros no banco de dados.  
  
 Se seu TableAdapter não tem um `Insert` método, significa que ou o TableAdapter está configurado para usar procedimentos armazenados ou seus `GenerateDBDirectMethods` está definida como `false`. Tente definir o TableAdapter `GenerateDBDirectMethods` propriedade `true` de dentro de [Dataset Designer](../data-tools/creating-and-editing-typed-datasets.md) e, em seguida, salve o dataset para regenerar o TableAdapter. Se o TableAdapter ainda não tem um `Insert` método, então a tabela provavelmente não fornece informações de esquema suficientes para distinguir entre linhas individuais \(por exemplo, nenhuma chave primária é definida na tabela\).  
  
## Inserir novos registros usando TableAdapters  
 TableAdapters fornecem maneiras diferentes para inserir novos registros em um banco de dados, dependendo dos requisitos do seu aplicativo.  
  
 Se seu aplicativo usa conjuntos de dados para armazenar dados, você pode simplesmente adicionar novos registros para o estado desejado <xref:System.Data.DataTable> no conjunto de dados e, em seguida, chame o `TableAdapter.Update` método. O `TableAdapter.Update` método obtém as alterações na <xref:System.Data.DataTable> e envia essas alterações ao banco de dados \(incluindo registros excluídos e modificados\).  
  
#### Para inserir novos registros em um banco de dados usando o método TableAdapter.  
  
1.  Adicionar novos registros para o estado desejado <xref:System.Data.DataTable> Criando um novo <xref:System.Data.DataRow> e adicioná\-lo para o <xref:System.Data.DataTable.Rows%2A> coleção. Para obter mais informações, consulte [Como adicionar linhas a um DataTable](../Topic/How%20to:%20Add%20Rows%20to%20a%20DataTable.md).  
  
2.  Após as novas linhas serem adicionadas à <xref:System.Data.DataTable>, chamar o `TableAdapter.Update` método. Você pode controlar a quantidade de dados para atualizar passando um inteiro <xref:System.Data.DataSet>, um <xref:System.Data.DataTable>, uma matriz de <xref:System.Data.DataRow>s ou um único <xref:System.Data.DataRow>.  
  
     O código a seguir mostra como adicionar um novo registro para um <xref:System.Data.DataTable> e, em seguida, chamar o `TableAdapter.Update` método para salvar a nova linha no banco de dados. \(Este exemplo usa o banco de dados Northwind `Region` tabela.\)  
  
     [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
     [!code-cs[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]  
  
 Se seu aplicativo usa objetos para armazenar os dados em seu aplicativo, você pode usar o `TableAdapter.Insert` método para criar novas linhas diretamente no banco de dados. O `Insert` método aceita os valores individuais para cada coluna como parâmetros. Chamar o método insere um novo registro no banco de dados com os valores de parâmetro passados.  
  
 O procedimento a seguir usa o banco de dados Northwind `Region` tabela como um exemplo.  
  
#### Para inserir novos registros em um banco de dados usando o método TableAdapter.  
  
-   Chamar o TableAdapter `Insert` método, passando os valores para cada coluna como parâmetros.  
  
    > [!NOTE]
    >  Se você não tiver uma instância disponível, crie uma instância do TableAdapter que você deseja usar.  
  
     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
     [!code-cs[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]  
  
## Inserir novos registros usando objetos de comando  
 O exemplo a seguir insere novos registros diretamente em um banco de dados usando objetos de comando. Para obter mais informações sobre como usar objetos de comando para executar comandos e procedimentos armazenados, consulte [Buscando dados no aplicativo](../data-tools/fetching-data-into-your-application.md).  
  
 O procedimento a seguir usa o banco de dados Northwind `Region` tabela como um exemplo.  
  
#### Para inserir novos registros em um banco de dados usando objetos de comando  
  
-   Criar um novo objeto de comando, defina sua `Connection`, `CommandType`, e `CommandText` Propriedades.  
  
     [!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
     [!code-cs[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]  
  
## Segurança do .NET Framework  
 Você deve ter acesso ao banco de dados que você está tentando se conectar, bem como permissão para executar inserções na tabela desejada.  
  
## Consulte também  
 [Salvar dados no banco de dados](../data-tools/save-data-back-to-the-database.md)