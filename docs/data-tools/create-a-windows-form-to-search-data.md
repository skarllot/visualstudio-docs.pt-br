---
title: "Criar um Windows Form para pesquisar dados | Microsoft Docs"
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
  - "Windows Forms, pesquisando dados"
  - "Windows Forms, exibindo dados"
  - "parâmetros, exibindo dados filtrados"
  - "dados [Visual Studio] parametrizando consultas"
  - "pesquisa de dados [Visual Studio]"
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
caps.latest.revision: 28
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Criar um Windows Form para pesquisar dados
Um cenário de aplicativo comum é exibir dados selecionados em um formulário. Por exemplo, você talvez queira exibir os pedidos de um cliente específico ou os detalhes de uma ordem específica. Nesse cenário, um usuário insere informações em um formulário e, em seguida, uma consulta é executada com a entrada do usuário como parâmetro; ou seja, os dados são selecionados com base em uma consulta parametrizada. A consulta retorna apenas os dados que satisfazem os critérios inseridos pelo usuário. Este passo a passo mostra como criar uma consulta que retorna clientes de uma cidade específica e modificar a interface do usuário para que os usuários podem inserir um nome de cidade e pressionar um botão para executar a consulta.  
  
 Usar consultas parametrizadas ajuda a tornar seu aplicativo eficiente, permitindo que o banco de dados faça o trabalho melhor — filtrar registros rapidamente. Por outro lado, se você solicitar uma tabela de banco de dados inteiro, transferi\-la através da rede e, em seguida, usa lógica do aplicativo para localizar os registros que deseja, seu aplicativo pode ficar lento e ineficiente.  
  
 Você pode adicionar consultas parametrizadas a qualquer TableAdapter \(e controles para aceitar valores de parâmetro e executar a consulta\) usando o **caixa de diálogo do construtor de critérios de pesquisa**. Abra a caixa de diálogo selecionando o **Add Query** comando o **dados** menu \(ou em qualquer marca inteligente TableAdapter\).  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
-   Criar um novo projeto de aplicativo do Windows Forms.  
  
-   Criando e configurando a fonte de dados em seu aplicativo com o **Data Source Configuration Wizard**.  
  
-   Definição do tipo subjacente dos itens na janela fontes de dados.  
  
-   Criando controles que exibem dados, arrastando itens do **fontes de dados** window para um formulário.  
  
-   Adicionando controles para exibir os dados no formulário.  
  
-   Concluindo o **caixa de diálogo Construtor de critérios de pesquisa**.  
  
-   Inserir parâmetros no formulário e executar a consulta parametrizada.  
  
## Pré-requisitos  
 Para concluir este passo a passo, você precisa:  
  
-   Acesso ao banco de dados de exemplo Northwind.  
  
## Criando o aplicativo Windows  
 A primeira etapa é criar um **Windows Application**. Atribuir um nome para o projeto é opcional nesta etapa mas nós daremos um nome porque nós estamos planejando salvá\-lo posteriormente.  
  
#### Para criar o novo projeto de aplicativo do Windows  
  
1.  Do **arquivo** menu, crie um novo projeto.  
  
2.  Nomeie o projeto `WindowsSearchForm`.  
  
3.  Selecione **Windows Application** e clique em **OK**.  
  
     O **WindowsSearchForm** projeto é criado e adicionado ao **Solution Explorer**.  
  
## Criando a fonte de dados  
 Esta etapa cria uma fonte de dados de um banco de dados usando o **Data Source Configuration Wizard**. Você deve ter acesso ao banco de dados de exemplo Northwind para criar a conexão. Para obter informações sobre como configurar o banco de dados de exemplo Northwind, consulte [Install SQL Server sample databases](../data-tools/install-sql-server-sample-databases.md).  
  
#### Para criar a fonte de dados  
  
1.  Sobre o **dados** menu, clique em **Show Data Sources**.  
  
2.  No **fontes de dados** janela, selecione **Add New Data Source** para iniciar o **Data Source Configuration Wizard**.  
  
3.  Selecione **banco de dados** sobre o **Escolher um tipo de fonte de dados** página e, em seguida, clique em **próximo**.  
  
4.  Sobre o **Escolha sua conexão de dados** página faça o seguinte:  
  
    -   Se uma conexão de dados para o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione\-o.  
  
         \- ou \-  
  
    -   Selecione **nova conexão** para iniciar o **Adicionar\/Modificar conexão** caixa de diálogo.  
  
5.  Se seu banco de dados exigir uma senha, selecione a opção para incluir dados confidenciais e, em seguida, clique em **próximo**.  
  
6.  Clique em **próximo** sobre o **Salvar cadeia de conexão no arquivo de configuração do aplicativo** página.  
  
7.  Expanda o **tabelas** nó o **Choose your Database Objects** página.  
  
8.  Selecione o **clientes** tabela e, em seguida, clique em **Concluir**.  
  
     O **NorthwindDataSet** é adicionado ao seu projeto e o **clientes** tabela aparece no **fontes de dados** janela.  
  
## Criando o formulário  
 Você pode criar os controles associados a dados arrastando itens do **fontes de dados** window para seu formulário.  
  
#### Para criar controles ligados a dados no formulário  
  
1.  Expanda o **clientes** nó o **fontes de dados** janela.  
  
2.  Arrastar o **clientes** nó a partir de **fontes de dados** janela ao seu formulário.  
  
     Um <xref:System.Windows.Forms.DataGridView> e uma faixa de ferramenta \(<xref:System.Windows.Forms.BindingNavigator>\) para navegação em registros aparecem no formulário. Um [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> aparecem na bandeja de componentes.  
  
## Adicionando parametrização \(funcionalidade de pesquisa\) à consulta  
 Você pode adicionar uma cláusula WHERE à consulta original usando o **caixa de diálogo do construtor de critérios de pesquisa**.  
  
#### Para criar uma consulta parametrizada e controles para inserir os parâmetros  
  
1.  Selecione o <xref:System.Windows.Forms.DataGridView> controle e, em seguida, escolha **Add Query** sobre o **dados** menu.  
  
2.  Tipo `FillByCity` no **novo nome de consulta** área de **caixa de diálogo do construtor de critérios de pesquisa**.  
  
3.  Adicionar `WHERE City = @City` à consulta no **texto da consulta** área.  
  
     A consulta deve ser semelhante ao seguinte:  
  
     `SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax`  
  
     `FROM Customers`  
  
     `WHERE City = @City`  
  
    > [!NOTE]
    >  Fontes de dados Access e OleDb usam o ponto de interrogação '?' para denotar parâmetros, portanto a cláusula WHERE teria esta aparência: `WHERE City = ?`.  
  
4.  Clique em **OK** para fechar o **Pesquisar Construtor de critérios** caixa de diálogo.  
  
     Um **FillByCityToolStrip** é adicionado ao formulário.  
  
## Testando o aplicativo  
 Executar o aplicativo abre o formulário pronto para receber o parâmetro como entrada.  
  
#### Para testar o aplicativo  
  
1.  Pressione F5 para executar o aplicativo.  
  
2.  Tipo **Londres** para o **City** caixa de texto e clique **FillByCity**.  
  
     A grade de dados é preenchida com clientes que atendem aos critérios de parametrização. Neste exemplo, a grade de dados exibe clientes que têm um valor de **Londres** em seus **City** coluna.  
  
## Próximas etapas  
 Dependendo dos requisitos de aplicativo, há várias etapas que você pode desejar executar depois de criar um formulário parametrizado. Alguns aprimoramentos que você poderia fazer neste passo a passo incluem:  
  
-   Adicionar controles que exibem dados relacionados. Para obter mais informações, consulte [Como exibir dados relacionados em um Aplicativo do Windows Forms](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md).  
  
-   Editando o conjunto de dados para adicionar ou remover objetos de banco de dados. Para obter mais informações, consulte [Criar e configurar conjuntos de dados](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
## Consulte também  
 [Associar controles dos Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)