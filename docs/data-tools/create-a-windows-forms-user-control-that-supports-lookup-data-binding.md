---
title: "Criar um controle de usu&#225;rio do Windows Forms que d&#225; suporte &#224; vincula&#231;&#227;o de dados de pesquisa | Microsoft Docs"
ms.custom: ""
ms.date: "11/15/2016"
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
  - "Classe LookupBindingPropertiesAttribute, exemplos"
  - "criação de controles de usuário [Visual Basic]"
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Criar um controle de usu&#225;rio do Windows Forms que d&#225; suporte &#224; vincula&#231;&#227;o de dados de pesquisa
Ao exibir dados em Windows Forms, você pode escolher os controles existentes da Toolbox, ou você pode criar controles personalizados se seu aplicativo requer funcionalidade não disponível nos controles padrão. Este passo a passo mostra como criar um controle que implementa o <xref:System.ComponentModel.LookupBindingPropertiesAttribute>. Controles que implementam o <xref:System.ComponentModel.LookupBindingPropertiesAttribute> pode conter três propriedades que podem ser vinculadas a dados. Tais controles são semelhantes a um <xref:System.Windows.Forms.ComboBox>.  
  
 Para obter mais informações sobre criação de controle, consulte [Desenvolvendo controles dos Windows Forms na hora de design](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md).  
  
 Ao criar controles para uso em cenários de ligação de dados, que você precisa implementar um dos seguintes atributos de vinculação de dados:  
  
|Uso do atributo de vinculação de dados|  
|--------------------------------------------|  
|Implementar o <xref:System.ComponentModel.DefaultBindingPropertyAttribute> em controles simples, como um <xref:System.Windows.Forms.TextBox>, que exibe uma única coluna \(ou propriedade\) de dados. Para obter mais informações, consulte [Criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados simples](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Implementar o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> nos controles, como um <xref:System.Windows.Forms.DataGridView>, que exibe listas \(ou tabelas\) de dados. Para obter mais informações, consulte [Criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados complexos](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implementar o <xref:System.ComponentModel.LookupBindingPropertiesAttribute> nos controles, como um <xref:System.Windows.Forms.ComboBox>, que exibe listas \(ou tabelas\) de dados, mas também precisa apresentar uma única coluna ou propriedade. \(Esse processo é descrito nesta página de explicação passo a passo.\)|  
  
 Este passo a passo cria um controle de pesquisa que associa dados de duas tabelas. Este exemplo usa o `Customers` e `Orders` tabelas do banco de dados de exemplo Northwind. O controle de pesquisa será associado para o `CustomerID` campo do `Orders` tabela. Ele usará este valor para pesquisar o `CompanyName` do `Customers` tabela.  
  
 Durante essa explicação passo a passo, você aprenderá como:  
  
-   Criar um novo **Windows Application**.  
  
-   Adicione um novo **controle de usuário** ao seu projeto.  
  
-   Crie visualmente o controle de usuário.  
  
-   Implementar o `LookupBindingProperty` atributo.  
  
-   Criar um conjunto de dados com o **Data Source Configuration Wizard**.  
  
-   Definir o **CustomerID** coluna o **pedidos** na tabela o **fontes de dados** janela para usar o novo controle.  
  
-   Crie um formulário para exibir dados no novo controle.  
  
## Pré-requisitos  
 Para concluir este passo a passo, você precisará de:  
  
-   Acesso ao banco de dados de exemplo Northwind.  
  
## Criando um aplicativo do Windows  
 A primeira etapa é criar um **Windows Application**.  
  
#### Para criar o novo projeto do Windows  
  
1.  No Visual Studio, do **arquivo** menu, crie um novo **projeto**.  
  
2.  Nomeie o projeto **LookupControlWalkthrough**.  
  
3.  Selecione **Windows Forms Application** e clique em **OK**.  
  
     O **LookupControlWalkthrough** projeto é criado e adicionado ao **Solution Explorer**.  
  
## Adicionando um controle de usuário ao projeto  
 Este passo a passo cria um controle de pesquisa de um **controle de usuário**, para adicionar um **controle de usuário** item para o **LookupControlWalkthrough** projeto.  
  
#### Para adicionar um controle de usuário ao projeto  
  
1.  Do **projeto** menu, selecione **Adicionar controle do usuário**.  
  
2.  Tipo `LookupBox` no **nome** área e clique **Add**.  
  
     O **LookupBox** controle é adicionado à **Solution Explorer** e abre no designer.  
  
## Criar o controle LookupBox  
  
#### Para criar o controle LookupBox  
  
-   Arraste um <xref:System.Windows.Forms.ComboBox> do **Toolbox** na superfície de design do controle de usuário.  
  
## Adicionando o atributo de vinculação de dados requerido  
 Para controles de pesquisa que suportam associação de dados, você pode implementar o <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.  
  
#### Para implementar o atributo LookupBindingProperties  
  
1.  Opção de **LookupBox** controle de exibição de código. \(No **exibição** menu, escolha **código**.\)  
  
2.  Substitua o código no `LookupBox` com o seguinte:  
  
     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-cs[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]  
  
3.  Do **criar** menu, escolha **Build Solution**.  
  
## Criando uma fonte de dados do banco de dados  
 Essa etapa cria uma fonte de dados usando o **Data Source Configuration Wizard** com base no `Customers` e `Orders` tabelas no banco de dados de exemplo Northwind. Você deve ter acesso ao banco de dados de exemplo Northwind para criar a conexão. Para obter informações sobre como configurar o banco de dados de exemplo Northwind, consulte [Install SQL Server sample databases](../data-tools/install-sql-server-sample-databases.md).  
  
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
  
8.  Selecione o `Customers` e `Orders` tabelas e clique **Concluir**.  
  
     O **NorthwindDataSet** é adicionado ao seu projeto e a `Customers` e `Orders` as tabelas aparecem no **fontes de dados** janela.  
  
## Definindo a coluna CustomerID da tabela Orders para usar o controle LookupBox  
 Dentro de **fontes de dados** janela você pode definir o controle a ser criado antes de arrastar itens para seu formulário.  
  
#### Para definir a coluna CustomerID para associar ao controle LookupBox  
  
1.  Abra **Form1** no designer.  
  
2.  Expanda o **clientes** nó o **fontes de dados** janela.  
  
3.  Expanda o **pedidos** nó \(no **clientes** abaixo do nó de **Fax** coluna\).  
  
4.  Clique na seta suspensa no **pedidos** nó e escolha **detalhes** na lista de controle.  
  
5.  Clique na seta suspensa no **CustomerID** coluna \(no **pedidos** nó\) e escolha **Personalizar**.  
  
6.  Selecione o **LookupBox** da lista de **controles associados** no **Opções de personalização da interface do usuário de dados** caixa de diálogo.  
  
7.  Clique em **OK**.  
  
8.  Clique na seta suspensa no **CustomerID** coluna e escolha **LookupBox**.  
  
## Adicionando controles ao formulário  
 Você pode criar os controles associados a dados arrastando itens do **fontes de dados** window para **Form1**.  
  
#### Para criar controles ligados a dados no Windows Form  
  
-   Arraste o **pedidos** nó a partir o **fontes de dados** window para o formulário do Windows e verifique o **LookupBox** controle é usado para exibir os dados no `CustomerID` coluna.  
  
## Vinculando o controle para pesquisar o CompanyName da tabela Customers  
  
#### Para configurar as associações de pesquisa  
  
-   Selecione principal **clientes** nó o **fontes de dados** janela e arraste\-a para a caixa de combinação caixa a **CustomerIDLookupBox** em **Form1**.  
  
     Isso configura a associação de dados para exibir o `CompanyName` do `Customers` tabela mantendo o `CustomerID` o valor do `Orders` tabela.  
  
## Executando o aplicativo  
  
#### Para executar o aplicativo  
  
-   Pressione F5 para executar o aplicativo.  
  
-   Navegue em alguns registros e verifique o `CompanyName` aparece no `LookupBox` controle.  
  
## Consulte também  
 [Associar controles dos Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)