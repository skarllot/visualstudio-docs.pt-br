---
title: "Conectando a dados em aplicativos dos Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "System.Data.SqlClient.SqlConnection"
  - "System.Data.Odbc.OdbcConnection"
  - "System.Data.OleDb.OleDbConnection"
  - "System.Data.OracleClient.OracleConnection"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "conectando-se a bancos de dados, conexões ADO.NET"
  - "objetos de conexão"
  - "objetos de conexão, ferramentas com as quais trabalhar"
  - "objetos de conexão, tipos de"
  - "sondagem de conexões, conexões ADO.NET"
  - "cadeias de conexão [Visual Studio], ADO.NET"
  - "conexões, sobre conexões"
  - "conexões, tempo de design"
  - "dados [Visual Studio], conectando"
  - "adaptadores de dados, conexões"
  - "conexões de banco de dados [Visual Studio], ADO.NET"
  - "bancos de dados [Visual Studio], conectando a"
  - "conexões de tempo de design"
  - "propriedades dinâmicas, conexões ADO.NET"
  - "Classe OleDbConnection, objetos de conexão ADO.NET"
  - "Classe SqlConnection, objetos de conexão ADO.NET"
  - "TableAdapters, conexões"
  - "transações, ADO.NET"
ms.assetid: 184cbd0d-3b26-418d-a11c-f9f8f004fbff
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Conectando a dados em aplicativos dos Windows Forms
O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fornece ferramentas para conectar seu aplicativo a dados de várias fontes diferentes, como bancos de dados, serviços Web e objetos.  Se você estiver usando as ferramentas de design de dados no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], normalmente você não precisa criar explicitamente um objeto de conexão para o formulário ou componente.  O objeto de conexão geralmente é criado depois que você preenche um dos assistentes de dados ou arrasta objetos de dados para o seu formulário.  Para conectar o seu aplicativo a dados em um banco de dados, serviço Web ou objeto, execute o [Assistente para Configuração da Fonte de Dados](../data-tools/media/data-source-configuration-wizard.png) selecionando **Adicionar Nova Fonte de Dados** da [Janela Fontes de Dados](../Topic/Data%20Sources%20Window.md).  
  
 O diagrama a seguir mostra o fluxo normal das operações durante a conexão aos dados, executando uma consulta TableAdapter para buscar dados e exibi\-lo em um formulário em um aplicativo do Windows.  
  
 ![Fluxo de dados em um aplicativo cliente](../data-tools/media/clientdatadiagram.png "ClientDataDiagram")  
  
 Em algumas situações, é conveniente criar um objeto de conexão sem o auxílio de ferramentas de design de dados.  Para obter informações sobre como criar conexões programaticamente, consulte [Conectando a uma fonte de dados](../Topic/Connecting%20to%20a%20Data%20Source%20in%20ADO.NET.md).  
  
> [!NOTE]
>  Para obter informações sobre como conectar aplicativos Web a dados, consulte [ASP.NET Data Access Content Map](http://msdn.microsoft.com/pt-br/f9219396-a0fa-481f-894d-e3d9c67d64f2).  
  
## Passo a passo para conectar aplicativos do Windows Forms a dados  
 O passo a passo a seguir fornece procedimentos relacionados à conexão a dados em aplicativos do Windows Forms:  
  
-   [Instruções passo a passo: conectando a dados em um banco de dados \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Database%20\(Windows%20Forms\).md)  
  
-   [Instruções passo a passo: conectando a dados em um arquivo de banco de dados local \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Local%20Database%20File%20\(Windows%20Forms\).md)  
  
-   [Instruções passo a passo: conectando a dados em um serviço Web \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Web%20Service%20\(Windows%20Forms\).md)  
  
-   [Instruções passo a passo: conectando a dados em objetos \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)  
  
-   [Instruções passo a passo: conectando a dados em um banco de dados do Access \(Windows Forms\)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)  
  
## Criando conexões  
 No [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], use a caixa de diálogo **Adicionar\/Modificar Conexão** para configurar as conexões.  A caixa de diálogo **Adicionar Conexão** aparece quando você está editando ou criando conexões dentro de um dos assistentes de dados, [Gerenciador de Servidores\/Navegador de Banco de Dados](../Topic/Server%20Explorer.md) ou quando você está editando propriedades de conexão na janela **Propriedades**.  
  
 As conexões de dados são configuradas automaticamente quando você executa uma das seguintes ações.  
  
|Ação|Descrição|  
|----------|---------------|  
|Executar o [Assistente para Configuração da Fonte de Dados](../data-tools/media/data-source-configuration-wizard.png).|As conexões são configuradas quando o caminho do banco de dados é escolhido no **Assistente de Configuração de Fonte de Dados**.  Para obter mais informações, consulte [Como conectar a dados em um banco de dados](../data-tools/how-to-connect-to-data-in-a-database.md).|  
|Executar o [TableAdapter Assistente de Configuração](../Topic/TableAdapter%20Configuration%20Wizard.md).|As conexões são criadas dentro do **Assistente de Configuração do TableAdapter**.  Para obter mais informações, consulte [Criar e configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md).|  
|Executar o [Editando TableAdapters](../data-tools/editing-tableadapters.md).|As conexões são criadas dentro do **Assistente de Configuração de Consultas do TableAdapter**.  Para obter mais informações, consulte [Como criar consultas TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).|  
|Arraste os itens da [Janela Fontes de Dados](../Topic/Data%20Sources%20Window.md) para um formulário ou o [Component Designer](../Topic/Component%20Designer.md).|Objetos de conexão são criados quando você arrasta itens da janela **Fontes de Dados** para o **Designer de Formulários do Windows** ou **Designer de Componentes**.  Para obter mais informações, consulte [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).|  
|Adicionar novas conexões de dados ao [Gerenciador de Servidores\/Navegador de Banco de Dados](../Topic/Server%20Explorer.md) .|As conexões de dados no **Gerenciador de Servidores\/Navegador de Banco de Dados** aparecem na lista de conexões disponíveis dentro dos assistentes de dados|  
  
## Cadeias de caracteres de conexão  
 As cadeias de caracteres de conexão podem ser armazenadas dentro do seu aplicativo compilado ou no arquivo de configuração do aplicativo.  Para obter mais informações, consulte [Como salvar e editar cadeias de conexão](../Topic/How%20to:%20Save%20and%20Edit%20Connection%20Strings.md).  
  
## Informações e segurança de conexão  
 Como abrir uma conexão envolve a obtenção de acesso a um importante recurso, que é um banco de dados, muitas vezes há questões de segurança envolvidas na configuração e trabalho com uma conexão.  
  
 Como você protege o aplicativo e o acesso dele à fonte de dados depende da arquitetura do seu sistema.  Em um aplicativo baseado na Web, por exemplo, os usuários normalmente têm acesso anônimo ao IIS \(Internet Information Services\) e, portanto, não fornecem credenciais de segurança.  Nesse caso, o aplicativo mantém e usa suas próprias informações de logon, em vez de quaisquer informações específicas do usuário, para abrir a conexão e acessar o banco de dados.  
  
> [!IMPORTANT]
>  O armazenamento de detalhes da cadeia de caracteres de conexão, como uma senha, pode afetar a segurança do aplicativo.  O uso da segurança integrada do Windows é uma maneira mais segura de controlar o acesso a um banco de dados.  Para obter mais informações, consulte [Protegendo informações de conexão](../Topic/Protecting%20Connection%20Information.md).  
  
 Em aplicativos de intranet ou de várias camadas, você pode usar a opção de segurança integrada fornecida pelo Windows, IIS e SQL Server.  Nesse modelo, as credenciais de autenticação do usuário para a rede local também são usadas para acessar recursos de banco de dados e nenhum nome de usuário ou senha explícita é usada na cadeia de caracteres de conexão.  Normalmente, as permissões são estabelecidas no computador do servidor de banco de dados por meio de grupos, para que você não precise estabelecer permissões individuais para cada usuário que acesse o banco de dados.  Neste modelo, você não precisa armazenar nenhuma informação de logon para a conexão e não precisa realizar outras ações para proteger as informações da cadeia de caracteres de conexão.  
  
 Para obter mais informações sobre segurança, consulte os seguintes tópicos:  
  
-   [Protegendo aplicativos ADO.NET](../Topic/Securing%20ADO.NET%20Applications.md)  
  
-   [Acesso mais seguro a arquivos e dados no Windows Forms](../Topic/More%20Secure%20File%20and%20Data%20Access%20in%20Windows%20Forms.md)  
  
## Conexões de tempo de design no Gerenciador de Servidores\/Navegador de Banco de Dados  
 O **Gerenciador de Servidores\/Navegador de Banco de Dados** é um dos meios para você criar conexões de tempo de design para as fontes de dados.  Isso permite que você: navegue fontes de dados disponíveis, exiba informações sobre as tabelas, colunas e outros elementos que elas contêm e edite e crie elementos de banco de dados.  
  
 Seu aplicativo não usa diretamente as conexões disponíveis no **Gerenciador de Servidores\/Navegador de Banco de Dados**.  Essas conexões são usadas pelo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para trabalhar com seu banco de dados em tempo de design.  Para obter mais informações, consulte [Visual Database Tools](http://msdn.microsoft.com/pt-br/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 Por exemplo, em tempo de design você pode usar o **Gerenciador de Servidores\/Navegador de Banco de Dados** para criar uma conexão com um banco de dados.  Depois, quando criar um formulário, você pode procurar o banco de dados, selecionar as colunas de uma tabela, e arrastá\-las para o [Designer de Conjunto de Dados](../data-tools/creating-and-editing-typed-datasets.md).  Isso cria um [TableAdapter](../data-tools/tableadapter-overview.md) no seu conjunto de dados.  Ele também cria um novo objeto de conexão, que é parte do TableAdapter recém\-criado.  
  
 As informações sobre conexões de tempo de design são armazenadas no seu computador local, independentemente de um projeto ou solução específicos.  Portanto, quando você estabelece uma conexão de tempo de design, enquanto trabalha em um aplicativo, ela aparece no **Gerenciador de Servidores\/Navegador de Banco de Dados** sempre que você trabalhar no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], desde que o servidor para o qual os pontos de conexão apontam esteja disponível.  Para obter mais informações, consulte [How to: Connect to a Database from Server Explorer](http://msdn.microsoft.com/pt-br/7c1c3067-0d77-471b-872b-639f9f50db74).  
  
 [!INCLUDE[SQLObjectExplorer](../data-tools/includes/sqlobjectexplorer_md.md)]  
  
## Consulte também  
 [Conectando a dados no Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Como conectar a dados em um banco de dados](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Instruções passo a passo: conectando a dados em um banco de dados \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Database%20\(Windows%20Forms\).md)   
 [ASP.NET Data Access Content Map](http://msdn.microsoft.com/pt-br/f9219396-a0fa-481f-894d-e3d9c67d64f2)   
 [Preparando o aplicativo para receber dados](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscando dados no aplicativo](../data-tools/fetching-data-into-your-application.md)   
 [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Editando dados no aplicativo](../data-tools/editing-data-in-your-application.md)   
 [Validando dados](../Topic/Validating%20Data.md)   
 [Salvando dados](../data-tools/saving-data.md)