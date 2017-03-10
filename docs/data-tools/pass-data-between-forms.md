---
title: "Passar dados entre formul&#225;rios | Microsoft Docs"
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
  - "explicações passo a passo [Windows Forms], dados"
  - "explicações passo a passo [Visual Studio], dados"
  - "dados [Visual Studio], transmitindo entre formulários"
  - "transmitindo dados entre formulários"
  - "Explicações passo a passo do Windows Forms"
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Passar dados entre formul&#225;rios
Este passo a passo fornece instruções passo a passo para passar dados de um formulário para outro. Usando as tabelas customers e orders do Northwind permitirá que os usuários selecionem um cliente e um segundo formulário exibirá os pedidos do cliente selecionado. Este passo a passo mostra como criar um método em um formulário que recebe dados do primeiro formulário.  
  
> [!NOTE]
>  Este passo a passo demonstra apenas uma forma de passar dados entre formulários. Existem outras opções para passar dados para um formulário, incluindo estes métodos: você pode criar um segundo construtor para receber dados, ou você pode criar uma propriedade pública que pode ser definida com dados do primeiro formulário.  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
-   Criando um novo **Windows Application** projeto.  
  
-   Criando e configurando um dataset com o [Assistente para Configuração da Fonte de Dados](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Selecionando o controle a ser criado no formulário ao arrastar itens do **fontes de dados** janela. Para obter mais informações, consulte [Como definir o controle a ser criado quando arrastado da janela Fontes de Dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Criando um controle ligado a dados arrastando itens do **fontes de dados** window para um formulário.  
  
-   Criando um segundo formulário com uma grade para exibir dados.  
  
-   Criar uma consulta TableAdapter para buscar pedidos para um cliente específico.  
  
-   Passando dados entre formulários.  
  
## Pré-requisitos  
 Para concluir este passo a passo, você precisa:  
  
-   Acesso ao banco de dados de exemplo Northwind. Para obter mais informações, consulte [Como instalar bancos de dados de exemplo](../data-tools/how-to-install-sample-databases.md).  
  
## Criando o aplicativo Windows  
  
#### Para criar o novo projeto do Windows  
  
1.  Do **arquivo** menu, crie um novo projeto.  
  
2.  Nomeie o projeto `PassingDataBetweenForms`.  
  
3.  Selecione **Windows Forms Application** e clique em **OK**. Para obter mais informações, consulte [Aplicativos cliente](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     O **PassingDataBetweenForms** projeto é criado e adicionado ao **Solution Explorer**.  
  
## Criando a fonte de dados  
  
#### Para criar a fonte de dados  
  
1.  Sobre o **dados** menu, clique em **Show Data Sources**.  
  
2.  No **fontes de dados** janela, selecione **Add New Data Source** para iniciar o **Data Source Configuration Wizard**.  
  
3.  Selecione **banco de dados** sobre o **Escolher um tipo de fonte de dados** página e, em seguida, clique em **próximo**.  
  
4.  No **Escolher um modelo de banco de dados** Verifique **Dataset** for especificado e, em seguida, clique em **próximo**.  
  
5.  Sobre o **Escolha sua conexão de dados** página, siga um destes procedimentos:  
  
    -   Se uma conexão de dados para o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione\-o.  
  
         \- ou \-  
  
    -   Selecione **nova conexão** para iniciar o **Adicionar\/Modificar conexão** caixa de diálogo.  
  
6.  Se seu banco de dados exigir uma senha e se a opção para incluir dados confidenciais é ativada, selecione a opção e, em seguida, clique em **próximo**.  
  
7.  Clique em **próximo** sobre o **Salvar cadeia de conexão no arquivo de configuração do aplicativo** página.  
  
8.  Expanda o **tabelas** nó o **Choose your Database Objects** página.  
  
9. Selecione o **clientes** e **pedidos** tabelas e clique **Concluir**.  
  
     O **NorthwindDataSet** é adicionado ao seu projeto e o **clientes** e tabelas de pedidos aparecem no **fontes de dados** janela.  
  
## Criando o primeiro formulário \(Form1\)  
 Você pode criar uma grade associada a dados \(um <xref:System.Windows.Forms.DataGridView> controle\) arrastando o **clientes** nó a partir de **fontes de dados** window para o formulário.  
  
#### Para criar uma grade associada a dados no formulário  
  
-   Arraste principal **clientes** nó a partir de **fontes de dados** window para **Form1**.  
  
     Um <xref:System.Windows.Forms.DataGridView> e uma faixa de ferramenta \(<xref:System.Windows.Forms.BindingNavigator>\) para navegação em registros aparecem no **Form1**. Um [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> aparecem na bandeja de componentes.  
  
## Criando o segundo formulário \(Form2\)  
  
#### Para criar um segundo formulário para passar os dados  
  
1.  Do **projeto** menu, escolha **Adicionar formulário do Windows**.  
  
2.  Deixe o nome padrão de **Form2** e clique em **Add**.  
  
3.  Arraste principal **pedidos** nó a partir de **fontes de dados** window para **Form2**.  
  
     Um <xref:System.Windows.Forms.DataGridView> e uma faixa de ferramenta \(<xref:System.Windows.Forms.BindingNavigator>\) para navegação em registros aparecem no **Form2**. Um [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> aparecem na bandeja de componentes.  
  
4.  Excluir o **OrdersBindingNavigator** da bandeja de componentes.  
  
     O **OrdersBindingNavigator** desaparece da **Form2**.  
  
## Adicionar uma consulta TableAdapter ao Form2 para carregar pedidos do cliente selecionado no Form1  
  
#### Para criar uma consulta TableAdapter  
  
1.  Clique duas vezes o **NorthwindDataSet** arquivo **Solution Explorer**.  
  
2.  Clique com botão direito do **OrdersTableAdapter** e selecione **Add Query**.  
  
3.  Deixe a opção padrão **usar instruções SQL**, e, em seguida, clique em **próximo**.  
  
4.  Deixe a opção padrão **SELECT que retorna linhas**, e, em seguida, clique em **próximo**.  
  
5.  Adicione uma cláusula WHERE à consulta para retornar `Orders` com base no `CustomerID`. A consulta deve ser semelhante ao seguinte:  
  
    ```  
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry  
    FROM Orders   
    WHERE CustomerID = @CustomerID  
    ```  
  
    > [!NOTE]
    >  Verifique a sintaxe de parâmetro corretos para seu banco de dados. Por exemplo, no Microsoft Access, a cláusula WHERE seria algo como: `WHERE CustomerID = ?`.  
  
6.  Clique em **Avançar**.  
  
7.  Para o **preencher uma DataTablenome do método**, tipo `FillByCustomerID`.  
  
8.  Limpar o **retornar uma DataTable** opção e, em seguida, clique em **próximo**.  
  
9. Clique em **Concluir**.  
  
## Criando um método no Form2 para passar dados  
  
#### Para criar um método para passar dados  
  
1.  Clique com botão direito **Form2** e selecione **Exibir código** abrir **Form2** no **Editor de códigos**.  
  
2.  Adicione o seguinte código para **Form2** após o `Form2_Load` método:  
  
     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-cs[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]  
  
## Criando um método no Form1 para passar dados e exibir o Form2  
  
#### Para criar um método para passar dados para o Form2  
  
1.  Em **Form1**, clique com botão direito da grade de dados do cliente e, em seguida, clique em **propriedades**.  
  
2.  No **propriedades** janela, clique em **eventos**.  
  
3.  Clique duas vezes o **CellDoubleClick** eventos.  
  
     O editor de código é exibido.  
  
4.  Atualize a definição do método para coincidir com o exemplo a seguir:  
  
     [!code-cs[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]  
  
## Executar o aplicativo  
  
#### Para executar o aplicativo  
  
-   Pressione F5 para executar o aplicativo.  
  
-   Clique duas vezes em um registro de cliente no **Form1** abrir **Form2** com os pedidos do cliente.  
  
## Próximas etapas  
 Dependendo dos requisitos de aplicativo, há várias etapas que você talvez queira realizar após passar dados entre formulários. Alguns aprimoramentos que você poderia fazer neste passo a passo incluem:  
  
-   Editando o dataset, para adicionar ou remover objetos de banco de dados. Para obter mais informações, consulte [Criar e configurar conjuntos de dados](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
-   Adicionando funcionalidade para salvar dados no banco de dados. Para obter mais informações, consulte [Salvar dados no banco de dados](../data-tools/save-data-back-to-the-database.md).  
  
## Consulte também  
 [Associar controles dos Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)