---
title: "Instru&#231;&#245;es passo a passo: criando um aplicativo de dados de N camadas | Microsoft Docs"
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
  - "aplicativos de n camadas, criando"
  - "aplicativos de n camadas, explicações passo a passo"
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
caps.latest.revision: 48
caps.handback.revision: 48
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Instru&#231;&#245;es passo a passo: criando um aplicativo de dados de N camadas
Os aplicativos de dados de *N camadas* são aplicativos que acessam dados e são separados em várias *camadas* lógicas.  A separação de componentes de aplicativos em camadas discretas aumenta a capacidade de manutenção e a escalabilidade do aplicativo.  Isso é feito pela adoção com mais facilidade de novas tecnologias que podem ser aplicadas a uma única camada, sem precisar reprojetar toda a solução.  A arquitetura de N camadas inclui uma camada de apresentação, uma camada intermediária e uma camada de dados.  A camada intermediária geralmente inclui uma camada de acesso a dados, uma camada lógica de negócios e componentes compartilhados, tais como autenticação e validação.  A camada de dados inclui um banco de dados relacional.  Os aplicativos de N camadas geralmente armazenam informações confidenciais na camada de acesso a dados da camada intermediária para manter o isolamento de usuários finais que acessam a camada de apresentação.  Para obter mais informações, consulte [Visão geral de aplicativos de dados de N camadas](../data-tools/n-tier-data-applications-overview.md).  
  
 Uma maneira de separar as várias camadas em um aplicativo de N camadas é criar projetos discretos para cada camada que você deseja incluir em seu aplicativo.  Os conjuntos de dados digitados contêm uma propriedade `DataSet Project` que determina quais projetos o conjunto de dados gerado e o código `TableAdapter` devem acessar.  
  
 Esse passo a passo demonstra como separar o conjunto de dados e o código `TableAdapter` em projetos de bibliotecas de classes discretas usando o **Designer de Conjunto de Dados**.  Depois de separar o conjunto de dados e o código TableAdapter, você criará um serviço [Serviços do Windows Communication Foundation e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) a ser chamado na camada de acesso a dados.  Finalmente, você criará um aplicativo do Windows Forms como a camada de apresentação.  Essa camada acessa dados do serviço de dados.  
  
 Durante este passo a passo, você executará as seguintes etapas:  
  
-   Criar uma nova solução de N camadas que conterá vários projetos.  
  
-   Adicionar dois projetos de bibliotecas de classes na solução de N camadas.  
  
-   Criar um conjunto de dados tipado usando o **Assistente de Configuração de Fonte de Dados**.  
  
-   Separar o [TableAdapters](../Topic/TableAdapters.md) gerado e o código do conjunto de dados em projetos discretos.  
  
-   Criar um serviço do Windows Communication Foundation \(WCF\) a ser chamado na camada de acesso a dados.  
  
-   Criar funções no serviço para recuperar dados da camada de acesso a dados.  
  
-   Criar um aplicativo do Windows Forms para servir como a camada de apresentação.  
  
-   Criar controles do Windows Forms associados à fonte de dados.  
  
-   Gravar código para preencher as tabelas de dados.  
  
 ![link para vídeo](~/data-tools/media/playvideo.gif "PlayVideo") Para obter uma versão em vídeo deste tópico, consulte [Vídeo Como criar um aplicativo de dados de N camadas](http://go.microsoft.com/fwlink/?LinkId=115188).  
  
## Pré-requisitos  
 Para concluir esta explicação passo a passo, será necessário:  
  
-   Acesso ao banco de dados de exemplo Northwind.  Para obter mais informações, consulte [Como instalar bancos de dados de exemplo](../data-tools/how-to-install-sample-databases.md).  
  
## Criando a solução de N camadas e a biblioteca de classes para manter o conjunto de dados \(DataEntityTier\)  
 A primeira etapa deste passo a passo é criar uma solução e dois projetos de biblioteca de classes.  A primeira biblioteca de classes manterá o conjunto de dados \(a classe DataSet digitada gerada e DataTables, que manterá os dados do aplicativo\).  Este projeto é usado como a camada de entidade de dados do aplicativo e geralmente está localizada na camada intermediária.  O [Criando e editando conjuntos de dados tipados](../data-tools/creating-and-editing-typed-datasets.md) é usado para criar o conjunto de dados inicial e separar automaticamente o código nas duas bibliotecas de classes.  
  
> [!NOTE]
>  Não se esqueça de nomear o projeto e a solução corretamente antes de clicar em **OK**.  Isso facilitará a conclusão deste passo a passo.  
  
#### Para criar a solução de N camadas e a biblioteca de classes DataEntityTier  
  
1.  No menu **Arquivo**, crie um novo projeto.  
  
    > [!NOTE]
    >  O **Designer de Conjunto de Dados** tem suporte em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] e em projetos C\#.  Crie o novo projeto em uma dessas linguagens.  
  
2.  Na caixa de diálogo **Novo Projeto**, no painel **Tipos de projetos**, clique em **Windows**.  
  
3.  Clique no modelo **Biblioteca de Classes**.  
  
4.  Nomeie o projeto como DataEntityTier.  
  
5.  Nomeie a solução como NTierWalkthrough.  
  
6.  Clique em **OK**.  
  
     Uma solução NTierWalkthrough que contém o projeto DataEntityTier é criada e adicionada ao **Gerenciador de Soluções**.  
  
## Criando a biblioteca de classes para manter os TableAdapters \(DataAccessTier\)  
 A próxima etapa após a criação do projeto DataEntityTier é criar outro projeto de biblioteca de classes.  Esse projeto servirá para manter os `TableAdapter`s gerados e será chamado de *camada de acesso a dados* do aplicativo.  A camada de acesso a dados contém as informações necessárias para se conectar ao banco de dados e geralmente está localizada na camada intermediária.  
  
#### Para criar a nova biblioteca de classes para os TableAdapters  
  
1.  No menu **Arquivo**, adicione um novo projeto para a solução NTierWalkthrough.  
  
2.  Na caixa de diálogo **Novo Projeto**, no painel **Modelos**, clique em **Biblioteca de Classes**.  
  
3.  Nomeie o projeto como DataAccessTier e clique em **OK**.  
  
     O projeto DataAccessTier é criado e adicionado à solução NTierWalkthrough.  
  
## Criando o conjunto de dados  
 A próxima etapa é criar um conjunto de dados tipado.  Os conjuntos de dados tipado são criados com a classe do conjunto de dados \(incluindo as classes DataTables\) e as classes `TableAdapter` em um único projeto.  \(Todas as classes são geradas em um único arquivo.\) Quando você separa o conjunto de dados e os `TableAdapter`s em projetos diferentes, é a classe do conjunto de dados que é movida para o outro projeto, mantendo as classes `TableAdapter` no projeto original.  Portanto, crie o conjunto de dados no projeto que conterá, por fim, os `TableAdapter`s \(o projeto DataAccessTier\).  Você criará o conjunto de dados usando o **Assistente de Configuração de Fonte de Dados**.  
  
> [!NOTE]
>  É preciso ter acesso ao banco de dados de exemplo Northwind para criar a conexão.  Para obter informações sobre como configurar o banco de dados de exemplo Northwind, consulte [Como instalar bancos de dados de exemplo](../data-tools/how-to-install-sample-databases.md).  
  
#### Para criar o conjunto de dados  
  
1.  Clique em DataAccessTier em **Gerenciador de Soluções**.  
  
2.  No menu **Dados**, clique em **Mostrar Fontes de Dados**.  
  
3.  Na janela **Fontes de Dados**, clique em **Adicionar Nova Fonte de Dados** para iniciar o **Assistente de Configuração de Fonte de Dados**.  
  
4.  Na página **Escolher um Tipo de Fonte de Dados**, selecione **Banco de Dados** e clique em **Próximo**.  
  
5.  Na página **Escolha a Conexão de Dados**, execute uma das seguintes ações:  
  
     Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, clique nela.  
  
     \-ou\-  
  
     Selecione **Nova Conexão** para abrir a caixa de diálogo **Adicionar Conexão**.  
  
6.  Se o banco de dados exigir uma senha, selecione a opção para incluir dados confidenciais e, em seguida, clique em **Próximo**.  
  
    > [!NOTE]
    >  Se você escolheu um arquivo do banco de dados local \(em vez de se conectar ao SQL Server\), talvez seja perguntado se deseja adicionar o arquivo ao projeto.  Clique em **Sim** para adicionar o arquivo do banco de dados ao projeto.  
  
7.  Clique em **Próximo** na página **Salvar a Cadeia de Conexão no Arquivo de Configuração do Aplicativo**.  
  
8.  Expanda o nó **Tabelas** na página **Escolher Objetos do Banco de Dados**.  
  
9. Clique nas caixas de seleção das tabelas **Clientes** e **Pedidos** e, em seguida, clique em **Concluir**.  
  
     NorthwindDataSet é adicionado ao projeto DataAccessTier e aparece na janela **Fontes de Dados**.  
  
## Separando os TableAdapters do Conjunto de Dados  
 Depois de criar o conjunto de dados, separe a classe do conjunto de dados gerada a partir dos TableAdapters.  Você faz isso ao configurar a propriedade **Projeto do Conjunto de Dados** para o nome do projeto que armazenará a classe do conjunto de dados separada.  
  
#### Para separar os TableAdapters do Conjunto de Dados  
  
1.  Dê um clique duplo em **NorthwindDataSet.xsd** no **Gerenciador de Soluções** para abrir o conjunto de dados no **Designer do Conjunto de Dados**.  
  
2.  Clique em uma área vazia no designer.  
  
3.  Localize o nó **Projeto do Conjunto de Dados** na janela **Propriedades**.  
  
4.  Na lista **Projeto do Conjunto de Dados**, clique em **DataEntityTier**.  
  
5.  No menu **Compilar**, clique em **Compilar Solução**.  
  
 O conjunto de dados e os TableAdapters são separados em dois projetos de biblioteca de classes.  O projeto que continha originalmente todo o conjunto de dados \(DataAccessTier\) contém agora somente os TableAdapters.  O projeto atribuído à propriedade **Projeto do Conjunto de Dados** \(DataEntityTier\) contém o conjunto de dados tipado: NorthwindDataSet.Dataset.Designer.vb \(ou NorthwindDataSet.Dataset.Designer.cs\).  
  
> [!NOTE]
>  Quando você separa os conjuntos de dados e os TableAdapters \(configurando a propriedade **Projeto de Conjunto de Dados**\), as classes dos conjuntos de dados parciais existentes no projeto não são movidas automaticamente.  As classes parciais do conjunto de dados existentes devem ser movidas manualmente para o projeto do conjunto de dados.  
  
## Criando um novo aplicativo de serviço  
 Como este passo a passo demonstra como acessar a camada de acesso a dados usando um serviço WCF, crie um novo aplicativo de serviço WCF.  
  
#### Para criar um novo aplicativo de Serviço WCF  
  
1.  No menu **Arquivo**, adicione um novo projeto para a solução NTierWalkthrough.  
  
2.  Na caixa de diálogo **Novo Projeto**, no painel **Tipos de projetos**, clique em **WCF**.  No painel **Modelos**, clique em **Biblioteca de Serviços WCF**.  
  
3.  Nomeie o projeto como DataService e clique em **OK**.  
  
     O projeto DataService é criado e adicionado à solução NTierWalkthrough.  
  
## Criando métodos na camada de acesso a dados para retornar os dados de clientes e pedidos  
 O serviço de dados deve chamar dois métodos na camada de acesso a dados: GetCustomers e GetOrders.  Esses métodos retornarão as tabelas Clientes e Pedidos do Northwind.  Crie os métodos GetCustomers e GetOrders no projeto DataAccessTier.  
  
#### Para criar um método na camada de acesso a dados que retorna a tabela Clientes  
  
1.  Em **Gerenciador de Soluções**, clique duas vezes em NorthwindDataset.xsd para abrir o conjunto de dados no [Criando e editando conjuntos de dados tipados](../data-tools/creating-and-editing-typed-datasets.md).  
  
2.  Clique com o botão direito do mouse em CustomersTableAdapter e clique em **Adicionar Consulta** para abrir o [Editando TableAdapters](../data-tools/editing-tableadapters.md).  
  
3.  Na página **Escolher um Tipo de Comando**, mantenha o valor padrão de **Usar instruções SQL** e clique em **Próximo**.  
  
4.  Na página **Escolher um Tipo de Consulta**, mantenha o valor padrão de **SELECT que retorna linhas** e clique em **Próximo**.  
  
5.  Na página **Especifique uma instrução SQL SELECT**, mantenha a consulta padrão e clique em **Próximo**.  
  
6.  Na página **Escolher Métodos a Serem Gerados**, digite GetCustomers para o **Nome do método** na seção **Retornar uma DataTable**.  
  
7.  Clique em **Finalizar**.  
  
#### Para criar um método na camada de acesso a dados que retorna a tabela Pedidos  
  
1.  Clique com o botão direito do mouse em OrdersTableAdapter e clique em **Adicionar Consulta**.  
  
2.  Na página **Escolher um Tipo de Comando**, mantenha o valor padrão de **Usar instruções SQL** e clique em **Próximo**.  
  
3.  Na página **Escolher um Tipo de Consulta**, mantenha o valor padrão de **SELECT que retorna linhas** e clique em **Próximo**.  
  
4.  Na página **Especifique uma instrução SQL SELECT**, mantenha a consulta padrão e clique em **Próximo**.  
  
5.  Na página **Escolher Métodos a Serem Gerados**, digite GetOrders para o **Nome do método** na seção **Retornar uma DataTable**.  
  
6.  Clique em **Finalizar**.  
  
7.  No menu **Compilar**, clique em **Compilar Solução**.  
  
## Adicionando uma referência à entidade de dados e às camadas de acesso a dados para o serviço de dados  
 Como o serviço de dados requer informações do conjunto de dados e dos TableAdapters, adicione referências aos projetos DataEntityTier e DataAccessTier.  
  
#### Para adicionar referência aos serviço de dados  
  
1.  Clique com o botão direito do mouse em DataService no **Gerenciador de Soluções** e clique em **Adicionar Referência**.  
  
2.  Clique na guia **Projetos** na caixa de diálogo **Adicionar Referência**.  
  
3.  Escolha os projetos **DataAccessTier** e **DataEntityTier**.  
  
4.  Clique em **OK**.  
  
## Adicionando funções ao serviço para chamar os métodos GetCustomers e GetOrders na camada de acesso a dados  
 Agora que a camada de acesso a dados contém os métodos para retornar dados, crie métodos no serviço de dados para chamar os métodos na camada de acesso a dados.  
  
> [!NOTE]
>  Para projetos C\#, adicione uma referência ao assembly `System.Data.DataSetExtensions` para que o código a seguir seja compilado.  
  
#### Para criar as funções GetCustomers e GetOrders no serviço de dados  
  
1.  No projeto **DataService**, dê um clique duplo em IService1.vb ou IService1.cs.  
  
2.  Adicione o seguinte código no comentário **Adicionar suas operações de serviço aqui**:  
  
    ```vb#  
    <OperationContract()> _  
    Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable  
  
    <OperationContract()> _  
    Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable  
    ```  
  
    ```c#  
    [OperationContract]  
    DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers();  
  
    [OperationContract]  
    DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders();  
  
    ```  
  
3.  No projeto DataService, dê um clique duplo em Service1.vb \(ou Service1.cs\).  
  
4.  Adicione o seguinte código à classe Service1:  
  
    ```vb#  
    Public Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable Implements IService1.GetCustomers  
        Dim CustomersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter  
        Return CustomersTableAdapter1.GetCustomers()  
    End Function  
  
    Public Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable Implements IService1.GetOrders  
        Dim OrdersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter  
        Return OrdersTableAdapter1.GetOrders()  
    End Function  
    ```  
  
    ```c#  
    public DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers()  
    {  
        DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter  
             CustomersTableAdapter1  
            = new DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter();  
        return CustomersTableAdapter1.GetCustomers();  
  
    }  
    public DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders()  
    {  
        DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter  
             OrdersTableAdapter1  
            = new DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter();  
        return OrdersTableAdapter1.GetOrders();  
  
    }  
    ```  
  
5.  No menu **Compilar**, clique em **Compilar Solução**.  
  
## Criando uma camada de apresentação para exibir dados a partir do serviço de dados  
 Agora que a solução contém o serviço de dados que possui métodos chamados na camada de acesso a dados, crie outro projeto que será chamado no serviço de dados e apresente os dados aos usuários.  Neste passo a passo, crie um aplicativo do Windows Forms, o qual será a camada de apresentação do aplicativo de N camadas.  
  
#### Para criar o projeto da camada de apresentação  
  
1.  No menu **Arquivo**, adicione um novo projeto para a solução NTierWalkthrough.  
  
2.  Na caixa de diálogo **Novo Projeto**, no painel **Tipos de projetos**, clique em **Windows**.  No painel **Modelos**, clique em **Aplicativo do Windows Forms**.  
  
3.  Nomeie o projeto como PresentationTier e clique em **OK**.  
  
4.  O projeto PresentationTier é criado e adicionado à solução NTierWalkthrough.  
  
## Configurando o projeto PresentationTier como o projeto de inicialização  
 Como a camada de apresentação é o aplicativo cliente real usado para apresentar e interagir com os dados, você deve configurar o projeto PresentationTier para ser o projeto de inicialização.  
  
#### Para configurar o novo projeto de camada de apresentação como o projeto de inicialização  
  
-   Em **Gerenciador de Soluções**, clique com o botão direito do mouse em **PresentationTier** e clique em **Definir como Projeto de Inicialização**.  
  
## Adicionando referências à camada de apresentação  
 O aplicativo cliente PresentationTier requer uma referência de serviço para o serviço de dados a fim de acessar os métodos no serviço.  Além disso, uma referência ao conjunto de dados é necessária para permitir o compartilhamento de tipos pelo serviço WCF.  O código adicionado à classe do conjunto de dados parcial estará disponível na camada de apresentação somente após você permitir o compartilhamento de tipos por meio do serviço de dados.  Como você geralmente adiciona código como validação para os eventos de alteração de linha e coluna de uma tabela de dados, é provável que você queira acessar esse código a partir do cliente.  
  
#### Para adicionar uma referência à camada de apresentação  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito do mouse em PresentationTier e clique em **Adicionar Referência**.  
  
2.  Na caixa de diálogo **Adicionar Referência**, clique na guia **Projetos**.  
  
3.  Escolha **DataEntityTier** e clique em **OK**.  
  
#### Para adicionar uma referência de serviço à camada de apresentação  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito do mouse em PresentationTier e clique em **Adicionar Referência de Serviço**.  
  
2.  Na caixa de diálogo **Adicionar Referência de Serviço**, clique em **Descobrir**.  
  
3.  Escolha **Service1** e clique em **OK**.  
  
    > [!NOTE]
    >  Se você tiver vários serviços no computador atual, escolha o serviço criado anteriormente neste passo a passo \(o serviço que contém os métodos GetCustomers e GetOrders\).  
  
## Adicionando DataGridViews ao formulário para exibir os dados retornados pelo serviço de dados  
 Depois de adicionar a referência de serviço ao serviço de dados, a janela **Fontes de Dados** é preenchida automaticamente com os dados retornados pelo serviço.  
  
#### Para adicionar duas associações de dados DataGridViews ao formulário  
  
1.  No **Gerenciador de Soluções**, escolha o projeto PresentationTier.  
  
2.  Na janela **Fontes de Dados**, expanda **NorthwindDataSet** e localize o nó **Clientes**.  
  
3.  Arraste o nó **Clientes** sobre Form1.  
  
4.  Na janela **Fontes de Dados**, expanda o nó **Clientes** e localize o nó **Pedidos** relacionado \(o nó **Pedidos** aninhado no nó **Clientes**\).  
  
5.  Arraste o nó **Pedidos** relacionado sobre Form1.  
  
6.  Crie um manipulador de eventos `Form1_Load` ao clicar duas vezes em uma área vazia do formulário.  
  
7.  Adicione o seguinte código ao manipulador de eventos do `Form1_Load`.  
  
    ```vb#  
    Dim DataSvc As New ServiceReference1.Service1Client  
    NorthwindDataSet.Customers.Merge(DataSvc.GetCustomers)  
    NorthwindDataSet.Orders.Merge(DataSvc.GetOrders)  
    ```  
  
    ```c#  
    ServiceReference1.Service1Client DataSvc =   
        new ServiceReference1.Service1Client();  
    northwindDataSet.Customers.Merge(DataSvc.GetCustomers());  
    northwindDataSet.Orders.Merge(DataSvc.GetOrders());  
  
    ```  
  
## Aumentando o tamanho máximo da mensagem permitida pelo serviço  
 Como o serviço retorna dados das tabelas Clientes e Pedidos, o valor padrão para maxReceivedMessageSize não é grande o suficiente para manter os dados e deve ser ampliado.  Neste passo a passo, você alterará o valor para 6553600.  Você alterará o valor no cliente e isso atualizará automaticamente a referência de serviço.  
  
> [!NOTE]
>  O menor tamanho padrão se destina a limitar a exposição para ataques de negação de serviço \(DoS\).  Para obter mais informações, consulte <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.  
  
#### Para aumentar o valor maxReceivedMessageSize  
  
1.  No **Gerenciador de Soluções**, clique duas vezes no arquivo app.config no projeto PresentationTier.  
  
2.  Encontre o atributo de tamanho **maxReceivedMessage** e altere o valor para `6553600`.  
  
## Testando o aplicativo  
 Execute o aplicativo.  Os dados são recuperados a partir do serviço de dados e exibidos no formulário.  
  
#### Para testar o aplicativo  
  
1.  Pressione F5.  
  
2.  Os dados das tabelas Clientes e Pedidos são recuperados a partir do serviço de dados e exibidos no formulário.  
  
## Próximas etapas  
 Dependendo dos requisitos do aplicativo, existem várias etapas que você talvez queira realizar após salvar os dados relacionados no aplicativo baseado em Windows.  Por exemplo, você poderia fazer as seguintes melhorias a este aplicativo:  
  
-   Adicionar validação ao conjunto de dados.  Para obter informações, consulte [Instruções passo a passo: adicionando validação a um aplicativo de dados de N camadas](../Topic/Walkthrough:%20Adding%20Validation%20to%20an%20N-Tier%20Data%20Application.md).  
  
-   Adicionar métodos adicionais ao serviço para atualizar dados novamente no banco de dados.  
  
## Consulte também  
 [Trabalhar com conjuntos de dados em aplicativos de n camadas](../data-tools/work-with-datasets-in-n-tier-applications.md)   
 [Atualização hierárquica](../data-tools/hierarchical-update.md)   
 [Acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)