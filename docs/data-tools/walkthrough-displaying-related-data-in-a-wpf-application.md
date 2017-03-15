---
title: "Instru&#231;&#245;es passo a passo: exibindo dados relacionados em um aplicativo WPF | Microsoft Docs"
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
  - "associação de dados WPF [Visual Studio], explicações passo a passo"
  - "WPF Designer, associação de dados"
  - "WPF, associação de dados no Visual Studio"
ms.assetid: 5c48f188-e9c4-40a6-97d9-67cdb2f90127
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Instru&#231;&#245;es passo a passo: exibindo dados relacionados em um aplicativo WPF
Em essa explicação passo a passo, você criará um aplicativo WPF que exibe dados de tabelas de banco de dados que têm um relacionamento pai\/filho.  Os dados são encapsulados nas entidades em um modelo de dados de entidade.  A entidade pai contém informações da visão geral para um conjunto de pedidos.  Cada propriedade de esse objeto é associada a um outro controle no aplicativo.  A entidade filho contém detalhes para cada pedido.  Este dataset é associado a um controle de <xref:System.Windows.Controls.DataGrid> .  
  
 Essa explicação passo a passo mostra as seguintes tarefas:  
  
-   Criando um aplicativo WPF e um modelo de dados de entidade que é gerado de dados no banco de dados de exemplo AdventureWorksLT.  
  
-   Criando um conjunto de controles associados a dados que exibem informações da visão geral para um conjunto de pedidos.  Você cria controles arrastando uma entidade pai da janela de **Fontes de Dados** a **o WPF designer**.  
  
-   Criando um controle de <xref:System.Windows.Controls.DataGrid> que exibe detalhes relacionadas para cada pedido selecionado.  Você cria controles arrastando um objeto filho da janela de **Fontes de Dados** a uma janela em **o WPF designer**.  
  
     [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Pré-requisitos  
 Para completar este passo\-a\-passo, são necessários os seguintes componentes:  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Acesso a uma instância do SQL Server em execução ou SQL Server Express que tenha o banco de dados de exemplo AdventureWorksLT anexou\-lhe.  Você pode baixar o banco de dados AdventureWorksLT de [site de CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  
  
 O conhecimento prévio dos seguintes conceitos também é útil, mas não necessário para concluir a explicação passo a passo:  
  
-   Modelos de dados de entidade e a estrutura de entidade ADO.NET.  Para mais informações, consulte [Visão geral do Entity Framework](../Topic/Entity%20Framework%20Overview.md).  
  
-   Trabalhando com o designer WPF.  Para mais informações, consulte [WPF e Silverlight Designer Overview](http://msdn.microsoft.com/pt-br/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
-   O WPF associação de dados.  Para obter mais informações, consulte: [Visão geral da vinculação de dados](../Topic/Data%20Binding%20Overview.md).  
  
## Criando o projeto  
 Crie um novo projeto WPF exibir registros de pedidos.  
  
#### Para criar um novo projeto WPF  
  
1.  Inicie o Visual Studio.  
  
2.  No menu **File**, aponte para **New**, e em seguida, clique em **Project**.  
  
3.  Expanda **Visual C\#** ou **Visual Basic**, selecione **Janelas**.  
  
4.  Certifique\-se de que **o .NET Framework 4** está selecionado na caixa de combinação na parte superior da caixa de diálogo.  O controle de <xref:System.Windows.Controls.DataGrid> que você usa em este passo\-a\-passo está disponível somente no .NET Framework 4.  
  
5.  Selecione o modelo de projeto de **Aplicativo WPF** .  
  
6.  Em a caixa de **Nome** , digite `AdventureWorksOrdersViewer`.  
  
7.  Clique em **OK**.  
  
     O Visual Studio cria o projeto de `AdventureWorksOrdersViewer` .  
  
## Criando um modelo de dados de entidade para o aplicativo  
 Antes de poder criar controles associados a dados, você deve definir um modelo de dados para seu aplicativo e o adiciona à janela de **Fontes de Dados** .  Em este passo\-a\-passo, o modelo de dados é um modelo de dados de entidade.  
  
#### Para criar um modelo de dados de entidade  
  
1.  Em o menu de **Dados** , clique em **Adicionar nova fonte de dados** para abrir **Assistente para Configuração de Fonte de Dados**.  
  
2.  Em a página de **Escolher um Tipo de Fonte de Dados** , clique em **Banco de Dados**, e clique em **Avançar**.  
  
3.  Em a página de **Escolha um modelo de banco de dados** , clique em **Modelo de dados de entidade**, e clique em **Avançar**.  
  
4.  Em a página de **Escolha o conteúdo modelo** , clique em **Gere de banco de dados**, e clique em **Avançar**.  
  
5.  Em a página de **Escolha a Conexão de Dados** , siga um de estes procedimentos:  
  
    -   Se uma conexão de dados ao banco de dados de exemplo AdventureWorksLT está disponível na lista suspensa, selecione.  
  
         \-  ou  \-  
  
    -   Clique **Nova conexão** e criar uma conexão para o banco de dados AdventureWorksLT.  
  
     Certifique\-se de que a opção de **Salvar configurações de conexão de entidade em App.Config como** esteja selecionada, e clique em **Avançar**.  
  
6.  Em a página de **Escolher Objetos do Banco de Dados** , expanda **Tabelas**, selecione as tabelas a seguir:  
  
    -   **SalesOrderDetail**  
  
    -   **SalesOrderHeader**  
  
7.  Clique em **Concluir**.  
  
8.  Crie o projeto.  
  
## Criando controles associados a dados que exibem os pedidos  
 Criar controles que exibem registros de entidade arrastando a ordem de `SalesOrderHeaders` de **Fontes de Dados** janela do WPF designer.  
  
#### Para criar controles associados a dados que exibem registros de pedidos  
  
1.  Em **Gerenciador de Soluções**, clique duas vezes em MainWindow.xaml.  
  
     A janela é aberta no WPF designer.  
  
2.  Editar o XAML para que as propriedades de **Altura** e de **Largura** são definidas como 800  
  
3.  Em a janela de **Fontes de Dados** , clique no menu drop\-down para o nó de **SalesOrderHeaders** e selecione **Detalhes**.  
  
4.  Expanda o nó de **SalesOrderHeaders** .  
  
5.  Clique no menu suspenso próximo de **SalesOrderID** e selecione **ComboBox**.  
  
6.  Para cada um dos nós filho do nó de **SalesOrderHeaders** , clique no menu suspenso após o nó e selecione **Nenhum**:  
  
    -   **RevisionNumber**  
  
    -   **OnlineOrderFlag**  
  
    -   **ShipToAddressID**  
  
    -   **BillToAddressID**  
  
    -   **CreditCardApprovalCode**  
  
    -   **Subtotal**  
  
    -   **TaxAmt**  
  
    -   **Frete**  
  
    -   **rowguid**  
  
    -   **ModifiedDate**  
  
     Esta ação impede que o Visual Studio criar controles associados a dados para esses nós na próxima etapa.  Para esta explicação passo a passo, presume\-se que o usuário final não precisa consultar esses dados.  
  
7.  De a janela de **Fontes de Dados** , arraste o nó de **SalesOrderHeaders** a janela em **o WPF designer**.  
  
     O Visual Studio gera XAML que cria um conjunto de controles associados a dados no entidade de **SalesOrderHeaders** , e o código que carrega os dados.  Para obter mais informações sobre o XAML e código gerado, consulte [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
8.  Em o designer, clique na caixa de combinação ao lado do rótulo de **Identificação de ordem de venda** .  
  
9. Em a janela de **Propriedades** , selecione a caixa de seleção próxima à propriedade de **IsReadOnly** .  
  
## Criar um DataGrid que exibe a ordem detalha  
 Crie um controle de <xref:System.Windows.Controls.DataGrid> que exibe detalhes do pedido arrastando a entidade de `SalesOrderDetails` de **Fontes de Dados** janela do WPF designer.  
  
#### Para criar um DataGrid que exibe os detalhes do pedido  
  
1.  Em a janela de **Fontes de Dados** , localize o nó de **SalesOrderDetails** que é um filho do nó de **SalesOrderHeaders** .  
  
    > [!NOTE]
    >  Há também um nó de **SalesOrderDetails** que é um ponto de nó de **SalesOrderHeaders** .  Certifique\-se de que você selecionar o nó filho do nó de **SalesOrderHeaders** .  
  
2.  Expanda o nó filho de **SalesOrderDetails** .  
  
3.  Para cada um dos nós filho do nó de **SalesOrderDetails** , clique no menu suspenso após o nó e selecione **Nenhum**:  
  
    -   **SalesOrderID**  
  
    -   **SalesOrderDetailID**  
  
    -   **rowguid**  
  
    -   **ModifiedDate**  
  
     Esta ação impede que o Visual Studio inclui esses dados no controle de <xref:System.Windows.Controls.DataGrid> que você cria na próxima etapa.  Para esta explicação passo a passo, presume\-se que o usuário final não precisa consultar esses dados.  
  
4.  De a janela de **Fontes de Dados** , arraste o nó filho de **SalesOrderDetails** a janela em **o WPF designer**.  
  
     O Visual Studio gera XAML para definir um novo controle associado a dados de <xref:System.Windows.Controls.DataGrid> , e o controle aparece no designer.  Visual Studio também atualiza o método gerado de `GetSalesOrderHeadersQuery` no arquivo code\-behind para incluir os dados no entidade de **SalesOrderDetails** .  
  
## Testando o aplicativo  
 Compilar e executar o aplicativo para verificar que exibe registros de pedidos.  
  
#### Para testar o aplicativo  
  
1.  Pressione **F5**.  
  
     As compilações e o é executado do aplicativo.  Verifique o seguinte:  
  
    -   a caixa de combinação de **Identificação de ordem de venda** exibe **71774**.  Este é a identificação de primeira ordem na entidade.  
  
    -   Para cada pedido que você seleciona na caixa combo **Identificação de ordem de venda** , informações detalhadas do pedido é exibido em <xref:System.Windows.Controls.DataGrid>.  
  
2.  Feche o aplicativo.  
  
## Próximas etapas  
 Após concluir essa explicação passo a passo, aprender a usar a janela de **Fontes de Dados** no Visual Studio para associar controles WPF para outros tipos de fontes de dados.  Para obter mais informações, consulte [Associar controles WPF a um WCF data service](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) e [Associar controles WPF a um conjunto de dados](../data-tools/bind-wpf-controls-to-a-dataset.md).  
  
## Consulte também  
 [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Exibir dados relacionados em aplicativos WPF](../data-tools/display-related-data-in-wpf-applications.md)