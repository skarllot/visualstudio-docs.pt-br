---
title: "Instru&#231;&#245;es passo a passo: exibindo dados em um Windows Form | Microsoft Docs"
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
  - "dados [Visual Studio], exibindo em Windows Forms"
  - "associação de dados, Windows Forms"
  - "exibindo dados em formulários, explicações passo a passo"
  - "formulários, exibindo dados"
  - "Aplicativos do Windows, exibindo dados"
  - "Windows Forms, exibindo dados"
ms.assetid: f6e08c2c-c792-43de-adf3-3e52c0100225
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Instru&#231;&#245;es passo a passo: exibindo dados em um Windows Form
Um dos cenários mais comuns no desenvolvimento de aplicativos é exibir dados de um formulário em um aplicativo baseado no Windows.  Você pode exibir os dados de um formulário ao arrastar itens do [Janela Fontes de Dados](../Topic/Data%20Sources%20Window.md) para o formulário.  Este passo a passo cria um formulário simples que exibe dados de uma única tabela em vários controles individuais.  Este exemplo usa a tabela `Customers` do banco de dados de exemplo Northwind.  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
-   Criando um novo projeto de **Aplicativo do Windows**.  
  
-   Criando e configurando um conjunto de dados com o [Assistente para Configuração da Fonte de Dados](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Selecionando o controle a ser criado no formulário ao arrastar itens da janela **Fontes de Dados**.  Para obter mais informações, consulte [Como definir o controle a ser criado quando arrastado da janela Fontes de Dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Criando um controle de associação de dados ao arrastar itens da janela **Fontes de Dados** para seu formulário.  
  
## Pré-requisitos  
 Para concluir este passo a passo, você precisará de:  
  
-   Acesso ao banco de dados de exemplo Northwind.  Para obter mais informações, consulte [Como instalar bancos de dados de exemplo](../data-tools/how-to-install-sample-databases.md).  
  
## Criando o aplicativo do Windows  
 A primeira etapa é criar um projeto de **Aplicativo do Windows**.  
  
#### Para criar o novo projeto de Aplicativo do Windows  
  
1.  No menu **Arquivo**, crie um novo projeto.  
  
2.  Nomeie o projeto como `DisplayingDataonaWindowsForm`.  
  
3.  Selecione **Aplicativo do Windows** e clique em **OK**.  Para obter mais informações, consulte [Aplicativos cliente](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     O projeto **DisplayingDataonaWindowsForm** é criado e adicionado ao **Gerenciador de Soluções**.  
  
## Criando a Fonte de Dados  
 Esta etapa cria uma fonte de dados usando o **Assistente de Configuração de Fonte de Dados** com base na tabela `Customers` no banco de dados de exemplo Northwind.  É preciso ter acesso ao banco de dados de exemplo Northwind para criar a conexão.  Para obter informações sobre como configurar o banco de dados de exemplo Northwind, consulte [Como instalar bancos de dados de exemplo](../data-tools/how-to-install-sample-databases.md).  
  
#### Para criar a fonte de dados  
  
1.  No menu **Dados**, clique em **Mostrar Fontes de Dados**.  
  
2.  Na janela **Fontes de Dados**, selecione **Adicionar Nova Fonte de Dados** para iniciar o **Assistente de Configuração de Fonte de Dados**.  
  
3.  Selecione **Base de dados** na página **Escolher um Tipo de Fonte de Dados** e, em seguida, clique em **Próximo**.  
  
4.  Na página **Escolha a Conexão de Dados**, faça o seguinte:  
  
    -   Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione\-o.  
  
         \-ou\-  
  
    -   Selecione **Nova Conexão** para iniciar a caixa de diálogo **Adicionar\/Modificar Conexão**.  
  
5.  Se o banco de dados exigir uma senha, selecione a opção para incluir dados confidenciais e, em seguida, clique em **Próximo**.  
  
6.  Clique em **Avançar** na página **Salvar cadeia de caracteres de conexão no arquivo de configuração do aplicativo**.  
  
7.  Expanda o nó **Tabelas** na página **Escolher Objetos do Banco de Dados**.  
  
8.  Selecione a tabela **Clientes** e clique em **Concluir**.  
  
     O **NorthwindDataSet** é adicionado ao projeto e a tabela **Clientes** aparece na janela **Fontes de Dados**.  
  
## Configurando os controles a serem criados  
 Para este passo a passo, os dados estarão em um layout **Detalhes** em que os dados são exibidos em controles individuais.  \(A abordagem alternativa é o layout **Grade** padrão em que os dados são exibidos em um controle <xref:System.Windows.Forms.DataGridView>.\)  
  
#### Definir o tipo de remoção dos itens na Janela Fontes de Dados  
  
1.  Expanda o nó **Clientes** na janela **Fontes de Dados**.  
  
2.  Altere o descarte de tipo da tabela **Clientes** para **Detalhes** selecionando **Detalhes** na lista suspensa no nó **Clientes**.  Para obter mais informações, consulte [Como definir o controle a ser criado quando arrastado da janela Fontes de Dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
3.  Altere o tipo de descarte da coluna **CustomerID** para um rótulo selecionando **Rótulo** na lista de controle no nó **CustomerID**.  
  
## Criando o formulário  
 Crie controles de associação de dados arrastando itens da janela **Fontes de Dados** para seu formulário.  
  
#### Para criar controles de associação de dados no formulário  
  
-   Arraste o nó principal **Clientes** da janela **Fontes de Dados** para o formulário.  
  
     Os controles de associação de dados com rótulos descritivos são exibidos no formulário, juntamente com uma faixa de ferramentas \(<xref:System.Windows.Forms.BindingNavigator>\) para registros de navegação.  Um [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator> são exibidos na bandeja de componentes.  
  
## Testando o aplicativo  
  
#### Para executar o aplicativo  
  
-   Pressione F5.  
  
-   Navegue nos registros usando o controle <xref:System.Windows.Forms.BindingNavigator>.  
  
## Próximas etapas  
 Dependendo dos requisitos do aplicativo, existem várias etapas que você talvez queira realizar após criar um Windows Form de associação de dados.  Entre algumas das melhorias que você poderia fazer nessa explicação passo a passo estão:  
  
-   Adicionando funcionalidade de busca ao formulário.  Para obter mais informações, consulte [Como adicionar uma consulta parametrizada a um aplicativo dos Windows Forms](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md).  
  
-   Adicionar a funcionalidade para enviar atualizações de volta ao banco de dados.  Para obter mais informações, consulte [Instruções passo a passo: salvando dados em um banco de dados \(tabela única\)](../Topic/Walkthrough:%20Saving%20Data%20to%20a%20Database%20\(Single%20Table\).md).  
  
-   Adicionar a tabela `Orders` ao conjunto de dados, selecionando **Configurar DataSet com Assistente** na janela **Fontes de Dados**.  Em seguida, você pode adicionar controles que exibem os dados relacionados ao arrastar o nó **Pedidos** \(abaixo da coluna **Fax** dentro da tabela **Clientes**\) para o formulário.  Para obter mais informações, consulte [Como exibir dados relacionados em um Aplicativo do Windows Forms](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md).  
  
## Consulte também  
 [Instruções passo a passo de dados](../Topic/Data%20Walkthroughs.md)   
 [Associar controles dos Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Adicionar novas fontes de dados](../data-tools/add-new-data-sources.md)   
 [Visão geral de TableAdapter](../data-tools/tableadapter-overview.md)