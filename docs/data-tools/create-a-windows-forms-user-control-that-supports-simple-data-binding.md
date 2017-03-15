---
title: "Criar um controle de usu&#225;rio do Windows Forms que d&#225; suporte &#224; vincula&#231;&#227;o de dados simples | Microsoft Docs"
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
  - "controles personalizados [Visual Studio], janela fontes de dados"
  - "Janela fontes de dados, controles"
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Criar um controle de usu&#225;rio do Windows Forms que d&#225; suporte &#224; vincula&#231;&#227;o de dados simples
Ao exibir dados em formulários em aplicativos Windows, você pode escolher os controles existentes do **Toolbox**, ou você pode criar controles personalizados se seu aplicativo requer funcionalidade que não está disponível nos controles padrão. Este passo a passo mostra como criar um controle que implementa o <xref:System.ComponentModel.DefaultBindingPropertyAttribute>. Controles que implementam o <xref:System.ComponentModel.DefaultBindingPropertyAttribute> podem conter uma propriedade que pode ser associada a dados. Tais controles são semelhantes a um <xref:System.Windows.Forms.TextBox> ou <xref:System.Windows.Forms.CheckBox>.  
  
 Para obter mais informações sobre criação de controle, consulte [Desenvolvendo controles dos Windows Forms na hora de design](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md).  
  
 Ao criar controles para usam em cenários de associação de dados, você precisa implementar um dos seguintes atributos de associação de dados:  
  
|Uso do atributo de vinculação de dados|  
|--------------------------------------------|  
|Implementar o <xref:System.ComponentModel.DefaultBindingPropertyAttribute> em controles simples, como um <xref:System.Windows.Forms.TextBox>, que exibe uma única coluna \(ou propriedade\) de dados. \(Esse processo é descrito nesta página de explicação passo a passo.\)|  
|Implementar o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> nos controles, como um <xref:System.Windows.Forms.DataGridView>, que exibe listas \(ou tabelas\) de dados. Para obter mais informações, consulte [Criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados complexos](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implementar o <xref:System.ComponentModel.LookupBindingPropertiesAttribute> nos controles, como um <xref:System.Windows.Forms.ComboBox>, que exibe listas \(ou tabelas\) de dados mas também precisa apresentar uma única coluna ou propriedade. Para obter mais informações, consulte [Criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados de pesquisa](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 Este passo a passo cria um controle simples que exibe dados de uma única coluna em uma tabela. Este exemplo usa o `Phone` coluna o `Customers` tabela do banco de dados de exemplo Northwind. O controle de usuário simples exibirá números de telefone do cliente em um formato de número de telefone padrão usando um <xref:System.Windows.Forms.MaskedTextBox> e definindo a máscara para um número de telefone.  
  
 Durante essa explicação passo a passo, você aprenderá como:  
  
-   Criar um novo **Windows Application**.  
  
-   Adicione um novo **controle de usuário** ao seu projeto.  
  
-   Crie visualmente o controle de usuário.  
  
-   Implementar o `DefaultBindingProperty` atributo.  
  
-   Criar um conjunto de dados com o **Data Source Configuration Wizard**.  
  
-   Definir o **Phone** coluna o **fontes de dados** janela para usar o novo controle.  
  
-   Crie um formulário para exibir dados no novo controle.  
  
## Pré-requisitos  
 Para concluir este passo a passo, você precisará de:  
  
-   Acesso ao banco de dados de exemplo Northwind. Para obter mais informações, consulte [Como instalar bancos de dados de exemplo](../data-tools/how-to-install-sample-databases.md).  
  
## Criando um aplicativo do Windows  
 A primeira etapa é criar um **Windows Application**.  
  
#### Para criar o novo projeto do Windows  
  
1.  No Visual Studio, do **arquivo** menu, crie um novo **projeto**.  
  
2.  Nomeie o projeto **SimpleControlWalkthrough**.  
  
3.  Selecione **Windows Application** e clique em **OK**. Para obter mais informações, consulte [Aplicativos cliente](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     O **SimpleControlWalkthrough** projeto é criado e adicionado ao **Solution Explorer**.  
  
## Adicionando um controle de usuário ao projeto  
 Este passo a passo cria um controle de ligação de dados simples de uma **controle de usuário**, para adicionar um **controle de usuário** item para o **SimpleControlWalkthrough** projeto.  
  
#### Para adicionar um controle de usuário ao projeto  
  
1.  Do **projeto** menu, escolha **Adicionar controle do usuário**.  
  
2.  Tipo de `PhoneNumberBox` na área nome e clique **Add**.  
  
     O **PhoneNumberBox** controle é adicionado à **Solution Explorer** e abre no designer.  
  
## Criando o controle PhoneNumberBox  
 Este passo a passo expande existente <xref:System.Windows.Forms.MaskedTextBox> para criar o `PhoneNumberBox` controle.  
  
#### Para criar o controle PhoneNumberBox  
  
1.  Arraste um <xref:System.Windows.Forms.MaskedTextBox> do **Toolbox** na superfície de design do controle de usuário.  
  
2.  Selecione a marca inteligente no <xref:System.Windows.Forms.MaskedTextBox> apenas arrastando e escolha **Definir máscara**.  
  
3.  Selecione **telefone** no **máscara de entrada** caixa de diálogo e clique em **OK** para configurar a máscara.  
  
## Adicionando o atributo de vinculação de dados requerido  
 Para simples controles que suportam associação de dados, implemente o <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.  
  
#### Para implementar o atributo DefaultBindingProperty  
  
1.  Opção de `PhoneNumberBox` controle de exibição de código. \(No **exibição** menu, escolha **código**.\)  
  
2.  Substitua o código no `PhoneNumberBox` com o seguinte:  
  
     [!code-cs[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]  
  
3.  Do **criar** menu, escolha **Build Solution**.  
  
## Criando uma fonte de dados do banco de dados  
 Esta etapa usa o **Data Source Configuration Wizard** para criar uma fonte de dados com base no `Customers` tabela no banco de dados de exemplo Northwind. Você deve ter acesso ao banco de dados de exemplo Northwind para criar a conexão. Para obter informações sobre como configurar o banco de dados de exemplo Northwind, consulte [Como instalar bancos de dados de exemplo](../data-tools/how-to-install-sample-databases.md).  
  
#### Para criar a fonte de dados  
  
1.  Sobre o **dados** menu, clique em **Show Data Sources**.  
  
2.  No **fontes de dados** janela, selecione **Add New Data Source** para iniciar o **Data Source Configuration Wizard**.  
  
3.  Selecione **banco de dados** sobre o **Escolher um tipo de fonte de dados** página e, em seguida, clique em **próximo**.  
  
4.  Sobre o **Escolha sua conexão de dados** página faça o seguinte:  
  
    -   Se uma conexão de dados para o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione\-o.  
  
         Ou  
  
    -   Selecione **nova conexão** para iniciar o **Adicionar\/Modificar conexão** caixa de diálogo.  
  
5.  Se seu banco de dados exigir uma senha, selecione a opção para incluir dados confidenciais e, em seguida, clique em **próximo**.  
  
6.  Clique em **próximo** sobre o **Salvar cadeia de conexão no arquivo de configuração do aplicativo** página.  
  
7.  Expanda o **tabelas** nó o **Choose your Database Objects** página.  
  
8.  Selecione o `Customers` da tabela e, em seguida, clique em **Concluir**.  
  
     O **NorthwindDataSet** é adicionado ao seu projeto e o `Customers` tabela aparece no **fontes de dados** janela.  
  
## Definir a coluna telefone para usar o controle PhoneNumberBox  
 Dentro de **fontes de dados** janela você pode definir o controle a ser criado antes de arrastar itens para seu formulário.  
  
#### Para definir a coluna telefone para associar ao controle PhoneNumberBox  
  
1.  Abra **Form1** no designer.  
  
2.  Expanda o **clientes** nó o **fontes de dados** janela.  
  
3.  Clique na seta suspensa no **clientes** nó e escolha **detalhes** na lista de controle.  
  
4.  Clique na seta suspensa no **Phone** coluna e escolha **Personalizar**.  
  
5.  Selecione o **PhoneNumberBox** da lista de **controles associados** no **Opções de personalização da interface do usuário de dados** caixa de diálogo.  
  
6.  Clique na seta suspensa no **Phone** coluna e escolha **PhoneNumberBox**.  
  
## Adicionando controles ao formulário  
 Você pode criar os controles associados a dados arrastando itens do **fontes de dados** window para o formulário.  
  
#### Para criar controles ligados a dados no formulário  
  
-   Arraste principal **clientes** nó a partir o **fontes de dados** window para o formulário e verifique o `PhoneNumberBox` controle é usado para exibir os dados no `Phone` coluna.  
  
     Controles ligados a dados com rótulos descritivos aparecem no formulário, juntamente com uma faixa de ferramenta \(<xref:System.Windows.Forms.BindingNavigator>\) para navegação em registros. Um [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> aparecem na bandeja de componentes.  
  
## Executando o aplicativo  
  
#### Para executar o aplicativo  
  
-   Pressione F5 para executar o aplicativo.  
  
## Próximas etapas  
 Dependendo dos requisitos de aplicativo, há várias etapas que você pode desejar executar depois de criar um controle que suporta ligação de dados. Algumas das próximas etapas típicas incluem:  
  
-   Colocar os controles personalizados em uma biblioteca de controle para que você possa reutilizá\-los em outros aplicativos.  
  
-   Criando controles que suportam cenários de vinculação de dados mais complexos. Para obter mais informações, consulte [Criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados complexos](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) e [Criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados de pesquisa](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## Consulte também  
 [Associar controles dos Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Como definir o controle a ser criado quando arrastado da janela Fontes de Dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)