---
title: "Associar controles WPF a um conjunto de dados | Microsoft Docs"
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
  - "WPF, ligação de dados no Visual Studio"
  - "Associação de dados do WPF [Visual Studio], instruções passo a passo"
  - "Designer de WPF, associação de dados"
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
caps.latest.revision: 32
caps.handback.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Associar controles WPF a um conjunto de dados
Neste passo a passo, você criará um aplicativo WPF que contém controles de associação de dados.  Os controles são associados a registros de produto que são encapsulados em um conjunto de dados.  Você também adicionará botões para navegar pelos produtos e salvar alterações em registros de produtos.  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Criando um aplicativo WPF e um conjunto de dados gerado a partir de dados no banco de dados de exemplo AdventureWorksLT.  
  
-   Criando um conjunto de controles de associação de dados ao arrastar uma tabela de dados da janela **Fontes de Dados** para uma janela do WPF Designer.  
  
-   Criando botões que navegam para a frente e para trás nos registros de produtos.  
  
-   Criando um botão para salvar as alterações que os usuários fazem nos registros de produtos na tabela de dados e na fonte de dados subjacente.  
  
     [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
-   Acesso a uma instância em execução do SQL Server ou SQL Server Express que tenha o banco de dados de exemplo AdventureWorksLT anexado a ele.  É possível baixar o banco de dados AdventureWorksLT no site do [CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  
  
 Conhecimento prévio dos conceitos a seguir também é útil, mas não é necessário para concluir o passo a passo:  
  
-   Conjuntos de dados e TableAdapters.  Para obter mais informações, consulte [Ferramentas do conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) e [Visão geral de TableAdapter](../data-tools/tableadapter-overview.md).  
  
-   Trabalhando com o WPF Designer.  Para obter mais informações, consulte [WPF e Silverlight Designer Overview](http://msdn.microsoft.com/pt-br/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
-   Associação de dados do WPF.  Para obter mais informações, consulte [Visão geral da vinculação de dados](../Topic/Data%20Binding%20Overview.md).  
  
## Criando o Projeto  
 Crie um novo projeto WPF.  O projeto exibirá registros de produtos.  
  
#### Para criar o projeto  
  
1.  Inicie o Visual Studio.  
  
2.  No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.  
  
3.  Expanda **Visual Basic** ou **Visual C\#** e selecione **Windows**.  
  
4.  Selecione o modelo de projeto **Aplicativo WPF**.  
  
5.  Na caixa **Nome**, digite `AdventureWorksProductsEditor` e clique em **OK**.  
  
     O Visual Studio cria o projeto `AdventureWorksProductsEditor`.  
  
## Criando um conjunto de dados para o aplicativo  
 Antes de criar controles de associação de dados, você deve definir um modelo de dados para seu aplicativo e adicioná\-lo à janela **Fontes de Dados**.  Neste passo a passo, você criará um conjunto de dados para usar como modelo de dados.  
  
#### Para criar um conjunto de dados  
  
1.  No menu **Dados**, clique em **Mostrar Fontes de Dados**.  
  
     A janela **Fontes de Dados** é aberta.  
  
2.  Na janela **Fontes de Dados**, clique em **Adicionar Nova Fonte de Dados**.  
  
     O **Assistente de Configuração de Fonte de Dados** é aberto.  
  
3.  Na página **Escolher um Tipo de Fonte de Dados**, selecione **Banco de Dados** e clique em **Avançar**.  
  
4.  Na página **Escolher um Modelo de Banco de Dados**, selecione **Conjunto de Dados** e clique em **Avançar**.  
  
5.  Na página **Escolha a Conexão de Dados**, selecione uma das seguintes opções:  
  
    -   Se uma conexão de dados com o banco de dados de exemplo AdventureWorksLT estiver disponível na lista suspensa, selecione\-a e clique em **Próximo**.  
  
         \-ou\-  
  
    -   Clique em **Nova Conexão** e crie uma conexão com o banco de dados AdventureWorksLT.  
  
6.  Na página **Salvar a Cadeia de Conexão no Arquivo de Configuração do Aplicativo** marque a caixa de seleção **Sim, salvar a conexão como** e clique em **Próximo**.  
  
7.  Na página **Escolher Objetos do Banco de Dados**, expanda **Tabelas** e selecione a tabela **Produto \(SalesLT\)**.  
  
8.  Clique em **Finalizar**.  
  
     O Visual Studio adiciona um novo arquivo AdventureWorksLTDataSet.xsd ao projeto, e adiciona um item correspondente **AdventureWorksLTDataSet** à janela **Fontes de Dados**.  O arquivo AdventureWorksLTDataSet.xsd define um conjunto de dados tipado nomeado `AdventureWorksLTDataSet` e um TableAdapter nomeado `ProductTableAdapter`.  A seguir neste passo a passo, você usará o `ProductTableAdapter` para preencher o conjunto de dados com dados e salvar as alterações no banco de dados.  
  
9. Compile o projeto.  
  
## Editando o método de preenchimento padrão do TableAdapter  
 Para preencher o conjunto de dados com dados, use o método `Fill` do `ProductTableAdapter`.  Por padrão, o método `Fill` preenche o `ProductDataTable` no `AdventureWorksLTDataSet` com todas as linhas de dados da tabela Produto.  Você pode modificar esse método para retornar apenas um subconjunto das linhas.  Para este passo a passo, modifique o método `Fill` para retornar somente linhas de produtos com fotos.  
  
#### Para carregar as linhas de produtos que possuem fotos  
  
1.  No **Gerenciador de Soluções**, clique duas vezes no arquivo AdventureWorksLTDataSet.xsd.  
  
     O designer de conjunto de dados é aberto.  
  
2.  No designer, clique com o botão direito do mouse na consulta **Fill,GetData\(\)** e selecione **Configurar**.  
  
     O **Assistente de Configuração do TableAdapter** é aberto.  
  
3.  Na página **Insira uma Instrução SQL**, adicione a seguinte cláusula WHERE após a instrução `SELECT` na caixa de texto.  
  
    ```  
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'  
    ```  
  
4.  Clique em **Finalizar**.  
  
## Definindo a interface do usuário  
 Adicione vários botões à janela, modificando o XAML no WPF Designer.  A seguir neste passo a passo, você adicionará o código que permite aos usuários navegar e salvar alterações nos registros de produtos, usando esses botões.  
  
#### Para definir a interface do usuário da janela  
  
1.  No **Gerenciador de Soluções**, clique duas vezes em MainWindow.xaml.  
  
     A janela é aberta no WPF Designer.  
  
2.  Na exibição [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] do designer, adicione o seguinte código entre as marcas `<Grid>`:  
  
    ```  
    <Grid.RowDefinitions>  
        <RowDefinition Height="75" />  
        <RowDefinition Height="625" />  
    </Grid.RowDefinitions>  
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>  
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>  
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>  
    ```  
  
3.  Compile o projeto.  
  
## Criando controles de associação de dados  
 Crie controles que exibem registros do cliente ao arrastar a tabela `Produto` da janela **Fontes de Dados** para o WPF Designer.  
  
#### Para adicionar controles de associação de dados  
  
1.  Na janela **Fontes de Dados**, abra o menu da lista suspensa para o nó **Produto** e selecione **Detalhes**.  
  
2.  Expanda o nó **Produto**.  
  
3.  Neste exemplo, alguns campos não serão exibidos, portanto, clique no menu suspenso ao lado dos seguintes nós e selecione **Nenhum**:  
  
    -   ProductCategoryID  
  
    -   ProductModelID  
  
    -   ThumbnailPhotoFileName  
  
    -   rowguid  
  
    -   ModifiedDate  
  
4.  Clique no menu suspenso ao lado do nó **ThumbNailPhoto** e selecione **Imagem**.  
  
    > [!NOTE]
    >  Por padrão, todos os itens na janela **Fontes de Dados** que representam as imagens têm seu controle padrão definido como **Nenhum**.  Isso ocorre porque as imagens são armazenadas como matrizes de bytes em bancos de dados e as matrizes de bytes podem conter qualquer coisa, desde uma simples matriz de bytes até um arquivo executável de um aplicativo grande.  
  
5.  Na janela **Fontes de Dados**, arraste o nó **Produto** para a linha de grade sob a linha que contém os botões.  
  
     O Visual Studio gera XAML que define um conjunto de controles associados aos dados na tabela **Produto**.  Também gera um código que carrega os dados.  Para obter mais informações sobre XAML e código, consulte [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
6.  No designer, clique na caixa de texto ao lado do rótulo de **Identificação do Produto \(Product ID\)**.  
  
7.  Na janela **Propriedades**, marque a caixa de seleção ao lado da propriedade **IsReadOnly**.  
  
## Navegando nos registros do produto  
 Adicione o código que permite aos usuários percorrer os registros do produto ao usar os botões **\<** e **\>**.  
  
#### Para permitir que os usuários naveguem nos registros do produto  
  
1.  No designer, clique duas vezes no botão **\<** na superfície da janela.  
  
     O Visual Studio abre o arquivo code\-behind e cria um novo manipulador de eventos `backButton_Click` para o evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
2.  Modifique o manipulador de eventos `Window_Loaded` para que `ProductViewSource`, `AdventureWorksLTDataSet` e `AdventureWorksLTDataSetProductTableAdapter` fiquem fora do método e acessíveis a todo o formulário.  Só declare esses globais para o formulário, atribua\-os no manipulador de eventos `Window_Loaded` de forma semelhante ao seguinte:  
  
     [!CODE [Data_WPFDATASET#1](../CodeSnippet/VS_Snippets_ProTools/data_wpfdataset#1)]  
  
3.  Adicione o seguinte código ao manipulador de eventos do `backButton_Click`:  
  
     [!CODE [Data_WPFDATASET#2](../CodeSnippet/VS_Snippets_ProTools/data_wpfdataset#2)]  
  
4.  Retorne ao designer e clique duas vezes no botão **\>**.  
  
5.  Adicione o seguinte código ao manipulador de eventos do `nextButton_Click`:  
  
     [!CODE [Data_WPFDATASET#3](../CodeSnippet/VS_Snippets_ProTools/data_wpfdataset#3)]  
  
## Salvando alterações em registros de produtos  
 Adicione o código que permite aos usuários salvar alterações em registros de produtos ao usar o botão **Salvar alterações**.  
  
#### Para adicionar a capacidade de salvar as alterações em registros de produtos  
  
1.  No designer, clique duas vezes no botão **Salvar Alterações**.  
  
     O Visual Studio abre o arquivo code\-behind e cria um novo manipulador de eventos `saveButton_Click` para o evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
2.  Adicione o seguinte código ao manipulador de eventos do `saveButton_Click`:  
  
     [!CODE [Data_WPFDATASET#4](../CodeSnippet/VS_Snippets_ProTools/data_wpfdataset#4)]  
  
    > [!NOTE]
    >  Este exemplo usa o método `Save` do `TableAdapter` para salvar as alterações.  Isso ocorre neste passo a passo, porque apenas uma tabela de dados está sendo alterada.  Se for necessário salvar alterações em várias tabelas de dados, você pode também usar o método `UpdateAll` do `TableAdapterManager` que o Visual Studio gera com o seu conjunto de dados.  Para obter mais informações, consulte [Visão geral de TableAdapterManager](../Topic/TableAdapterManager%20Overview.md).  
  
## Testando o aplicativo  
 Crie e execute o aplicativo.  Verifique se você pode exibir e atualizar registros de produtos.  
  
#### Para testar o aplicativo  
  
1.  Pressione **F5**.  
  
     O aplicativo é compilado e executado.  Verifique o seguinte:  
  
    -   As caixas de texto exibem dados do primeiro registro do produto que tem uma foto.  A identificação deste produto é 713 e nome **Long\-Sleeve Logo Jersey, S**.  
  
    -   Você pode clicar nos botões **\>** ou **\<** para navegar em outros registros de produto.  
  
2.  Em um dos registros de produto, altere o valor **Tamanho** e clique em **Salvar Alterações**.  
  
3.  Feche o aplicativo e reinicie\-o pressionando **F5** no Visual Studio.  
  
4.  Navegue até o registro do produto que você alterou e verifique se a mudança persistiu.  
  
5.  Feche o aplicativo.  
  
## Próximas etapas  
 Depois de completar este passo a passo, você poderá realizar as seguintes tarefas relacionadas:  
  
-   Saiba como usar a janela **Fontes de Dados** no Visual Studio para associar controles do WPF a outros tipos de fontes de dados.  Para obter mais informações, consulte [Associar controles WPF a um WCF data service](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).  
  
-   Saiba como usar a janela **Fontes de Dados** no Visual Studio para exibir dados relacionados \(isto é, dados em uma relação pai\-filho\) em controles do WPF.  Para obter mais informações, consulte [Instruções passo a passo: exibindo dados relacionados em um aplicativo WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).  
  
## Consulte também  
 [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Ferramentas do conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [WPF e Silverlight Designer Overview](http://msdn.microsoft.com/pt-br/570b7a5c-0c86-4326-a371-c9b63378fc62)   
 [Visão geral da vinculação de dados](../Topic/Data%20Binding%20Overview.md)