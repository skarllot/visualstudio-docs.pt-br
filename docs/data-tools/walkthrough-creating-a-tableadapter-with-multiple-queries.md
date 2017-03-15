---
title: "Instru&#231;&#245;es passo a passo: criando um TableAdapter com v&#225;rias consultas | Microsoft Docs"
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
  - "dados [Visual Studio], TableAdapters"
  - "dados [Visual Studio], explicações passo a passo"
  - "consultas [Visual Studio], TableAdapters"
  - "consultas TableAdapter, criando"
  - "TableAdapters, criando"
ms.assetid: f784dc4d-d514-4ade-8226-f8271c5b1ed8
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Instru&#231;&#245;es passo a passo: criando um TableAdapter com v&#225;rias consultas
Neste passo a passo, você criará um TableAdapter em um conjunto de dados usando o [Assistente para Configuração da Fonte de Dados](../data-tools/media/data-source-configuration-wizard.png).  O passo a passo o conduz pelo processo de criação de uma segunda consulta no [TableAdapter](../data-tools/tableadapter-overview.md) usando o [Editando TableAdapters](../data-tools/editing-tableadapters.md) dentro do [Designer do Conjunto de Dados](../data-tools/creating-and-editing-typed-datasets.md).  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
-   Criando um novo projeto de **Aplicativo do Windows**.  
  
-   Criando e configurando uma fonte de dados em seu aplicativo pela compilação de um conjunto de dados com o **Assistente de Configuração de Fonte de Dados**.  
  
-   Abrindo o novo conjunto de dados no **Designer de Conjunto de Dados**.  
  
-   Adicionando consultas ao TableAdapter com o **Assistente de Configuração de Consulta do TableAdapter**.  
  
## Pré-requisitos  
 Para concluir este passo a passo, você precisará de:  
  
-   Acesso ao banco de dados de exemplo Northwind \(versão SQL Server ou Access\).  Para obter mais informações, consulte [Como instalar bancos de dados de exemplo](../data-tools/how-to-install-sample-databases.md).  
  
## Criando um novo Aplicativo do Windows  
 A primeira etapa é criar um aplicativo do Windows.  
  
#### Para criar um novo projeto de Aplicativo do Windows  
  
1.  No [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], no menu **Arquivo**, crie um novo projeto.  
  
2.  Escolha uma linguagem de programação no painel **Tipos de Projetos**.  
  
3.  Clique em **Aplicativo do Windows** no painel **Modelos**.  
  
4.  Nomeie o projeto como `TableAdapterQueriesWalkthrough` e clique em **OK**.  
  
     O Visual Studio adiciona o projeto ao **Gerenciador de Soluções** e exibe um novo formulário no designer.  
  
## Criando uma fonte de dados do banco de dados com um TableAdapter  
 Esta etapa cria uma fonte de dados usando o **Assistente de Configuração de Fonte de Dados** com base na tabela `Customers` no banco de dados de exemplo Northwind.  É preciso ter acesso ao banco de dados de exemplo Northwind para criar a conexão.  Para obter informações sobre como configurar o banco de dados de exemplo Northwind, consulte [Como instalar bancos de dados de exemplo](../data-tools/how-to-install-sample-databases.md).  
  
#### Para criar a fonte de dados  
  
1.  No menu **Dados**, clique em **Mostrar Fontes de Dados**.  
  
2.  Na janela **Fontes de Dados**, selecione **Adicionar Nova Fonte de Dados** para iniciar o **Assistente de Configuração de Fonte de Dados**.  
  
3.  Selecione **Base de dados** na página **Escolher um Tipo de Fonte de Dados** e, em seguida, clique em **Próximo**.  
  
4.  Na página **Escolha a Conexão de Dados**, faça o seguinte:  
  
    -   Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione\-o.  
  
         \-ou\-  
  
    -   Selecione **Nova Conexão** para iniciar a caixa **Adicionar\/Modificar Conexão**.  
  
5.  Se o banco de dados exigir uma senha, selecione a opção para incluir dados confidenciais e, em seguida, clique em **Próximo**.  
  
6.  Clique em **Avançar** na página **Salvar cadeia de caracteres de conexão no arquivo de configuração do aplicativo**.  
  
7.  Expanda o nó **Tabelas** na página **Escolher Objetos do Banco de Dados**.  
  
8.  Selecione a tabela **Clientes** e clique em **Concluir**.  
  
     O **NorthwindDataSet** é adicionado ao projeto e a tabela **Clientes** aparece na janela **Fontes de Dados**.  
  
## Abrindo o conjunto de dados no Designer de Conjunto de Dados  
  
#### Para abrir o conjunto de dados no Designer de Conjunto de Dados  
  
1.  Clique com o botão direito do mouse em **NorthwindDataset** na janela **Fontes de Dados**.  
  
2.  No menu de atalho, escolha **Editar DataSet com Designer**.  
  
     O NorthwindDataset é aberto no **Designer de Conjunto de Dados**.  
  
## Adicionando uma segunda consulta ao CustomersTableAdapter  
 O assistente criou o conjunto de dados com uma tabela de dados **Clientes** e o **CustomersTableAdapter**.  Esta seção do passo a passo adiciona uma segunda consulta ao **CustomersTableAdapter**.  
  
#### Para adicionar uma consulta ao CustomersTableAdapter  
  
1.  Arraste uma **Consulta** da guia **DataSet** da **Caixa de Ferramentas** para a tabela **Clientes**.  
  
     O [Editando TableAdapters](../data-tools/editing-tableadapters.md) será aberto.  
  
2.  Selecione **Usar instruções SQL** e clique em **Próximo**.  
  
3.  Selecione **SELECT que retorna linhas** e clique em **Próximo**.  
  
4.  Adicione uma cláusula WHERE à consulta para que se leia:  
  
    ```  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax   
    FROM Customers   
    WHERE City = @City  
    ```  
  
    > [!NOTE]
    >  Se você estiver usando a versão Access do Northwind, substitua o parâmetro @City por um ponto de interrogação.  \(`SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE City = ?`\)  
  
5.  Na página **Escolher Métodos a Serem Gerados**, nomeie o método **Preencher uma DataTable** como `FillByCity`.  
  
    > [!NOTE]
    >  O método para **Retornar uma DataTable** não é usado neste passo a passo, portanto, você pode desmarcar a caixa de seleção ou manter o nome padrão.  
  
6.  Clique em **Próximo** e conclua o assistente.  
  
     A consulta **FillByCity** é adicionada ao **CustomersTableAdapter**.  
  
## Adicionando código para executar a consulta adicional ao formulário  
  
#### Para executar a consulta  
  
1.  Selecione **Form1** no **Gerenciador de Soluções** e clique em **Designer de modos de exibição**.  
  
2.  Arraste o nó **Clientes** da janela **Fontes de Dados** para **Form1**.  
  
3.  Altere o modo de exibição de código ao selecionar **Código** no menu **Exibir**.  
  
4.  Substitua o código no manipulador de eventos `Form1_Load` pelo código abaixo para executar a consulta `FillByCity`.  
  
     [!CODE [VbRaddataTableAdapters#1](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataTableAdapters#1)]  
  
## Executando o aplicativo  
  
#### Para executar o aplicativo  
  
-   Pressione F5.  
  
-   A grade é preenchida por clientes com um valor `City` de `Seattle`.  
  
## Próximas etapas  
  
### Para adicionar funcionalidade ao seu aplicativo  
  
-   Adicione um controle <xref:System.Windows.Forms.TextBox> e um controle <xref:System.Windows.Forms.Button> e passe o valor na caixa de texto para a consulta.  \(`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, TextBox1.Text)`\).  
  
-   Adicione a lógica de validação ao evento <xref:System.Data.DataTable.ColumnChanging> ou <xref:System.Data.DataTable.RowChanging> das tabelas de dados no conjunto de dados.  Para obter mais informações, consulte [Validar dados em conjuntos de dados](../data-tools/validate-data-in-datasets.md).  
  
## Consulte também  
 [Visão geral de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Criar e configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md)   
 [Como criar consultas TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Instruções passo a passo de dados](../Topic/Data%20Walkthroughs.md)   
 [Conectando a dados no Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparando o aplicativo para receber dados](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscando dados no aplicativo](../data-tools/fetching-data-into-your-application.md)   
 [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Editando dados no aplicativo](../data-tools/editing-data-in-your-application.md)