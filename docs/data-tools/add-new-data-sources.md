---
title: "Adicionar novas fontes de dados | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.datasource.datasourcefieldspicker"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "dados [Visual Studio], fontes de dados"
  - "fontes de dados"
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
caps.latest.revision: 56
caps.handback.revision: 52
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Adicionar novas fontes de dados
No contexto de associação de dados .NE no Visual Studio, o termo *fonte de dados* refere\-se a objetos .NET que se conectar a um repositório de dados e expõem os dados a um aplicativo .NET. Os designers do Visual Studio podem consumir a fonte de dados para gerar o código clichê para associar os dados a formas arrastando e soltando a partir de **fontes de dados** janela.    Esse tipo de fonte de dados pode ser:  
  
-   uma classe em um modelo do Entity Framework \(EF\) que está associado a algum tipo de banco de dados  
  
-   um conjunto de dados que está associado a algum tipo de banco de dados  
  
-   uma classe que representa um serviço de rede como um serviço WCF de dados ou um serviço REST  
  
-   uma classe que representa um serviço do Sharepoint  
  
-   uma classe ou uma coleção em sua solução  
  
 Você cria e edita fontes de dados usando o **Data Source Configuration Wizard** em um aplicativo WinForms ou Windows Presentation Foundation. Inicie o assistente selecionando **projeto &#124; Adicionar nova fonte de dados**.  
  
 ![Data Source Configuration Wizard](../data-tools/media/data-source-configuration-wizard.png "Data Source Configuration Wizard")  
  
 Depois de criar uma fonte de dados, ele aparece na janela da ferramenta de fontes de dados \(**Shift \+ Alt \+ D** ou **Exibir &#124; Outras janelas &#124; Fonte de dados**\). Você pode arrastar uma fonte de dados da janela fontes de dados para uma superfície de design do formulário ou controle. Isso faz com que o código clichê ser gerado que exibe os dados que se origina no armazenamento de dados para o usuário. A ilustração a seguir mostra um conjunto de dados foi descartado em um Windows Form. Se você pressionou F5 no aplicativo, os dados do banco de dados subjacente será exibido nos controles de formulários.  
  
 ![Data Source drag operation](~/docs/data-tools/media/raddata-data-source-drag-operation.png "raddata Data Source drag operation")  
  
## Fontes de dados para bancos de dados ou arquivos de banco de dados  
  
### Conjuntos de dados  
 Para criar um conjunto de dados como uma fonte de dados, execute o **Data Source Configuration Wizard** \(**projeto &#124; Adicionar nova fonte de dados**\) e escolha o **banco de dados** tipo de fonte de dados. Siga os prompts para especificar um arquivo de banco de dados ou a conexão de banco de dados novo ou existente.  
  
### Classes de entidade  
 Para criar um modelo do Entity Framework como uma fonte de dados, execute primeiro o **Assistente de modelo de dados de entidade** para criar as classes de entidade \(**projeto &#124; Adicionar Novo Item &#124; Modelo de dados de entidade ADO.NET**\).  
  
 ![New Entity Framework model project item](../data-tools/media/raddata-new-entity-framework-model-project-item.png "raddata New Entity Framework model project item")  
  
 Escolha o método pelo qual você deseja gerar o modelo.  
  
 ![Entity Data Model Wizard](../data-tools/media/raddata-entity-data-model-wizard.png "raddata Entity Data Model Wizard")  
  
 As classes que foram geradas aparecem no **Data Source Configuration Wizard** quando você escolhe o **objetos** categoria.  
  
 ![Data Source Configuration Wizard with Entity Classes](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png "raddata Data Source Configuration Wizard with Entity Classes")  
  
## Fontes de dados de serviços  
 Para criar uma fonte de dados de um serviço, execute o **Data Source Configuration Wizard** e escolha o **Service** tipo de fonte de dados. Isso é realmente apenas um atalho para o **Add Service Reference** caixa de diálogo, você também pode acessar clicando no projeto no Solution Explorer e escolha **Adicionar referência de serviço**.  
  
 Quando você cria uma fonte de dados de um serviço, o Visual Studio adiciona uma referência de serviço ao seu projeto. O Visual Studio também cria objetos de proxy que correspondem aos objetos retornados pelo serviço. Por exemplo, um serviço que retorna um conjunto de dados é representado no seu projeto como um conjunto de dados; um serviço que retorna que um tipo específico é representado no seu projeto como o tipo retornada.  
  
 Você pode criar uma fonte de dados entre os seguintes tipos de serviços:  
  
-   WCF Data Services. Para obter mais informações, consulte [Visão Geral](../Topic/WCF%20Data%20Services%20Overview.md).  
  
-   Serviços do Windows Communication Foundation \(WCF\). Para obter mais informações, consulte [Serviços do Windows Communication Foundation e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md).  
  
-   Serviços da Web.  
  
    > [!NOTE]
    >  Os itens que aparecem no **fontes de dados** janela são dependentes dos dados retornados pelo serviço. Alguns serviços podem não fornecer informações suficientes para que o **Data Source Configuration Wizard** para criar objetos ligáveis. Por exemplo, se o serviço retorna um conjunto de dados não tipado, nenhum item aparecerá no **fontes de dados** janela após concluir o assistente. Isso ocorre porque datasets não tipados não fornecem um esquema e, portanto, o assistente não tem informações suficientes para criar a fonte de dados.  
  
## Fontes de dados para objetos  
 Você pode criar uma fonte de dados de qualquer objeto que expõe uma ou mais propriedades públicas, executando o **Data Source Configuration Wizard** e, em seguida, selecionando o **objeto** tipo de fonte de dados. Todas as propriedades públicas de um objeto são exibidas no **fontes de dados** janela.   Se você estiver usando o Entity Framework e gerar um modelo, isso é onde encontrar as classes de entidade que as fontes de dados para seu aplicativo.  
  
 Sobre o **Selecionar os objetos de dados** página, expanda os nós na exibição em árvore para localizar os objetos que você deseja associar a. O modo de exibição de árvore contém nós para seu projeto e assemblies e outros projetos referenciados pelo seu projeto.  
  
 Se você deseja associar a um objeto em um assembly ou projeto que não aparece na exibição de árvore, clique em **Adicionar referência** e usar o **Add Reference Dialog Box** para adicionar uma referência ao assembly ou projeto. Depois de adicionar a referência, o assembly ou projeto é adicionado à exibição em árvore.  
  
> [!NOTE]
>  Você precisará criar o projeto que contém os objetos antes dos objetos aparecem na exibição de árvore.  
  
> [!NOTE]
>  Para oferecer suporte a vinculação de dados de arrastar e soltar, os objetos que implementam a <xref:System.ComponentModel.ITypedList> ou <xref:System.ComponentModel.IListSource> interface deve ter um construtor padrão. Caso contrário, o Visual Studio não é possível instanciar o objeto de fonte de dados, e ele exibirá um erro quando você arrasta o item para a superfície de design.  
  
## Fontes de dados de listas do SharePoint  
 Você pode criar uma fonte de dados de uma lista do SharePoint executando o **Data Source Configuration Wizard** e selecionando o **SharePoint** tipo de fonte de dados. SharePoint expõe dados por meio de [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] para criar uma fonte de dados do SharePoint é o mesmo que criar uma fonte de dados de um serviço. Selecionando o **SharePoint** item o **Data Source Configuration Wizard** abre o **Add Service Reference** caixa de diálogo em que você se conectar ao serviço de dados do SharePoint, apontando para o servidor do SharePoint.  Requer o SDK do Sharepoint.  
  
## Consulte também  
 [Ferramentas de dados do Visual Studio para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)