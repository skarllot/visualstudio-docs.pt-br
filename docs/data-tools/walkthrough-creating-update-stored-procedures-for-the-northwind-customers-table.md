---
title: "Instru&#231;&#245;es passo a passo: criando procedimentos armazenados atualizados para a tabela Clientes do Northwind | Microsoft Docs"
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
  - "banco de dados de exemplo Northwind"
  - "Designer Relacional de Objetos, procedimentos armazenados"
  - "procedimentos armazenados [Visual Studio]"
ms.assetid: 6fd9e7e0-6862-44d3-9710-acc5a72d4ffd
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Instru&#231;&#245;es passo a passo: criando procedimentos armazenados atualizados para a tabela Clientes do Northwind
Alguns tópicos de Ajuda na documentação do [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] exigem procedimentos armazenados adicionais no banco de dados de exemplo Northwind para realizar atualizações \(Insere, Atualiza e Exclui\) de dados na tabela Clientes.  
  
 Essa explicação passo a passo fornece orientações para criar esses procedimentos armazenados adicionais nos bancos de dados de exemplo Northwind para [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)].  
  
 A seção Próximas Etapas mais adiante neste tópico fornece links para tópicos que demonstram como trabalhar com esses procedimentos armazenados adicionais.  
  
 Durante essa explicação passo a passo, será ensinado como realizar as seguintes tarefas:  
  
-   Criar uma conexão de dados com o banco de dados de exemplo Northwind.  
  
-   Criar os procedimentos armazenados.  
  
## Pré-requisitos  
 Para concluir esta explicação passo a passo, será necessário:  
  
-   Acessar a versão do SQL Server do banco de dados de exemplo Northwind.  Para obter mais informações, consulte [Como instalar bancos de dados de exemplo](../data-tools/how-to-install-sample-databases.md).  
  
## Conectando ao Banco de Dados Northwind  
 Essa explicação passo a passo exige uma conexão com a versão do SQL Server do banco de dados Northwind.  O procedimento a seguir fornece orientações para criar a conexão de dados.  
  
> [!NOTE]
>  Se já houver uma conexão de dados com o banco de dados Northwind, avance para a próxima seção, Criando os Procedimentos Armazenados.  
  
#### Criar uma conexão de dados com o banco de dados Northwind do SQL Server  
  
1.  No menu **Visualizar**, clique em **Gerenciador de Servidores** ou **Navegador de Banco de Dados**.  
  
2.  Clique com o botão direito em **Conexões de Dados** e clique em **Adicionar Conexão**.  
  
3.  Na caixa de diálogo **Escolher Fonte de Dados**, clique em **Microsoft SQL Server** e em **OK**.  
  
     Se a caixa **Adicionar Conexão** for exibida e a **Fonte de dados** não for **Microsoft SQL Server \(SqlClient\)**, clique em **Alterar** para abrir a caixa de diálogo **Escolher\/Alterar Fonte de Dados**, clique em **Microsoft SQL Server** e em **OK**.  
  
4.  Clique em um **Nome de servidor** na lista suspensa ou digite o nome do servidor no qual o banco de dados Northwind está localizado.  
  
5.  Com base nos requisitos do banco de dados ou aplicativo, clique em **Usar Autenticação do Windows** ou use um nome do usuário e senha para fazer logon no computador que está executando o SQL Server \(**Autenticação do SQL Server**\).  
  
6.  Clique no banco de dados Northwind na lista **Selecione ou insira um nome de banco de dados**.  
  
7.  Clique em **OK**.  
  
     A conexão de dados é adicionada ao **Gerenciador de Servidores**\/**Navegador de Banco de Dados**.  
  
## Criando os procedimentos armazenados  
 Crie os procedimentos armazenados executando o script SQL no banco de dados Northwind usando o [Visual Database Tools](http://msdn.microsoft.com/pt-br/6b145922-2f00-47db-befc-bf351b4809a1) disponível no **Gerenciador de Servidores**\/**Navegador de Banco de Dados**.  
  
#### Criar os procedimentos armazenados usando um script SQL  
  
1.  Expanda o banco de dados Northwind no **Gerenciador de Servidores**\/**Navegador de Banco de Dados**.  
  
2.  Clique com o botão direito no nó **Procedimentos Armazenados** e clique em **Adicionar Novo Procedimento Armazenado**.  
  
3.  Cole o seguinte código no Editor de Códigos, substituindo o modelo `CREATE PROCEDURE`:  
  
    ```  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'SelectCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.[SelectCustomers]  
    GO  
  
    CREATE PROCEDURE dbo.[SelectCustomers]  
    AS  
        SET NOCOUNT ON;  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM dbo.Customers  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'InsertCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.InsertCustomers  
    GO  
  
    CREATE PROCEDURE dbo.InsertCustomers  
    (  
        @CustomerID nchar(5),  
        @CompanyName nvarchar(40),  
        @ContactName nvarchar(30),  
        @ContactTitle nvarchar(30),  
        @Address nvarchar(60),  
        @City nvarchar(15),  
        @Region nvarchar(15),  
        @PostalCode nvarchar(10),  
        @Country nvarchar(15),  
        @Phone nvarchar(24),  
        @Fax nvarchar(24)  
    )  
    AS  
        SET NOCOUNT OFF;  
    INSERT INTO [dbo].[Customers] ([CustomerID], [CompanyName], [ContactName], [ContactTitle], [Address], [City], [Region], [PostalCode], [Country], [Phone], [Fax]) VALUES (@CustomerID, @CompanyName, @ContactName, @ContactTitle, @Address, @City, @Region, @PostalCode, @Country, @Phone, @Fax);  
  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE (CustomerID = @CustomerID)  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'UpdateCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.UpdateCustomers  
    GO  
  
    CREATE PROCEDURE dbo.UpdateCustomers  
    (  
        @CustomerID nchar(5),  
        @CompanyName nvarchar(40),  
        @ContactName nvarchar(30),  
        @ContactTitle nvarchar(30),  
        @Address nvarchar(60),  
        @City nvarchar(15),  
        @Region nvarchar(15),  
        @PostalCode nvarchar(10),  
        @Country nvarchar(15),  
        @Phone nvarchar(24),  
        @Fax nvarchar(24),  
        @Original_CustomerID nchar(5)  
    )  
    AS  
        SET NOCOUNT OFF;  
    UPDATE [dbo].[Customers] SET [CustomerID] = @CustomerID, [CompanyName] = @CompanyName, [ContactName] = @ContactName, [ContactTitle] = @ContactTitle, [Address] = @Address, [City] = @City, [Region] = @Region, [PostalCode] = @PostalCode, [Country] = @Country, [Phone] = @Phone, [Fax] = @Fax WHERE (([CustomerID] = @Original_CustomerID));  
  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE (CustomerID = @CustomerID)  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'DeleteCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.DeleteCustomers  
    GO  
  
    CREATE PROCEDURE dbo.DeleteCustomers  
    (  
        @Original_CustomerID nchar(5)  
    )  
    AS  
        SET NOCOUNT OFF;  
    DELETE FROM [dbo].[Customers] WHERE (([CustomerID] = @Original_CustomerID))  
    GO  
    ```  
  
4.  Selecionar todo o texto no Editor de Código, clique com o botão direito no texto selecionado e clique em **Executar Seleção**.  
  
     Os procedimentos armazenados SelectCustomers, InsertCustomers, UpdateCustomers e DeleteCustomers são criados para o banco de dados Northwind.  
  
## Próximas etapas  
 Agora que os procedimentos armazenados foram criados, tente as seguintes explicações passo a passo que demonstram como trabalhar com eles:  
  
 [Como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões \(Object Relational Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
  
 [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)  
  
 [Passo a passo: Personalizando a inserção, atualização e exclusão de comportamento de classes de entidade](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
  
## Consulte também  
 [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)