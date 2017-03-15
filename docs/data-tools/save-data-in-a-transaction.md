---
title: "Instru&#231;&#245;es passo a passo: salvando dados em uma transa&#231;&#227;o | Microsoft Docs"
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
  - "dados [Visual Studio], salvando em uma transação"
  - "salvando dados"
  - "Namespace System.Transactions"
  - "Namespace de transações"
  - "transações, salvando dados"
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Instru&#231;&#245;es passo a passo: salvando dados em uma transa&#231;&#227;o
Este passo a passo demonstra como salvar dados em uma transação usando o <xref:System.Transactions> namespace. Este exemplo usa o `Customers` e `Orders` tabelas do banco de dados de exemplo Northwind.  
  
## Pré-requisitos  
 Este passo a passo requer acesso ao banco de dados de exemplo Northwind. Para obter informações sobre como configurar o banco de dados de exemplo Northwind, consulte [Como instalar bancos de dados de exemplo](../data-tools/how-to-install-sample-databases.md).  
  
## Criando um aplicativo do Windows  
 A primeira etapa é criar um **Windows Application**.  
  
#### Para criar o novo projeto do Windows  
  
1.  No Visual Studio, do **arquivo** menu, crie um novo **projeto**.  
  
2.  Nomeie o projeto **SavingDataInATransactionWalkthrough**.  
  
3.  Selecione **Windows Application** e clique em **OK**. Para obter mais informações, consulte [Aplicativos cliente](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     O **SavingDataInATransactionWalkthrough** projeto é criado e adicionado ao **Solution Explorer**.  
  
## Criando uma fonte de dados do banco de dados  
 Esta etapa usa o [Assistente para Configuração da Fonte de Dados](../data-tools/media/data-source-configuration-wizard.png) para criar uma fonte de dados com base no `Customers` e `Orders` tabelas no banco de dados de exemplo Northwind.  
  
#### Para criar a fonte de dados  
  
1.  Sobre o **dados** menu, clique em **Show Data Sources**.  
  
2.  No **fontes de dados** janela, selecione **Add New Data Source** para iniciar o **Data Source Configuration Wizard**.  
  
3.  Selecione **banco de dados** sobre o **Escolher um tipo de fonte de dados** página e, em seguida, clique em **próximo**.  
  
4.  Sobre o **Escolha sua conexão de dados** página faça o seguinte:  
  
    -   Se uma conexão de dados para o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione\-o.  
  
         \- ou \-  
  
    -   Selecione **nova conexão** para iniciar o **Adicionar\/Modificar conexão** caixa de diálogo caixa e criar uma conexão com o banco de dados Northwind.  
  
5.  Se seu banco de dados exigir uma senha, selecione a opção para incluir dados confidenciais e, em seguida, clique em **próximo**.  
  
6.  Clique em **próximo** sobre o **Salvar cadeia de conexão no arquivo de configuração do aplicativo** página.  
  
7.  Expanda o **tabelas** nó o **Choose your Database Objects** página.  
  
8.  Selecione o `Customers` e `Orders` tabelas e clique **Concluir**.  
  
     O **NorthwindDataSet** é adicionado ao seu projeto e a `Customers` e `Orders` as tabelas aparecem no **fontes de dados** janela.  
  
## Adicionando controles ao formulário  
 Você pode criar os controles associados a dados arrastando itens do **fontes de dados** window para seu formulário.  
  
#### Para criar dados vinculados a controles no Windows Form  
  
-   Expanda o **clientes** nó o **fontes de dados** janela.  
  
-   Arraste principal **clientes** nó a partir de **fontes de dados** window para **Form1**.  
  
     Um <xref:System.Windows.Forms.DataGridView> controle e uma faixa de ferramenta \(<xref:System.Windows.Forms.BindingNavigator>\) para navegação em registros aparecem no formulário. Um [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> aparecem na bandeja de componentes.  
  
-   Arraste o relacionado **pedidos** nó \(o nó de tabela filha relacionada abaixo o **Fax** coluna, não principal **pedidos** nó\) para o formulário abaixo o **CustomersDataGridView**.  
  
     Um <xref:System.Windows.Forms.DataGridView> aparece no formulário. Um [OrdersTableAdapter](../data-tools/tableadapter-overview.md) e <xref:System.Windows.Forms.BindingSource> aparecem na bandeja de componentes.  
  
## Adicionando uma referência ao Assembly System. Transactions  
 As transações que usam o <xref:System.Transactions> namespace. Uma referência de projeto ao assembly System. Transactions não é adicionada por padrão, portanto você precisa adicioná\-lo manualmente.  
  
#### Para adicionar uma referência para o arquivo DLL System. Transactions  
  
1.  Do **projeto** menu, escolha **Adicionar referência**.  
  
2.  Selecione **System. Transactions** \(sobre o **.NET** guia\) e clique em **OK**.  
  
     Uma referência a **System. Transactions** é adicionado ao projeto.  
  
## Modificando o código no botão SaveItem do BindingNavigator  
 Por padrão, para a primeira tabela arrastada para seu formulário, código é adicionado para o `click` botão evento do salvamento a <xref:System.Windows.Forms.BindingNavigator>. Você precisa adicionar manualmente o código para atualizar quaisquer tabelas adicionais. Para este passo a passo, podemos refatorar o código salvar existente manipulador de eventos de clique do botão e criar mais alguns métodos para fornecer a funcionalidade de atualização específica com base em se a linha precisa ser adicionada ou excluída.  
  
#### Para modificar o auto\-código salvar gerado  
  
1.  Clique duas vezes o **Salvar** botão o **CustomersBindingNavigator** \(o botão com o ícone de disquete\).  
  
2.  Substitua o `CustomersBindingNavigatorSaveItem_Click` método com o código a seguir:  
  
     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-cs[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]  
  
 A ordem para reconciliar as alterações aos dados relacionados é da seguinte maneira:  
  
-   Excluir registros filho \(neste caso, exclua registros do `Orders` tabela\)  
  
-   Excluir registros pai \(neste caso, exclua registros do `Customers` tabela\)  
  
-   Inserir registros pai \(neste caso, inserir registros a `Customers` tabela\)  
  
-   Inserir registros filho \(neste caso, inserir registros a `Orders` tabela\)  
  
#### Para excluir pedidos existentes  
  
-   Adicione o seguinte `DeleteOrders` método **Form1**:  
  
     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-cs[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]  
  
#### Para excluir clientes existentes  
  
-   Adicione o seguinte `DeleteCustomers` método **Form1**:  
  
     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-cs[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]  
  
#### Para adicionar novos clientes  
  
-   Adicione o seguinte `AddNewCustomers` método **Form1**:  
  
     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-cs[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]  
  
#### Para adicionar novos pedidos  
  
-   Adicione o seguinte `AddNewOrders` método **Form1**:  
  
     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-cs[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]  
  
## Executando o aplicativo  
  
#### Para executar o aplicativo  
  
-   Pressione F5 para executar o aplicativo.  
  
## Consulte também  
 [Salvar dados no banco de dados](../data-tools/save-data-back-to-the-database.md)