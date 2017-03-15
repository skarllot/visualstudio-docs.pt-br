---
title: "Criando aplicativos de dados | Microsoft Docs"
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
  - "Criando aplicativos de acesso de dados [Visual Studio]"
  - "aplicativos [Visual Studio], dados"
  - "dados [Visual Studio]"
  - "dados [Visual Studio], criando aplicativos"
ms.assetid: ab334d5f-4f49-4346-bce0-3325d6130b3e
caps.latest.revision: 41
caps.handback.revision: 41
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Criando aplicativos de dados
O Visual Studio fornece várias ferramentas em tempo de design para ajudá\-lo a criar aplicativos que acessam dados.  Esta introdução apresenta uma visão geral sobre os processos básicos envolvidos na criação de aplicativos que trabalham com dados.  As informações aqui ignoram deliberadamente muitos detalhes e foram elaboradas como uma fonte de informações gerais e um ponto de saída para muitas outras páginas da Ajuda associadas à criação de um aplicativo de dados.  
  
 À medida que você desenvolve aplicativos que acessam dados no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], você terá requisitos diferentes.  Em alguns casos, você pode simplesmente querer exibir dados em um formulário.  Em outros casos, talvez seja necessário imaginar uma maneira de compartilhar informações com outros aplicativos ou processos.  
  
 Não importa o que faz com dados, há determinados conceitos fundamentais que você deve compreender.  Você pode nunca precisar saber alguns dos detalhes do tratamento de dados, por exemplo, talvez nunca precise criar programaticamente um banco de dados, mas é muito útil entender os conceitos básicos de dados, bem como as ferramentas de dados \(assistentes e designers\) disponíveis no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Um aplicativo de dados típico usa a maioria dos processos ilustrados no diagrama a seguir:  
  
 ![Gráfico de ciclo de dados](../data-tools/media/datacyclegraphicinfo.png "datacyclegraphicinfo")  
O ciclo de dados  
  
 À medida que você cria seu aplicativo, pense na tarefa que você está tentando realizar.  Use as seções a seguir para ajudar a localizar as ferramentas do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e objetos que estão disponíveis para você.  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fornece assistentes para simplificar vários processos mostrados no diagrama anterior.  Por exemplo, executar o **Assistente de Configuração da Fonte de Dados** fornece a seu aplicativo informações suficientes para conectar\-se aos dados, criar um conjunto de dados tipado para receber os dados e transferir os dados para seu aplicativo.  
  
 Para ver rapidamente como [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ajuda no desenvolvimento de aplicativos de dados, consulte [Instruções passo a passo: criando um aplicativo de dados simples](../Topic/Walkthrough:%20Creating%20a%20Simple%20Data%20Application.md).  
  
## Conectando\-se aos dados  
 Para transferir dados para seu aplicativo \(e enviar alterações de volta para a fonte de dados\), algum tipo de comunicação bidirecional precisará ser estabelecida.  Essa comunicação bidirecional é geralmente tratada por objetos no seu modelo de dados.  
  
 Por exemplo, `TableAdapter` conecta os aplicativos que usam conjuntos de dados a um banco de dados e <xref:System.Data.Objects.ObjectContext> conecta entidades no Entity Framework a um banco de dados.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fornece várias ferramentas para auxiliar na criação de conexões que podem ser usadas por seu aplicativo.  Para obter mais informações sobre como conectar seu aplicativo a dados, consulte [Conectando a dados no Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md).  
  
 Para saber como usar conjuntos de dados para conectar seu aplicativo a dados em um banco de dados, consulte [Instruções passo a passo: conectando a dados em um banco de dados \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Database%20\(Windows%20Forms\).md).  
  
## Preparando seu aplicativo para receber dados  
 Se o aplicativo usa um modelo de dados desconectado, você precisa armazenar temporariamente os dados em seu aplicativo enquanto você trabalha com ele.  Visual Studio fornece ferramentas que ajudam você cria os objetos que seu aplicativo usa para armazenar dados temporariamente: conjuntos de dados, entidades e objetos [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].  
  
> [!NOTE]
>  Um aplicativo que usa um modelo de dados desconectado geralmente se conecta a um banco de dados, executa uma consulta trazendo dados para o aplicativo, desconecta\-se do banco de dados e, em seguida, manipula os dados offline antes de reconectar\-se e atualizar o banco de dados.  
  
 Para obter mais informações sobre a criação de conjuntos de dados tipados no seu aplicativo, consulte [Preparando o aplicativo para receber dados](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md).  Para obter informações adicionais sobre como usar conjuntos de dados em aplicativos de n\-camadas, consulte [Conjuntos de dados separados e TableAdapters em diferentes projetos](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md).  
  
 Para aprender a criar um conjunto de dados, conclua os procedimentos no [Instruções passo a passo: criando um conjunto de dados com o Designer de Conjunto de Dados](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
 Para saber como criar objetos [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)], conclua os procedimentos em [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md).  
  
## Buscando dados em seu aplicativo  
 Se seu aplicativo utiliza um modelo de dados desconectado ou não, você precisará ser capaz de buscar dados no aplicativo.  Você coloca dados em seu aplicativo executando consultas ou procedimentos armazenados em um banco de dados.  Aplicativos que armazenam dados em datasets executam consultas e procedimentos armazenados usando `TableAdapter`s, enquanto os aplicativos que armazenam dados em entidades executam consultas usando [LINQ to Entities](../Topic/LINQ%20to%20Entities.md) ou conectando entidades diretamente a procedimentos armazenados.  Para obter mais informações sobre como criar e editar as consultas que usam TableAdapters, consulte [Como criar consultas TableAdapter](../data-tools/how-to-create-tableadapter-queries.md) e [Como editar consultas TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md).  
  
 Para obter mais informações sobre carregar dados em conjuntos de dados e objetos, e sobre executar consultas e procedimentos armazenados, consulte [Buscando dados no aplicativo](../data-tools/fetching-data-into-your-application.md).  
  
 Para saber como carregar dados em um conjunto de dados, conclua os procedimentos em [Instruções passo a passo: exibindo dados em um Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md) e examine o código no manipulador de eventos de carregamento de formulário.  
  
 Para saber como carregar dados em objetos [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)], conclua os procedimentos no [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md).  
  
 Para saber como criar e executar uma consulta SQL, consulte [Como criar e executar uma instrução SQL que retorna linhas](../Topic/How%20to:%20Create%20and%20Execute%20an%20SQL%20Statement%20that%20Returns%20Rows.md).  
  
 Para saber como executar um procedimento armazenado, consulte [Como executar um procedimento armazenado que retorna linhas](../Topic/How%20to:%20Execute%20a%20Stored%20Procedure%20that%20Returns%20Rows.md).  
  
## Exibindo dados em formulários  
 Após inserir os dados em seu aplicativo, você os exibirá normalmente em um formulário para que os usuários possam visualizá\-los ou modificá\-los.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fornece [Janela Fontes de Dados](../Topic/Data%20Sources%20Window.md), onde você pode arrastar itens em formulários para criar automaticamente os controles associados a dados que exibem dados.  Para obter mais informações sobre a associação de dados e exibição de dados para os usuários, consulte [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 Para aprender a apresentar dados aos usuários, conclua os procedimentos nas seguintes explicações passo a passo \(prestando atenção especial para o processo de arrastar itens da janela **Fontes de Dados**\):  
  
-   [Instruções passo a passo: exibindo dados em um Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).  
  
-   [Associar controles WPF a um WCF data service](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)  
  
-   [Instruções passo a passo: associando controles Silverlight a um WCF Data Services](../Topic/Walkthrough:%20Binding%20Silverlight%20Controls%20to%20a%20WCF%20Data%20Service.md)  
  
## Editar dados no seu aplicativo  
 Depois dos usuários serem apresentados aos dados, provavelmente eles os modificarão adicionando novos registros, editando e excluindo registros antes de enviar os dados de volta para o banco de dados.  
  
 Para obter mais informações sobre como trabalhar com os dados depois que são carregados no seu conjunto de dados, consulte [Editando dados no aplicativo](../data-tools/editing-data-in-your-application.md).  
  
## Validando dados  
 Ao fazer alterações nos dados, você geralmente desejará verificar as alterações antes de permitir que os valores sejam aceitos de volta no conjunto de dados ou gravados para o banco de dados.  *Validação* é o nome do processo para verificar se esses novos valores são aceitáveis para os requisitos do seu aplicativo.  Você pode adicionar lógica para verificar valores em seu aplicativo à medida que eles mudam.  O Visual Studio fornece ferramentas que ajudam na adição de código que valida os dados durante alterações de coluna e linha.  Para obter mais informações, consulte [Validando dados](../Topic/Validating%20Data.md).  
  
 Para saber como adicionar validação de dados a seu aplicativo, consulte [Instruções passo a passo: adicionando validação a um conjunto de dados](../Topic/Walkthrough:%20Adding%20Validation%20to%20a%20Dataset.md).  
  
 Para saber como adicionar validação a um conjunto de dados que é separado em um aplicativo de n camadas, consulte [Adicionar validação a um conjunto de dados de n camadas](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
## Salvando dados  
 Após realizar alterações no seu aplicativo \(e validar essas alterações\), você geralmente deseja enviar as alterações de volta para o banco de dados.  Os aplicativos que armazenam dados em conjuntos de dados geralmente usam um TableAdapterManager para salvar dados.  Para obter mais informações, consulte [Visão geral de TableAdapterManager](../Topic/TableAdapterManager%20Overview.md).  Aplicativos do Entity Framework usam o método <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> para salvar dados.  
  
 Para obter mais informações sobre o envio de dados atualizados de volta a um banco de dados, consulte [Salvando dados](../data-tools/saving-data.md).  
  
 Para saber como enviar dados atualizados de um conjunto de dados para um banco de dados, conclua os procedimentos em [Instruções passo a passo: salvando dados de tabelas de dados relacionados \(atualização hierárquica\)](../Topic/Walkthrough:%20Saving%20Data%20from%20Related%20Data%20Tables%20\(Hierarchical%20Update\).md).  
  
## Tópicos relacionados  
 [Visão geral de aplicativos de dados no Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)  
 Fornece links para tópicos que discutem como criar aplicativos que funcionam com os dados.  
  
 [Conectando a dados no Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)  
 Fornece links para tópicos sobre como usar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para conectar seu aplicativo a dados e criar fontes de dados para seus aplicativos.  
  
 [Preparando o aplicativo para receber dados](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)  
 Fornece links para tópicos que explicam como trabalhar com modelos de dados em seu aplicativo, incluindo datasets e Modelos de Dados de Entidade.  
  
 [Buscando dados no aplicativo](../data-tools/fetching-data-into-your-application.md)  
 Fornece links para tópicos que descrevem como carregar dados em seu aplicativo.  
  
 [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)  
 Fornece links para tópicos que explicam como associar os controles do Windows Forms, os controles de WPF e os controles do Silverlight a fontes de dados.  
  
 [Editando dados no aplicativo](../data-tools/editing-data-in-your-application.md)  
 Fornece links para tópicos que descrevem como modificar dados em seu aplicativo.  
  
 [Validando dados](../Topic/Validating%20Data.md)  
 Fornece links para tópicos que descrevem como adicionar validação às alterações de dados.  
  
 [Salvando dados](../data-tools/saving-data.md)  
 Fornece links para tópicos que explicam como enviar dados atualizados do seu aplicativo para um banco de dados ou como salvá\-lo em outros formatos como XML.  
  
 [Ferramentas para trabalhar com fontes de dados no Visual Studio](../Topic/Tools%20for%20Working%20with%20Data%20Sources%20in%20Visual%20Studio.md)  
 Fornece links para tópicos sobre ferramentas que você pode usar para trabalhar com fontes de dados no Visual Studio, como a janela de **Fontes de Dados** e o Designer de Modelo de Dados de Entidade do ADO.NET.