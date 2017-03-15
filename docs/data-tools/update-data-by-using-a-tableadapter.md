---
title: "Como atualizar dados usando um TableAdapter | Microsoft Docs"
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
  - "dados [Visual Studio], TableAdapters"
  - "dados [Visual Studio], atualizando"
  - "salvando dados"
  - "TableAdapters, atualizando dados"
  - "atualizando dados, TableAdapters"
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Como atualizar dados usando um TableAdapter
Depois que os dados no conjunto de dados foi modificados e validados, você pode enviar os dados atualizados para uma chamada databaseby o `Update` método de um [TableAdapter](../data-tools/tableadapter-overview.md). O `Update` atualizará uma única tabela de dados e executar o comando correto \(INSERT, UPDATE ou DELETE\) com base no método de <xref:System.Data.DataRow.RowState%2A> de cada linha de dados na tabela. Quando um conjunto de dados tiver tabelas relacionadas, o Visual Studio gera uma classe de TableAdapterManager que você deve usar para fazer as atualizações. TableAdapterManager garante que as atualizações são feitas a ordem correta com base nas restrições de chave estrangeira definidas no banco de dados. Quando você usa controles ligados a dados, a arquitetura de vinculação de dados cria uma variável de membro de TableAdapterManager para você, chamado tableAdapterManager. Para obter mais informações, consulte [Visão geral de atualização hierárquica](../Topic/Hierarchical%20Update%20Overview.md).  
  
> [!NOTE]
>  Pois tentar atualizar uma fonte de dados com o conteúdo de um conjunto de dados pode causar erros, você deve colocar o código que chama o adaptador `Update` método dentro um `try`\/`catch` bloco.  
  
 O procedimento exato para atualizar uma fonte de dados pode variar dependendo das necessidades de negócios, mas o aplicativo deve incluir as seguintes etapas:  
  
1.  Chamar o adaptador `Update` método em um `try`\/`catch` bloco.  
  
2.  Se uma exceção é detectada, localize a linha de dados que causou o erro. Para obter mais informações, consulte [Como localizar linhas com erros](../Topic/How%20to:%20Locate%20Rows%20that%20Have%20Errors.md).  
  
3.  Reconcilie o problema nos dados de linha \(programaticamente se você puder, ou apresentando a linha inválida para o usuário para modificação\) e, em seguida, tente novamente a atualização \(<xref:System.Data.DataRow.HasErrors%2A>, <xref:System.Data.DataTable.GetErrors%2A>\).  
  
## Salvando dados em um banco de dados  
 Chamar o `Update` método de um TableAdapter, passando o nome da tabela de dados que contém os valores a serem gravados no banco de dados.  
  
#### Para atualizar um banco de dados usando um TableAdapter  
  
-   Coloque o adaptador `Update` método em um `try`\/`catch` bloco. O exemplo a seguir mostra como tentar uma atualização de dentro um `try`\/`catch` bloco com o conteúdo a `Customers` na tabela `NorthwindDataSet`.  
  
     [!code-cs[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]  
  
## Consulte também  
 [Salvar dados no banco de dados](../data-tools/save-data-back-to-the-database.md)