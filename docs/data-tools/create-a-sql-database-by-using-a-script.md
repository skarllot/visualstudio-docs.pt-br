---
title: "Criar um banco de dados SQL usando um script | Microsoft Docs"
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
ms.assetid: 36f913c0-f5a7-4831-83a0-baba721ac95c
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Criar um banco de dados SQL usando um script
Neste passo a passo, você usa o Visual Studio para criar um pequeno banco de dados que contém o código de exemplo para [Criar um aplicativo simples de dados usando o ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).  
  
 **Neste tópico**  
  
-   [Criar um script que contenha um esquema de banco de dados](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)  
  
-   [Criar um projeto de banco de dados e importar um esquema](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)  
  
-   [Implantar o banco de dados](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)  
  
## Pré-requisitos  
 Para concluir este passo a passo, você deve ter o SQL Express LocalDB ou outro banco de dados SQL instalado.  
  
##  <a name="CreateScript"></a> Criar um script que contenha um esquema de banco de dados  
  
#### Para criar um script do qual você pode importar um esquema  
  
1.  Em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], na barra de menus, escolha **arquivo**, **novo**, **arquivo**.  
  
     O **novo arquivo** caixa de diálogo é exibida.  
  
2.  No **categorias** escolha **geral**.  
  
3.  No **modelos** escolha **arquivo Sql**, e, em seguida, escolha o **Abrir** botão.  
  
     Abre o Editor do Transact\-SQL.  
  
4.  Copie o seguinte código Transact\-SQL e, em seguida, colá\-lo no Editor de Transact\-SQL.  
  
    ```  
    PRINT N'Creating Sales...';  
    GO  
    CREATE SCHEMA [Sales]  
        AUTHORIZATION [dbo];  
    GO  
    PRINT N'Creating Sales.Customer...';  
    GO  
    CREATE TABLE [Sales].[Customer] (  
        [CustomerID]   INT           IDENTITY (1, 1) NOT NULL,  
        [CustomerName] NVARCHAR (40) NOT NULL,  
        [YTDOrders]    INT           NOT NULL,  
        [YTDSales]     INT           NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Orders...';  
    GO  
    CREATE TABLE [Sales].[Orders] (  
        [CustomerID] INT      NOT NULL,  
        [OrderID]    INT      IDENTITY (1, 1) NOT NULL,  
        [OrderDate]  DATETIME NOT NULL,  
        [FilledDate] DATETIME NULL,  
        [Status]     CHAR (1) NOT NULL,  
        [Amount]     INT      NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDOrders...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDOrders] DEFAULT 0 FOR [YTDOrders];  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDSales...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDSales] DEFAULT 0 FOR [YTDSales];  
    GO  
    PRINT N'Creating Sales.Def_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_OrderDate] DEFAULT GetDate() FOR [OrderDate];  
    GO  
    PRINT N'Creating Sales.Def_Orders_Status...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_Status] DEFAULT 'O' FOR [Status];  
    GO  
    PRINT N'Creating Sales.PK_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [PK_Customer_CustID] PRIMARY KEY CLUSTERED ([CustomerID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.PK_Orders_OrderID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [PK_Orders_OrderID] PRIMARY KEY CLUSTERED ([OrderID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.FK_Orders_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [FK_Orders_Customer_CustID] FOREIGN KEY ([CustomerID]) REFERENCES [Sales].[Customer] ([CustomerID]) ON DELETE NO ACTION ON UPDATE NO ACTION;  
    GO  
    PRINT N'Creating Sales.CK_Orders_FilledDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_FilledDate] CHECK ((FilledDate >= OrderDate) AND (FilledDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.CK_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_OrderDate] CHECK ((OrderDate > '01/01/2005') and (OrderDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.uspCancelOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspCancelOrder]  
    @OrderID INT  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'X'  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders - @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspFillOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspFillOrder]  
    @OrderID INT, @FilledDate DATETIME  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'F',  
           [FilledDate] = @FilledDate  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDSales = YTDSales + @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspNewCustomer...';  
    GO  
    CREATE PROCEDURE [Sales].[uspNewCustomer]  
    @CustomerName NVARCHAR (40),  
    @CustomerID INT OUTPUT  
    AS  
    BEGIN  
    INSERT INTO [Sales].[Customer] (CustomerName) VALUES (@CustomerName);  
    SET @CustomerID = SCOPE_IDENTITY();  
    RETURN @@ERROR  
    END  
    GO  
    PRINT N'Creating Sales.uspPlaceNewOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspPlaceNewOrder]  
    @CustomerID INT, @Amount INT, @OrderDate DATETIME, @Status CHAR (1)='O'  
    AS  
    BEGIN  
    DECLARE @RC INT  
    BEGIN TRANSACTION  
    INSERT INTO [Sales].[Orders] (CustomerID, OrderDate, FilledDate, Status, Amount)   
         VALUES (@CustomerID, @OrderDate, NULL, @Status, @Amount)  
    SELECT @RC = SCOPE_IDENTITY();  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders + @Amount  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    RETURN @RC  
    END  
    GO  
    CREATE PROCEDURE [Sales].[uspShowOrderDetails]  
    @CustomerID INT=0  
    AS  
    BEGIN  
    SELECT [C].[CustomerName], CONVERT(date, [O].[OrderDate]), CONVERT(date, [O].[FilledDate]), [O].[Status], [O].[Amount]  
      FROM [Sales].[Customer] AS C  
      INNER JOIN [Sales].[Orders] AS O  
         ON [O].[CustomerID] = [C].[CustomerID]  
      WHERE [C].[CustomerID] = @CustomerID  
    END  
    GO  
    ```  
  
5.  Na barra de menus, escolha **arquivo**, **Salvar SqlQuery\_1.sql como**.  
  
     O **Salvar arquivo como** caixa de diálogo é exibida.  
  
6.  No **nome de arquivo** digite `SampleImportScript.sql`, anote o local onde você poderá salvar o arquivo e escolha o **Salvar** botão.  
  
7.  Na barra de menus, escolha **arquivo**, **Fechar solução**.  
  
     Em seguida, crie um projeto de banco de dados e, em seguida, importar o esquema do script que você criou.  
  
##  <a name="CreateProject"></a> Criar um projeto de banco de dados e importar um esquema  
  
#### Para criar um projeto de banco de dados  
  
1.  Na barra de menus, escolha **arquivo**, **novo**, **projeto**.  
  
     O **novo projeto** caixa de diálogo é exibida.  
  
2.  Em **instalados**, expanda o **modelos** nó, expanda o **outros idiomas** nó, escolha o **SQL Server** categoria e, em seguida, escolha o **projeto de banco de dados do SQL Server** modelo.  
  
    > [!NOTE]
    >  O **outros idiomas** nó não aparece em todas as instalações do Visual Studio.  
  
3.  No **nome** digite `Small Database`.  
  
4.  Selecione o **criar diretório para solução** caixa de seleção se ainda não estiver selecionada.  
  
5.  Limpar o **Adicionar ao controle de origem** caixa de seleção se ele já não estiver desmarcada e, em seguida, escolha o **OK** botão.  
  
     O projeto de banco de dados é criado e aparece no **Solution Explorer**.  
  
     Em seguida, importe o esquema de banco de dados do script.  
  
#### Para importar um esquema de banco de dados de um script  
  
1.  Na barra de menus, escolha **projeto**, **importação**, **Script**.  
  
2.  Na página de boas\-vindas, revise o texto e, em seguida, escolha o **próximo** botão.  
  
3.  Escolha o **único arquivo** botão de opção e, em seguida, escolha o **Procurar** botão.  
  
     O **Importar SQL Script** caixa de diálogo é exibida.  
  
4.  Abra a pasta onde você salvou o arquivo SampleImportScript.sql, escolha\-o e escolha o **Abrir** botão.  
  
5.  Escolha o **Concluir** para fechar o **Importar SQL Script** caixa de diálogo.  
  
     O script é importado, e os objetos que o script define são adicionados ao seu projeto de banco de dados.  
  
6.  Revise o resumo e, em seguida, escolha o **Concluir** para fechar o **Importar arquivo de Script SQL** caixa de diálogo.  
  
7.  Em **Solution Explorer**, expanda a vendas, Scripts e segurança pastas do seu projeto e verificar se eles contêm arquivos. SQL.  
  
8.  Em **SQL Server Object Explorer**, verifique se o banco de dados aparece sob o **projetos** nó.  
  
     Neste ponto, o banco de dados contém apenas objetos de sistema, como tabelas e procedimentos armazenados. Depois de implantar o banco de dados, ele irá conter as tabelas de usuário e procedimentos armazenados que definem os scripts.  
  
##  <a name="DeployDatabase"></a> Implantar o banco de dados  
 Quando você escolhe a tecla F5, você implanta ou publica o banco de dados para um banco de dados LocalDB por padrão. Você pode implantar o banco de dados para um local diferente, abra a página de propriedades do projeto, escolhendo o **Depurar** guia e, em seguida, alterando a cadeia de conexão.