---
title: "Instru&#231;&#245;es passo a passo: criando um conjunto de dados com o Designer de Conjunto de Dados | Microsoft Docs"
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
  - "conjuntos de dados [Visual Basic], instruções passo a passo"
  - "Esquemas XML, criando conjuntos de dados"
  - "dados [Visual Studio] Dataset Designer"
  - "Designer de conjunto de dados, instruções passo a passo"
  - "conjuntos de dados [Visual Basic], criando"
ms.assetid: 12360f54-db6c-45d2-a91f-fee43214b555
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Instru&#231;&#245;es passo a passo: criando um conjunto de dados com o Designer de Conjunto de Dados
Neste passo a passo, você irá criar um conjunto de dados usando o **Dataset Designer**. Ele o guiará pelo processo de criação de um novo projeto e adicionar um novo **DataSet** item a ele. Você aprenderá como criar tabelas com base em tabelas em um banco de dados sem usar um assistente.  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
-   Criando um novo **Windows Application** projeto.  
  
-   Adicionando um vazio **DataSet** item ao projeto.  
  
-   Criando e configurando uma fonte de dados em seu aplicativo, criando um dataset com o **Dataset Designer**.  
  
-   Criar uma conexão com o banco de dados Northwind **Server Explorer**.  
  
-   Criar tabelas com TableAdapters no conjunto de dados com base em tabelas no banco de dados.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Pré-requisitos  
 Para concluir este passo a passo, você precisa:  
  
-   Acesso a dados de exemplo Northwind \(versão do SQL Server ou Access\). Para obter mais informações, consulte [Como instalar bancos de dados de exemplo](../data-tools/how-to-install-sample-databases.md).  
  
## Criar um novo projeto de aplicativo do Windows  
  
#### Para criar um novo projeto de aplicativo do Windows  
  
1.  Do **arquivo** menu, crie um novo projeto.  
  
2.  Escolha uma linguagem de programação a **tipos de projeto** painel.  
  
3.  Clique em **Windows Application** no **modelos** painel.  
  
4.  Nomeie o projeto `DatasetDesignerWalkthrough`, e, em seguida, clique em **OK**.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Adicionar o projeto **Solution Explorer** e exibirá um novo formulário no designer.  
  
## Adicionando um novo Dataset ao aplicativo  
  
#### Para adicionar um novo item dataset ao projeto  
  
1.  Sobre o **projeto** menu, clique em **Add New Item**.  
  
     O **Add New Item** caixa de diálogo é exibida.  
  
2.  No **modelos** caixa do **Add New Item** caixa de diálogo, clique em **DataSet**.  
  
3.  Nome do conjunto de dados `NorthwindDataset`, e, em seguida, clique em **Add**.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Adicionar um arquivo chamado **NorthwindDataSet** ao projeto e abri\-lo no **Dataset Designer**.  
  
## Criar uma conexão de dados no Server Explorer  
  
#### Para criar uma conexão ao banco de dados Northwind  
  
1.  Sobre o **exibição** menu, clique em **Server Explorer**.  
  
2.  Em **Server Explorer**, clique o **conectar\-se ao banco de dados** botão.  
  
3.  Crie uma conexão com o banco de dados de exemplo Northwind.  
  
    > [!NOTE]
    >  Você pode se conectar à versão SQL Server ou Access do Northwind para este passo a passo.  
  
## Criando tabelas no Dataset  
 Esta seção explicará como adicionar tabelas ao conjunto de dados.  
  
#### Para criar a tabela de clientes  
  
1.  Expanda a conexão de dados que você criou no **Server Explorer**, e, em seguida, expanda o **tabelas** nó.  
  
2.  Arraste o **clientes** tabela **Server Explorer** para o **Dataset Designer**.  
  
     Um **clientes** tabela de dados e **CustomersTableAdapter** são adicionados ao conjunto de dados.  
  
#### Para criar a tabela de pedidos  
  
-   Arraste o **pedidos** tabela **Server Explorer** para o **Dataset Designer**.  
  
     Um **pedidos** tabela de dados, **OrdersTableAdapter**, e a relação de dados entre o **clientes** e **pedidos** tabelas são adicionadas ao conjunto de dados.  
  
#### Para criar a tabela OrderDetails  
  
-   Arraste o **detalhes do pedido** tabela **Server Explorer** para o **Dataset Designer**.  
  
     Um **Order Details** tabela de dados, **Order DetailsTableAdapter**, e a relação de dados entre o **pedidos** e **Order Details** tabelas são adicionadas ao conjunto de dados.  
  
## Próximas etapas  
  
### Para adicionar funcionalidade ao seu aplicativo  
  
-   Salve o conjunto de dados.  
  
-   Selecione itens de **fontes de dados** janela e arrastá\-los para um formulário. Para obter mais informações, consulte [Associar controles dos Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
-   Adicione mais consultas aos TableAdapters. Para obter mais informações, consulte [Como criar consultas TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  
  
-   Adicionar lógica de validação de <xref:System.Data.DataTable.ColumnChanging> ou <xref:System.Data.DataTable.RowChanging> eventos das tabelas de dados no conjunto de dados. Para obter mais informações, consulte [Validar dados em conjuntos de dados](../data-tools/validate-data-in-datasets.md).  
  
## Consulte também  
 [Instruções passo a passo de dados](../Topic/Data%20Walkthroughs.md)   
 [Associar controles dos Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Conectando a dados no Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparando o aplicativo para receber dados](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscando dados no aplicativo](../data-tools/fetching-data-into-your-application.md)   
 [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Editando dados no aplicativo](../data-tools/editing-data-in-your-application.md)   
 [Validando dados](../Topic/Validating%20Data.md)   
 [Salvando dados](../data-tools/saving-data.md)