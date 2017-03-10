---
title: "Passo a passo: Criando um WCF Data Service com WPF e o Entity Framework | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "serviços de dados no Visual Studio"
  - "WCF Data Services, o Visual Studio"
  - "Serviços de dados ADO.NET, o Visual Studio"
  - "serviços de dados WCF no Visual Studio"
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Passo a passo: Criando um WCF Data Service com WPF e o Entity Framework
Este passo a passo demonstra como criar um simples [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] que é hospedado em um [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicativo Web e, em seguida, acessá\-lo de um aplicativo Windows Forms.  
  
 Neste passo a passo, você irá:  
  
-   Criar um aplicativo Web para hospedar um [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].  
  
-   Criar um [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] que representa a tabela Customers no banco de dados Northwind.  
  
-   Criar um [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].  
  
-   Criar um aplicativo cliente e adicione uma referência para o [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].  
  
-   Habilitar a associação de dados para o serviço e gerar a interface do usuário.  
  
-   Opcionalmente, adicione recursos de filtragem para o aplicativo.  
  
## Pré-requisitos  
 Você precisará dos seguintes componentes para concluir este passo a passo:  
  
-   O banco de dados de exemplo Northwind.  
  
     Se você não tiver esse banco de dados no computador de desenvolvimento, você pode baixá\-lo do [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088). Para obter instruções, consulte [Downloading Sample Databases](../Topic/Downloading%20Sample%20Databases.md).  
  
## Criando o serviço  
 Para criar um [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], você irá adicionar um projeto da Web, crie um [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)], e, em seguida, crie o serviço do modelo.  
  
 A primeira etapa, você adicionará um projeto da Web para hospedar o serviço.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Para criar o projeto Web  
  
1.  Na barra de menus, escolha **arquivo**, **novo**,  **projeto**.  
  
2.  No **novo projeto** caixa de diálogo caixa, expanda o **Visual Basic** ou **Visual C\#** e **Web** nós e, em seguida, escolha o **aplicativo Web ASP.NET** modelo.  
  
3.  No **nome** texto, digite **NorthwindWeb**, e, em seguida, escolha o **OK** botão.  
  
4.  No **novo projeto ASP.NET** na caixa de **Selecionar um modelo de** escolha **vazio**, e, em seguida, escolha o **OK** botão.  
  
 Nesta etapa, você criará um [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] que representa a tabela Customers no banco de dados Northwind.  
  
#### Para criar o modelo de dados de entidade  
  
1.  Na barra de menus, escolha **projeto**, **Add New Item**.  
  
2.  No **Add New Item** caixa de diálogo, escolha o **dados** nó e, em seguida, escolha o **modelo de dados de entidade ADO.NET** item.  
  
3.  No **nome** texto, digite `NorthwindModel`, e, em seguida, escolha o **Add** botão.  
  
     O Assistente de modelo de dados de entidade é exibida.  
  
4.  No Assistente de modelo de dados de entidade, no **Escolher conteúdo do modelo** página, escolha o **EF Designer do banco de dados** item e, em seguida, escolha o **próximo** botão.  
  
5.  Sobre o **Choose Your Data Connection** execute uma das seguintes etapas:  
  
    -   Se uma conexão de dados para o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione\-o.  
  
         \- ou \-  
  
    -   Escolha o **nova conexão** botão para configurar uma nova conexão de dados. Para obter mais informações, consulte [Adicionar novas conexões](../data-tools/add-new-connections.md).  
  
6.  Se o banco de dados exigir uma senha, selecione a **Sim, incluir dados confidenciais na cadeia de conexão** botão de opção e, em seguida, escolha o **próximo** botão.  
  
    > [!NOTE]
    >  Se for exibida uma caixa de diálogo, escolha **Sim** para salvar o arquivo ao seu projeto.  
  
7.  No **Escolha sua versão** página, escolha o **Entity Framework 5.0** botão de opção e, em seguida, escolha o **próximo** botão.  
  
    > [!NOTE]
    >  Para usar a versão mais recente do Entity Framework 6 com serviços WCF, você precisará instalar o pacote do NuGet do WCF Data Services Entity Framework provedor. Consulte [usar o WCF Data Services 5.6.0 com o Entity Framework 6 \+](http://blogs.msdn.com/b/odatateam/archive/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6.aspx).  
  
8.  No **Choose Your Database Objects** página, expanda o **tabelas** nó, selecione o **clientes** caixa de seleção e, em seguida, escolha o **Concluir** botão.  
  
     O diagrama de modelo de entidade será exibido, e um arquivo NorthwindModel será adicionado ao seu projeto.  
  
 Nesta etapa, você irá criar e testar o serviço de dados.  
  
#### Para criar o serviço de dados  
  
1.  Na barra de menus, escolha **projeto**, **Add New Item**.  
  
2.  No **Add New Item** caixa de diálogo, escolha o **Web** nó e, em seguida, escolha o **WCF Data Services 5.6** item.  
  
3.  No **nome** texto, digite `NorthwindCustomers`, e, em seguida, escolha o **Add** botão.  
  
     O arquivo Northwindcustomers aparece no **Editor de códigos**.  
  
4.  No **Editor de códigos**, localize a primeira `TODO:` comentário e substitua o código a seguir:  
  
     [!code-vb[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.vb)]
     [!code-cs[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.cs)]  
  
5.  Substitua os comentários a `InitializeService` manipulador de eventos com o seguinte código:  
  
     [!code-vb[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.vb)]
     [!code-cs[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.cs)]  
  
6.  Na barra de menus, escolha **Depurar**, **Start Without Debugging** para executar o serviço. Abre uma janela do navegador e o esquema XML para o serviço é exibido.  
  
7.  No **endereço** barra, digite `Customers` ao final da URL para Northwindcustomers e, em seguida, escolha o **ENTER** chave.  
  
     É exibida uma representação XML dos dados na tabela Customers.  
  
    > [!NOTE]
    >  Em alguns casos, o Internet Explorer interpretará os dados como um RSS feed. Você deve certificar\-se de que a opção para exibir RSS feeds está desabilitada. Para obter mais informações, consulte [Troubleshooting Service References](../data-tools/troubleshooting-service-references.md).  
  
8.  Feche a janela do navegador.  
  
 As próximas etapas, você criará um aplicativo de cliente do Windows Forms para consumir o serviço.  
  
## Criando um aplicativo cliente  
 Para criar o aplicativo cliente, você será adicionar um segundo projeto, adicionar uma referência ao projeto, configurar uma fonte de dados e criar uma interface do usuário para exibir os dados do serviço.  
  
 Na primeira etapa, você irá adicionar um projeto Windows Forms à solução e defini\-lo como o projeto de inicialização.  
  
#### Para criar o aplicativo cliente  
  
1.  Na barra de menus, escolha arquivo, **Add**, **novo projeto**.  
  
2.  No **novo projeto** caixa de diálogo caixa, expanda o **Visual Basic** ou **Visual C\#** nó e escolha o **Windows** nó e, em seguida, escolha **Windows Forms Application**.  
  
3.  No **nome** texto, digite `NorthwindClient`, e, em seguida, escolha o **OK** botão.  
  
4.  Em **Solution Explorer**, escolha o **NorthwindClient** nó do projeto.  
  
5.  Na barra de menus, escolha **projeto**, **Set as StartUp Project**.  
  
 Nesta etapa, você irá adicionar uma referência de serviço para o [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] no projeto da Web.  
  
#### Para adicionar uma referência de serviço  
  
1.  Na barra de menus, escolha **projeto**, **Add Service Reference**.  
  
2.  No **Add Service Reference** caixa de diálogo, escolha o **Discover** botão.  
  
     A URL do serviço NorthwindCustomers aparece no **endereço** campo.  
  
3.  Escolha o **OK** botão para adicionar a referência de serviço.  
  
 Nesta etapa, você irá configurar uma fonte de dados para habilitar a vinculação de dados para o serviço.  
  
#### Para habilitar a associação de dados para o serviço  
  
1.  Na barra de menus, escolha **exibição**, **outras janelas**, **fontes de dados**.  
  
2.  No **fontes de dados** janela, escolha o **Add New Data Source** botão.  
  
3.  No **Escolher um tipo de fonte de dados** página do **Data Source Configuration Wizard**, escolha **objeto**, e, em seguida, escolha o **próximo** botão.  
  
4.  Sobre o **Selecionar os objetos de dados** página, expanda o **NorthwindClient** nó e, em seguida, expanda o **Servicereference1** nó.  
  
5.  Selecione **cliente** caixa de seleção e, em seguida, escolha o **Concluir** botão.  
  
 Nesta etapa, você criará a interface do usuário que exibirá os dados do serviço.  
  
#### Para criar a interface do usuário  
  
1.  No **fontes de dados** janela, abra o menu de atalho para o **clientes** nó e escolha **cópia**.  
  
2.  No **Form1. vb** ou **Form1. CS** designer de formulário, abra o menu de atalho e escolha **Colar**.  
  
     Um <xref:System.Windows.Forms.DataGridView> controle, um <xref:System.Windows.Forms.BindingSource> componente e um <xref:System.Windows.Forms.BindingNavigator> componente são adicionados ao formulário.  
  
3.  Escolha o **CustomersDataGridView** controle e, em seguida, no **propriedades** janela conjunto a **encaixe** propriedade **Preencher**.  
  
4.  Em **Solution Explorer**, abra o menu de atalho para o **Form1** nó e escolha **Exibir código** para abrir o Editor de códigos e adicione as seguintes importações ou usando a instrução na parte superior do arquivo:  
  
    ```vb  
    Imports NorthwindClient.ServiceReference1  
    ```  
  
    ```c#  
    using NorthwindClient.ServiceReference1;  
    ```  
  
5.  Adicione o seguinte código para o `Form1_Load` manipulador de eventos:  
  
    ```vb  
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
            Dim proxy As New NorthwindEntities _  
    (New Uri("http://localhost:53161/NorthwindCustomers.svc/"))  
            Me.CustomersBindingSource.DataSource = proxy.Customers  
        End Sub  
    ```  
  
    ```c#  
    private void Form1_Load(object sender, EventArgs e)  
    {  
    NorthwindEntities proxy = new NorthwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc/"));  
    this.CustomersBindingSource.DataSource = proxy.Customers;  
    }  
  
    ```  
  
6.  Em **Solution Explorer**, abra o menu de atalho para o arquivo Northwindcustomers exe e escolha **Exibir no navegador**. Internet Explorer é aberto e o esquema XML para o serviço é exibido.  
  
7.  Copie a URL da barra de endereços do Internet Explorer.  
  
8.  No código que você adicionou na etapa 4, selecione `http://localhost:53161/NorthwindCustomers.svc/` e substituí\-lo com a URL que você acabou de copiar.  
  
9. Na barra de menus, escolha **Depurar**, **Iniciar depuração** para executar o aplicativo. As informações do cliente são exibidas.  
  
 Agora você tem um aplicativo funcional que exibe uma lista de clientes do serviço NorthwindCustomers. Se você quiser expor dados adicionais por meio do serviço, você poderá modificar o [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] para incluir tabelas adicionais do banco de dados Northwind.  
  
 A próxima etapa opcional, você aprenderá como filtrar os dados retornados pelo serviço.  
  
## Adicionando recursos de filtragem  
 Nesta etapa, você irá personalizar o aplicativo para filtrar os dados por cidade do cliente.  
  
#### Para adicionar a filtragem por cidade  
  
1.  Em **Solution Explorer**, abra o menu de atalho para o **Form1. vb** ou **Form1. CS** nó e escolha **Abrir**.  
  
2.  Adicionar um <xref:System.Windows.Forms.TextBox> controle e um <xref:System.Windows.Forms.Button> controle de **Toolbox** ao formulário.  
  
3.  Abra o menu de atalho para o <xref:System.Windows.Forms.Button> controlar e escolha **Exibir código**, e, em seguida, adicione o seguinte código no `Button1_Click` manipulador de eventos:  
  
    ```vb  
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
            Dim proxy As New northwindEntities _  
    (New Uri("http://localhost:53161/NorthwindCustomers.svc"))  
            Dim city As String = TextBox1.Text  
  
            If city <> "" Then  
                Me.CustomersBindingSource.DataSource = From c In _  
             proxy.Customers Where c.City = city  
            End If  
  
        End Sub  
    ```  
  
    ```c#  
    private void Button1_Click(object sender, EventArgs e)  
    {  
    ServiceReference1.northwindModel.northwindEntities proxy = new northwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc"));  
    string city = TextBox1.Text;  
  
    if (!string.IsNullOrEmpty(city)) {  
    this.CustomersBindingSource.DataSource = from c in proxy.Customers where c.City == city;  
    }  
  
    }  
    ```  
  
4.  No código anterior, substitua `http://localhost:53161/NorthwindCustomers.svc` com a URL do `Form1_Load` manipulador de eventos.  
  
5.  Na barra de menus, escolha **Depurar**, **Iniciar depuração** para executar o aplicativo.  
  
6.  Na caixa de texto, digite **Londres**, e, em seguida, escolha o botão. São exibidos apenas os clientes de Londres.  
  
## Consulte também  
 [Serviços do Windows Communication Foundation e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)   
 [How to: Add, Update, or Remove a WCF Data Service Reference](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)