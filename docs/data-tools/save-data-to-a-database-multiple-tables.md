---
title: "Instru&#231;&#245;es passo a passo: salvando dados em um banco de dados (v&#225;rias tabelas) | Microsoft Docs"
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
  - "dados [Visual Studio], salvar"
  - "dados [Visual Studio], atualizando"
  - "salvando dados, explicações passo a passo"
  - "atualizando conjuntos de dados, explicações passo a passo"
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: 24
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Instru&#231;&#245;es passo a passo: salvando dados em um banco de dados (v&#225;rias tabelas)
Um dos cenários mais comuns no desenvolvimento de aplicativos é exibir dados em um formulário em um aplicativo do Windows, editar os dados e enviar os dados atualizados no banco de dados. Este passo a passo cria um formulário que exibe dados de duas tabelas relacionadas e mostra como editar registros e salvar alterações no banco de dados. Este exemplo usa o `Customers` e `Orders` tabelas do banco de dados de exemplo Northwind.  
  
 Você pode salvar dados em seu aplicativo de volta para o banco de dados chamando o `Update` método de um TableAdapter. Quando você arrasta itens do **fontes de dados** janela, código para salvar dados será automaticamente adicionada para a primeira tabela arrastada para um formulário. Quaisquer tabelas adicionais a um formulário exigem a inclusão manual de qualquer código necessário para salvar dados. Este passo a passo mostra como adicionar código para salvar atualizações de mais de uma tabela.  
  
> [!NOTE]
>  Caixas de diálogo e comandos de menu que você vê podem diferir daqueles descritos na Ajuda, dependendo de suas configurações ativas ou edição. Para alterar suas configurações, escolha **Import and Export Settings** sobre o **ferramentas** menu. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
-   Criando um novo **Windows Application** projeto.  
  
-   Criando e configurando uma fonte de dados em seu aplicativo com o [Assistente para Configuração da Fonte de Dados](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Configurando os controles dos itens na [Janela Fontes de Dados](../Topic/Data%20Sources%20Window.md). Para obter mais informações, consulte [Como definir o controle a ser criado quando arrastado da janela Fontes de Dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Criando controles associados a dados arrastando itens do **fontes de dados** window para seu formulário.  
  
-   Modificando alguns registros em cada tabela no conjunto de dados.  
  
-   Modificando o código para enviar os dados atualizados no conjunto de dados no banco de dados.  
  
## Pré-requisitos  
 Para concluir este passo a passo, você precisará de:  
  
-   Acesso ao banco de dados de exemplo Northwind.  Para obter mais informações, consulte [Como instalar bancos de dados de exemplo](../data-tools/how-to-install-sample-databases.md).  
  
## Criando o aplicativo Windows  
 A primeira etapa é criar um **Windows Application**. Atribuir um nome para o projeto é opcional nesta etapa mas nós daremos um nome porque nós estamos planejando salvá\-lo posteriormente.  
  
#### Para criar o novo projeto de aplicativo do Windows  
  
1.  Do **arquivo** menu, crie um novo projeto.  
  
2.  Nomeie o projeto `UpdateMultipleTablesWalkthrough`.  
  
3.  Selecione **Windows Application** e clique em **OK**. Para obter mais informações, consulte [Aplicativos cliente](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     O **UpdateMultipleTablesWalkthrough** projeto é criado e adicionado ao **Solution Explorer**.  
  
## Criando a fonte de dados  
 Esta etapa cria uma fonte de dados do banco de dados Northwind usando o **Data Source Configuration Wizard**. Você deve ter acesso ao banco de dados de exemplo Northwind para criar a conexão. Para obter informações sobre como configurar o banco de dados de exemplo Northwind, consulte [Como instalar bancos de dados de exemplo](../data-tools/how-to-install-sample-databases.md).  
  
#### Para criar a fonte de dados  
  
1.  Sobre o **dados** menu, clique em **Show Data Sources**.  
  
2.  No **fontes de dados** janela, clique em **Add New Data Source** para iniciar o **Data Source Configuration Wizard**.  
  
3.  Selecione **banco de dados** sobre o **Escolher um tipo de fonte de dados** página e, em seguida, clique em **próximo**.  
  
4.  Sobre o **Escolha sua conexão de dados** página faça o seguinte:  
  
    -   Se uma conexão de dados para o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione\-o.  
  
         \- ou \-  
  
    -   Selecione **nova conexão** para abrir o **Adicionar\/Modificar conexão** caixa de diálogo.  
  
5.  Se seu banco de dados exigir uma senha, selecione a opção para incluir dados confidenciais e, em seguida, clique em **próximo**.  
  
6.  Clique em **próximo** sobre o **Salvar cadeia de conexão no arquivo de configuração do aplicativo** página.  
  
7.  Expanda o **tabelas** nó o **Choose your Database Objects** página.  
  
8.  Selecione o **clientes** e **pedidos** tabelas e clique **Concluir**.  
  
     O **NorthwindDataSet** é adicionado ao seu projeto e as tabelas aparecem no **fontes de dados** janela.  
  
## Configurando os controles a serem criados  
 Para este passo a passo os dados no `Customers` tabela estará em um **detalhes** layout onde os dados são exibidos em controles individuais. Os dados a partir o `Orders` tabela estará em um **grade** layout exibido em um <xref:System.Windows.Forms.DataGridView> controle.  
  
#### Para definir o tipo subjacente para os itens na janela fontes de dados  
  
1.  Expanda o **clientes** nó o **fontes de dados** janela.  
  
2.  Alterar o controle do **clientes** tabela para controles individuais selecionando **detalhes** da lista de controle de **clientes** nó. Para obter mais informações, consulte [Como definir o controle a ser criado quando arrastado da janela Fontes de Dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## Criando o formulário de associação de dados  
 Você pode criar os controles associados a dados arrastando itens do **fontes de dados** window para seu formulário.  
  
#### Para criar controles ligados a dados no formulário  
  
1.  Arraste principal **clientes** nó a partir de **fontes de dados** window para **Form1**.  
  
     Controles ligados a dados com rótulos descritivos aparecem no formulário, juntamente com uma faixa de ferramenta \(<xref:System.Windows.Forms.BindingNavigator>\) para navegação em registros. Um [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> aparecem na bandeja de componentes.  
  
2.  Arraste relacionado **pedidos** nó a partir de **fontes de dados** window para **Form1**.  
  
    > [!NOTE]
    >  Relacionado **pedidos** nó está localizado abaixo do **Fax** coluna e é um nó filho do **clientes** nó.  
  
     Um <xref:System.Windows.Forms.DataGridView> controle e uma faixa de ferramenta \(<xref:System.Windows.Forms.BindingNavigator>\) para navegação em registros aparecem no formulário. Um [OrdersTableAdapter](../data-tools/tableadapter-overview.md) e <xref:System.Windows.Forms.BindingSource> aparecem na bandeja de componentes.  
  
## Adicionando código para atualizar o banco de dados  
 Você pode atualizar o banco de dados chamando o `Update` métodos o **clientes** e **pedidos** TableAdapters. Por padrão, um manipulador de eventos para o <xref:System.Windows.Forms.BindingNavigator>da **Salvar** botão é adicionado ao código do formulário para enviar atualizações para o banco de dados. Este procedimento modifica esse código para enviar atualizações na ordem apropriada para eliminar a possibilidade de gerar erros de integridade referencial. O código também implementa o tratamento de erro ao encapsular a chamada de atualização em um bloco try\-catch. Você pode modificar o código para atender às necessidades do seu aplicativo.  
  
> [!NOTE]
>  Para maior clareza esta explicação passo a passo não usa uma transação, mas se você estiver atualizando duas ou mais tabelas relacionadas, então você deve incluir toda a lógica de atualização dentro de uma transação. Uma transação é um processo que garante que todas as alterações relacionadas a um banco de dados terão êxito antes de confirmar as alterações. Para obter mais informações, consulte [Transações e simultaneidade](../Topic/Transactions%20and%20Concurrency.md).  
  
#### Para adicionar lógica de atualização para o aplicativo  
  
1.  Clique duas vezes o **Salvar** botão o <xref:System.Windows.Forms.BindingNavigator> para abrir o Editor de código para o `bindingNavigatorSaveItem_Click` manipulador de eventos.  
  
2.  Substitua o código no manipulador de eventos para chamar o `Update` métodos dos TableAdapters relacionados. O código a seguir primeiramente cria três tabelas de dados temporárias para armazenar as informações atualizadas para cada <xref:System.Data.DataRowState> \(<xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, e <xref:System.Data.DataRowState>\). Em seguida, as atualizações são executadas na ordem correta. O código deve parecer com o seguinte:  
  
     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-cs[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]  
  
## Testando o aplicativo  
  
#### Para testar o aplicativo  
  
1.  Pressione F5.  
  
2.  Faça algumas alterações nos dados de um ou mais registros em cada tabela.  
  
3.  Pressione o **Salvar** botão.  
  
4.  Verifique os valores no banco de dados para verificar se as alterações foram salvas.  
  
## Próximas etapas  
 Dependendo dos requisitos de aplicativo, há várias etapas que você pode desejar executar após criar um formulário de associação de dados em seu aplicativo do Windows. Alguns aprimoramentos que você poderia fazer neste passo a passo incluem:  
  
-   Adicionando funcionalidade de pesquisa ao formulário. Para obter mais informações, consulte [Como adicionar uma consulta parametrizada a um aplicativo dos Windows Forms](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md).  
  
-   Editando a fonte de dados para adicionar ou remover objetos de banco de dados. Para obter mais informações, consulte [Como editar um conjunto de dados](../Topic/How%20to:%20Edit%20a%20Dataset.md).  
  
## Consulte também  
 [Salvar dados no banco de dados](../data-tools/save-data-back-to-the-database.md)