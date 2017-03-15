---
title: "Criar um controle de usu&#225;rio do Windows Forms que d&#225; suporte &#224; vincula&#231;&#227;o de dados complexos | Microsoft Docs"
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
  - "associação de dados, controles de usuário"
  - "associação de dados complexa"
  - "controles de usuário [Visual Studio], vinculação de dados complexos"
ms.assetid: c8f29c2b-b49b-4618-88aa-33b6105880b5
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Criar um controle de usu&#225;rio do Windows Forms que d&#225; suporte &#224; vincula&#231;&#227;o de dados complexos
Ao exibir dados em formulários em aplicativos Windows, você pode escolher os controles existentes do **Toolbox**, ou você pode criar controles personalizados se seu aplicativo requer funcionalidade que não está disponível nos controles padrão. Este passo a passo mostra como criar um controle que implementa o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. Controles que implementam o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> contêm um `DataSource` e `DataMember` propriedade que pode ser associada a dados. Tais controles são semelhantes a um <xref:System.Windows.Forms.DataGridView> ou <xref:System.Windows.Forms.ListBox>.  
  
 Para obter mais informações sobre criação de controle, consulte [Desenvolvendo controles dos Windows Forms na hora de design](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md).  
  
 Ao criar controles para uso em cenários de ligação de dados, você precisa implementar um dos seguintes atributos de associação de dados:  
  
|Uso do atributo de vinculação de dados|  
|--------------------------------------------|  
|Implementar o <xref:System.ComponentModel.DefaultBindingPropertyAttribute> em controles simples, como um <xref:System.Windows.Forms.TextBox>, que exibe uma única coluna \(ou propriedade\) de dados. Para obter mais informações, consulte [Criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados simples](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Implementar o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> nos controles, como um <xref:System.Windows.Forms.DataGridView>, que exibe listas \(ou tabelas\) de dados. \(Esse processo é descrito nesta página de explicação passo a passo.\)|  
|Implementar o <xref:System.ComponentModel.LookupBindingPropertiesAttribute> nos controles, como um <xref:System.Windows.Forms.ComboBox>, que exibe listas \(ou tabelas\) de dados mas também precisa apresentar uma única coluna ou propriedade. Para obter mais informações, consulte [Criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados de pesquisa](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 Este passo a passo cria um controle complexo que exibe linhas de dados de uma tabela. Este exemplo usa o `Customers` tabela do banco de dados de exemplo Northwind. O controle de usuário complexo exibirá a tabela clientes em um <xref:System.Windows.Forms.DataGridView> no controle personalizado.  
  
 Durante essa explicação passo a passo, você aprenderá como:  
  
-   Criar um novo **Windows Application**.  
  
-   Adicione um novo **controle de usuário** ao seu projeto.  
  
-   Crie visualmente o controle de usuário.  
  
-   Implementar o `ComplexBindingProperty` atributo.  
  
-   Criar um conjunto de dados com o [Assistente para Configuração da Fonte de Dados](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Definir o **clientes** tabela o [Janela Fontes de Dados](../Topic/Data%20Sources%20Window.md) para usar o novo controle complexo.  
  
-   Adicione o novo controle, arrastando\-o da **janela fontes de dados** para **Form1**.  
  
## Pré-requisitos  
 Para concluir este passo a passo, você precisará de:  
  
-   Acesso ao banco de dados de exemplo Northwind. Para obter mais informações, consulte [Como instalar bancos de dados de exemplo](../data-tools/how-to-install-sample-databases.md).  
  
## Criando um aplicativo do Windows  
 A primeira etapa é criar um **Windows Application**.  
  
#### Para criar o novo projeto do Windows  
  
1.  No Visual Studio, do **arquivo** menu, crie um novo **projeto**.  
  
2.  Nomeie o projeto **ComplexControlWalkthrough**.  
  
3.  Selecione **Windows Application** e clique em **OK**. Para obter mais informações, consulte [Aplicativos cliente](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     O **ComplexControlWalkthrough** projeto é criado e adicionado ao **Solution Explorer**.  
  
## Adicionando um controle de usuário ao projeto  
 Porque essa explicação passo a passo cria um controle complexo de ligação de dados de um **controle de usuário**, você deve adicionar um **controle de usuário** item ao projeto.  
  
#### Para adicionar um controle de usuário ao projeto  
  
1.  Do **projeto** menu, escolha **Adicionar controle do usuário**.  
  
2.  Tipo de **ComplexDataGridView** no **nome** área e clique **Add**.  
  
     O **ComplexDataGridView** controle é adicionado à **Solution Explorer** e abre no designer.  
  
## Criar o controle ComplexDataGridView  
 Esta etapa adiciona um <xref:System.Windows.Forms.DataGridView> ao controle de usuário.  
  
#### Para criar o controle ComplexDataGridView  
  
-   Arraste um <xref:System.Windows.Forms.DataGridView> do **Toolbox** na superfície de design do controle de usuário.  
  
## Adicionando o atributo de vinculação de dados requerido  
 Para controles de complexos que suportam associação de dados, você pode implementar o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>.  
  
#### Para implementar o atributo ComplexBindingProperties  
  
1.  Comutador de **ComplexDataGridView** controle de exibição de código. \(No **exibição** menu, selecione **código**.\)  
  
2.  Substitua o código no `ComplexDataGridView` com o seguinte:  
  
     [!code-cs[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]  
  
3.  Do **criar** menu, escolha **Build Solution**.  
  
## Criando uma fonte de dados do banco de dados  
 Esta etapa usa o **Data Source Configuration Wizard** para criar uma fonte de dados com base no `Customers` tabela no banco de dados de exemplo Northwind. Você deve ter acesso ao banco de dados de exemplo Northwind para criar a conexão. Para obter informações sobre como configurar o banco de dados de exemplo Northwind, consulte [Install SQL Server sample databases](../data-tools/install-sql-server-sample-databases.md).  
  
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
  
8.  Selecione o `Customers` da tabela e, em seguida, clique em **Concluir**.  
  
     O **NorthwindDataSet** é adicionado ao seu projeto e o `Customers` tabela aparece no **fontes de dados** janela.  
  
## Configurando a tabela clientes para usar o controle ComplexDataGridView  
 Dentro de **fontes de dados** janela você pode definir o controle a ser criado antes de arrastar itens para seu formulário.  
  
#### Para definir a tabela clientes para associar ao controle ComplexDataGridView  
  
1.  Abra **Form1** no designer.  
  
2.  Expanda o **clientes** nó o **fontes de dados** janela.  
  
3.  Clique na seta suspensa no **clientes** nó e escolha **Personalizar**.  
  
4.  Selecione o **ComplexDataGridView** da lista de **controles associados** no **Opções de personalização da interface do usuário de dados** caixa de diálogo.  
  
5.  Clique na seta suspensa no `Customers` da tabela e escolha **ComplexDataGridView** na lista de controle.  
  
## Adicionando controles ao formulário  
 Você pode criar os controles associados a dados arrastando itens do **fontes de dados** window para seu formulário.  
  
#### Para criar controles ligados a dados no formulário  
  
-   Arraste principal **clientes** nó a partir de **fontes de dados** window para o formulário e verifique o **ComplexDataGridView** controle é usado para exibir os dados da tabela.  
  
## Executando o aplicativo  
  
#### Para executar o aplicativo  
  
-   Pressione F5 para executar o aplicativo.  
  
## Próximas etapas  
 Dependendo dos requisitos de aplicativo, há várias etapas que você pode desejar executar depois de criar um controle que oferece suporte a vinculação de dados. Algumas das próximas etapas típicas incluem:  
  
-   Colocar os controles personalizados em uma biblioteca de controle para que você possa reutilizá\-los em outros aplicativos.  
  
-   Criando controles que suportam cenários de pesquisa. Para obter mais informações, consulte [Criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados de pesquisa](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## Consulte também  
 [Associar controles dos Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Como definir o controle a ser criado quando arrastado da janela Fontes de Dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Controles de Windows Forms](../Topic/Windows%20Forms%20Controls.md)