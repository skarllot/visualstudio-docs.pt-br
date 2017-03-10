---
title: "Associar controles WPF a um WCF data service | Microsoft Docs"
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
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
caps.latest.revision: 40
caps.handback.revision: 38
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Associar controles WPF a um WCF data service
Neste passo a passo, você criará um aplicativo WPF que contém controles de associação de dados.  Os controles estão associados a registros de clientes que são encapsulados em um [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].  Você também adicionará botões que os clientes podem usar para exibir e atualizar registros.  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Criando um Modelo de Dados de Entidade que é gerado a partir de dados no banco de dados de exemplo AdventureWorksLT.  
  
-   Criando um [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] que expõe os dados no Modelo de Dados de Entidade para um aplicativo WPF.  
  
-   Criando um conjunto de controles de associação de dados ao arrastar itens da janela **Fontes de Dados** para o WPF Designer.  
  
-   Criando botões que navegam para a frente e para trás nos registros de clientes.  
  
-   Criando um botão que salva as alterações dos dados nos controles para o [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] e a fonte de dados subjacente.  
  
     [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
-   Acesso a uma instância em execução do SQL Server ou SQL Server Express que tenha o banco de dados de exemplo AdventureWorksLT anexado a ele.  É possível baixar o banco de dados AdventureWorksLT no site do [CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  
  
 Conhecimento prévio dos conceitos a seguir também é útil, mas não é necessário para concluir o passo a passo:  
  
-   WCF Data Services.  Para obter mais informações, consulte [Visão Geral](../Topic/WCF%20Data%20Services%20Overview.md).  
  
-   Modelos de dados no [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)].  
  
-   Modelos de Dados de Entidade e o ADO.NET Entity Framework.  Para obter mais informações, consulte [Visão geral do Entity Framework](../Topic/Entity%20Framework%20Overview.md).  
  
-   Trabalhando com o WPF Designer.  Para obter mais informações, consulte [WPF e Silverlight Designer Overview](http://msdn.microsoft.com/pt-br/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
-   Associação de dados do WPF.  Para obter mais informações, consulte [Visão geral da vinculação de dados](../Topic/Data%20Binding%20Overview.md).  
  
## Criando o projeto de serviço  
 Comece este passo a passo criando um projeto para um [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].  
  
#### Para criar o projeto de serviço  
  
1.  Inicie o Visual Studio.  
  
2.  No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.  
  
3.  Expanda **Visual C\#** ou **Visual Basic** e selecione **Web**.  
  
4.  Selecione o modelo de projeto **Aplicativo Web ASP.NET**.  
  
5.  Na caixa **Nome**, digite `AdventureWorksService` e clique em **OK**.  
  
     O Visual Studio cria o projeto `AdventureWorksService`.  
  
6.  No **Gerenciador de Soluções**, clique com o botão direito do mouse em **Default.aspx** e selecione **Excluir**.  Este arquivo não é necessário neste passo a passo.  
  
## Criando um Modelo de Dados de Entidade para o serviço  
 Para expor os dados para um aplicativo usando um [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], você deve definir um modelo de dados para o serviço.  O [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] tem suporte a dois tipos de modelos de dados: Modelos de Dados de Entidade e modelos de dados personalizados definidos usando objetos CRL \(Common Language Runtime\) que implementam a interface <xref:System.Linq.IQueryable%601>.  Neste passo a passo, você criará um Modelo de Dados de Entidade para o modelo de dados.  
  
#### Para criar um Modelo de Dados de Entidade  
  
1.  No menu **Projeto**, clique em **Adicionar Novo Item**.  
  
2.  Na lista Modelos Instalados, clique em **Dados**, e selecione o item do projeto **Modelo de Dados de Entidade ADO.NET**.  
  
3.  Mude o nome para `AdventureWorksModel.edmx` e clique em **Adicionar**.  
  
     O **Assistente do Modelo de Dados de Entidade** será aberto.  
  
4.  Na página **Escolher Conteúdo do Modelo**, clique em **Gerar a partir do banco de dados** e em **Próximo**.  
  
5.  Na página **Escolha a Conexão de Dados**, selecione uma das seguintes opções:  
  
    -   Se uma conexão de dados com o banco de dados de exemplo AdventureWorksLT estiver disponível na lista suspensa, selecione\-a.  
  
         \-ou\-  
  
    -   Clique em **Nova Conexão** e crie uma conexão com o banco de dados AdventureWorksLT.  
  
6.  Na página **Escolha a Conexão de Dados**, verifique se a opção **Salvar configurações de conexão de entidade em App.Config como** está selecionada e clique em **Próximo**.  
  
7.  Na página **Escolher Objetos do Banco de Dados**, expanda **Tabelas** e selecione a tabela **SalesOrderHeader**.  
  
8.  Clique em **Finalizar**.  
  
## Criando o serviço  
 Crie um [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] para expor os dados no Modelo de Dados de Entidade para um aplicativo WPF.  
  
#### Para criar o serviço  
  
1.  No menu **Projeto**, selecione **Adicionar Novo Item**.  
  
2.  Na lista Modelos Instalados, clique em **Web** e selecione o item de projeto **Serviço de Dados WCF**.  
  
3.  Na caixa **Nome**, digite `AdventureWorksService.svc` e clique em **Adicionar**.  
  
     O Visual Studio adiciona o `AdventureWorksService.svc` ao projeto.  
  
## Configurando o serviço  
 Você deve configurar o serviço para operar no Modelo de Dados de Entidades que você criou.  
  
#### Para configurar o serviço  
  
1.  No arquivo de código `AdventureWorks.svc`, substitua a declaração de classe `AdventureWorksService` pelo código a seguir.  
  
     [!code-cs[Data_WPFWCF#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_1.cs)]
     [!code-vb[Data_WPFWCF#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_1.vb)]  
  
     Esse código atualiza a classe `AdventureWorksService` para que ela derive de um <xref:System.Data.Services.DataService%601> que opera na classe de contexto do objeto `AdventureWorksLTEntities` em seu Modelo de Dados de Entidade.  Ele também atualiza o método `InitializeService` para permitir aos clientes do serviço acesso completo de leitura\/gravação à entidade `SalesOrderHeader`.  
  
2.  Crie o projeto e verifique se ele foi criado sem erros.  
  
## Criando o aplicativo cliente WPF  
 Para exibir os dados do [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], crie um novo aplicativo WPF com uma fonte de dados que se baseie no serviço.  A seguir neste passo a passo, você adicionará controles de associação de dados ao aplicativo.  
  
#### Para criar o aplicativo cliente WPF  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó da solução, clique em **Adicionar** e selecione **Novo Projeto**.  
  
2.  Na caixa de diálogo **Novo Projeto**, expanda **Visual Basic** ou **Visual C\#** e selecione **Windows**.  
  
3.  Selecione o modelo de projeto **Aplicativo WPF**.  
  
4.  Na caixa **Nome**, digite `AdventureWorksSalesEditor` e clique em **OK**.  
  
     O Visual Studio adiciona o projeto `AdventureWorksSalesEditor` à solução.  
  
5.  No menu **Dados**, clique em **Mostrar Fontes de Dados**.  
  
     A janela **Fontes de Dados** é aberta.  
  
6.  Na janela **Fontes de Dados**, clique em **Adicionar Nova Fonte de Dados**.  
  
     O **Assistente de Configuração de Fonte de Dados** é aberto.  
  
7.  Na página **Escolher um Tipo de Fonte de Dados** do assistente, selecione **Serviço** e clique em **Próximo**.  
  
8.  Na caixa de diálogo **Adicionar Referência de Serviço**, clique em **Descobrir**.  
  
     O Visual Studio pesquisa a solução atual para os serviços disponíveis e acrescenta `AdventureWorksService.svc` à lista de serviços disponíveis na caixa **Serviços**.  
  
9. Na caixa **Namespace**, digite `AdventureWorksService`.  
  
10. Na caixa **Serviços**, clique em **AdventureWorksService.svc** e em **OK**.  
  
     O Visual Studio baixa as informações de serviço e retorna ao **Assistente de Configuração de Fonte de Dados**.  
  
11. Na página **Adicionar Referência de Serviço**, clique em **Concluir**.  
  
     O Visual Studio adiciona nós que representam os dados retornados pelo serviço à janela **Fontes de Dados**.  
  
## Definindo a interface do usuário da janela  
 Adicione vários botões à janela, modificando o XAML no WPF Designer.  A seguir neste passo a passo, você adicionará código que permite aos usuários exibir e atualizar registros de vendas usando esses botões.  
  
#### Para criar o layout da janela  
  
1.  No **Gerenciador de Soluções**, clique duas vezes em MainWindow.xaml.  
  
     A janela é aberta no WPF Designer.  
  
2.  Na exibição [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] do designer, adicione o seguinte código entre as marcas `<Grid>`:  
  
    ```  
    <Grid.RowDefinitions>  
        <RowDefinition Height="75" />  
        <RowDefinition Height="525" />  
    </Grid.RowDefinitions>  
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>  
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>  
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>  
    ```  
  
3.  Compile o projeto.  
  
## Criando os controles de associação de dados  
 Crie controles que exibem registros do cliente ao arrastar o nó `SalesOrderHeaders` da janela **Fontes de Dados** para o designer.  
  
#### Para criar os controles de associação de dados  
  
1.  Na janela **Fontes de Dados**, abra o menu da lista suspensa para o nó **SalesOrderHeaders** e selecione **Detalhes**.  
  
2.  Expanda o nó **SalesOrderHeaders**.  
  
3.  Neste exemplo, alguns campos não serão exibidos, portanto, clique no menu suspenso ao lado dos seguintes nós e selecione **Nenhum**:  
  
    -   **CreditCardApprovalCode**  
  
    -   **ModifiedDate**  
  
    -   **OnlineOrderFlag**  
  
    -   **RevisionNumber**  
  
    -   **rowguid**  
  
     Essa ação impede que o Visual Studio crie controles de associação de dados para esses nós na etapa seguinte.  Para este passo a passo, pressupõe\-se que o usuário final não precise ver esses dados.  
  
4.  Na janela **Fontes de Dados**, arraste o nó **SalesOrderHeaders** para a linha de grade sob a linha que contém os botões.  
  
     O Visual Studio gera XAML e código que criam um conjunto de controles associados a dados na tabela **Produto**.  Para obter mais informações sobre XAML e código, consulte [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
5.  No designer, clique na caixa de texto ao lado do rótulo de **ID do Cliente**.  
  
6.  Na janela **Propriedades**, marque a caixa de seleção ao lado da propriedade **IsReadOnly**.  
  
7.  Configure a propriedade **IsReadOnly** para cada uma das seguintes caixas de texto:  
  
    -   **Número da Ordem de Compra**  
  
    -   **ID da Ordem de Venda**  
  
    -   **Número da Ordem de Venda**  
  
## Carregar os Dados do Serviço  
 Use o objeto de proxy de serviço para carregar os dados de vendas do serviço e atribua os dados retornados à fonte de dados para <xref:System.Windows.Data.CollectionViewSource> na janela WPF.  
  
#### Para carregar os dados do serviço  
  
1.  No designer, clique duas vezes no texto onde se lê: **MainWindow** para criar o manipulador de eventos `Window_Loaded`.  
  
2.  Substitua o manipulador de eventos pelo código a seguir.  Substitua o endereço *localhost* neste código pelo endereço de host local no computador de desenvolvimento.  
  
     [!code-cs[Data_WPFWCF#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_2.cs)]
     [!code-vb[Data_WPFWCF#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_2.vb)]  
  
## Navegando nos registros de venda  
 Adicione o código que permite aos usuários percorrer os registros de vendas, usando os botões **\<** e **\>**.  
  
#### Para permitir que os usuários naveguem nos registros de vendas  
  
1.  No designer, clique duas vezes no botão **\<** na superfície da janela.  
  
     O Visual Studio abre o arquivo code\-behind e cria um novo manipulador de eventos `backButton_Click` para o evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
2.  Adicione o seguinte código ao manipulador de eventos `backButton_Click` gerado:  
  
     [!code-cs[Data_WPFWCF#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_3.cs)]
     [!code-vb[Data_WPFWCF#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_3.vb)]  
  
3.  Retorne ao designer e clique duas vezes no botão **\>**.  
  
     O Visual Studio abre o arquivo code\-behind e cria um novo manipulador de eventos `nextButton_Click` para o evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
4.  Adicione o seguinte código ao manipulador de eventos `nextButton_Click` gerado:  
  
     [!code-cs[Data_WPFWCF#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_4.cs)]
     [!code-vb[Data_WPFWCF#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_4.vb)]  
  
## Salvando alterações em registros de vendas  
 Adicione o código que permite aos usuários visualizar e salvar as alterações em registros de vendas ao usar o botão **Salvar alterações**.  
  
#### Para adicionar a capacidade de salvar as alterações em registros de vendas  
  
1.  No designer, clique duas vezes no botão **Salvar Alterações**.  
  
     O Visual Studio abre o arquivo code\-behind e cria um novo manipulador de eventos `saveButton_Click` para o evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
2.  Adicione o seguinte código ao manipulador de eventos do `saveButton_Click`.  
  
     [!code-cs[Data_WPFWCF#5](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_5.cs)]
     [!code-vb[Data_WPFWCF#5](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_5.vb)]  
  
## Testando o aplicativo  
 Compile e execute o aplicativo para verificar se é possível exibir e atualizar os registros do cliente.  
  
#### Para testar o aplicativo  
  
1.  No menu **Compilar**, clique em **Compilar Solução**.  Verifique se a solução é compilada sem erros.  
  
2.  Pressione **CTRL\+F5**.  
  
     O Visual Studio inicia o projeto **AdventureWorksService** sem depurá\-lo.  
  
3.  No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto **AdventureWorksSalesEditor**.  
  
4.  No menu de contexto, em **Depurar**, clique em **Iniciar nova instância**.  
  
     O aplicativo é executado.  Verifique o seguinte:  
  
    -   As caixas de texto exibem diferentes campos de dados a partir do primeiro registro de venda, que tem o ID de ordem de venda **71774**.  
  
    -   Você pode clicar nos botões **\>** ou **\<** para navegar em outros registros de vendas.  
  
5.  Em um dos registros de vendas, digite algum texto na caixa **Comentário** e clique em **Salvar alterações**.  
  
6.  Feche o aplicativo e depois inicie\-o novamente no Visual Studio.  
  
7.  Navegue até o registro de vendas que você alterou e verifique se a alteração persiste depois de fechar e reabrir o aplicativo.  
  
8.  Feche o aplicativo.  
  
## Próximas etapas  
 Depois de completar este passo a passo, você poderá realizar as seguintes tarefas relacionadas:  
  
-   Saiba como usar a janela **Fontes de Dados** no Visual Studio para associar controles do WPF a outros tipos de fontes de dados.  Para obter mais informações, consulte [Associar controles WPF a um conjunto de dados](../data-tools/bind-wpf-controls-to-a-dataset.md).  
  
-   Saiba como usar a janela **Fontes de Dados** no Visual Studio para exibir dados relacionados \(isto é, dados em uma relação pai\-filho\) em controles do WPF.  Para obter mais informações, consulte [Instruções passo a passo: exibindo dados relacionados em um aplicativo WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).  
  
## Consulte também  
 [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Associar controles WPF a um conjunto de dados](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [Visão Geral](../Topic/WCF%20Data%20Services%20Overview.md)   
 [Visão geral do Entity Framework](../Topic/Entity%20Framework%20Overview.md)   
 [WPF e Silverlight Designer Overview](http://msdn.microsoft.com/pt-br/570b7a5c-0c86-4326-a371-c9b63378fc62)   
 [Visão geral da vinculação de dados](../Topic/Data%20Binding%20Overview.md)