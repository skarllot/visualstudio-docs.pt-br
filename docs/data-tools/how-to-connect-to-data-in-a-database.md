---
title: "Como conectar a dados em um banco de dados | Microsoft Docs"
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
  - "dados [Visual Studio], conectando-se a bancos de dados"
  - "fontes de dados, criando"
  - "fontes de dados, bancos de dados"
  - "conexões de banco de dados"
  - "bancos de dados, conectando a"
ms.assetid: 6c56e54e-8834-4297-85aa-cc1a443ba556
caps.latest.revision: 55
caps.handback.revision: 55
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Como conectar a dados em um banco de dados
É possível usar o Visual Studio para conectar o aplicativo a um banco de dados.  Após criar a conexão de dados, o Visual Studio gera um modelo de dados que o aplicativo usa para interagir com os dados no banco de dados.  Os objetos no modelo de dados são exibidos no [Janela Fontes de Dados](../Topic/Data%20Sources%20Window.md).  É possível criar controles associados a dados arrastando itens da **Janela Fontes de Dados** para uma superfície de design.  Para obter mais informações, consulte [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 Este tópico fornece instruções para conectar a um banco de dados e criar os seguintes tipos de modelos de dados:  
  
-   Conjunto de dados  
  
-   Modelo de Dados de Entidade \(EDM\)  
  
> [!NOTE]
>  Também é possível usar o Visual Studio para criar classes LINQ to SQL a partir de um banco de dados.  No entanto, classes LINQ to SQL não são exibidas na janela **Fontes de Dados** e, portanto, não podem ser arrastadas diretamente para um designer para criar controles associados a dados.  Para obter mais informações sobre criação de classes LINQ to SQL a partir de um banco de dados, consulte [Como: criar LINQ to SQL classes mapeadas para tabelas e exibições \(Object Relational Designer\)](../Topic/How%20to:%20Create%20LINQ%20to%20SQL%20classes%20mapped%20to%20tables%20and%20views%20\(O-R%20Designer\).md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
##  <a name="dataset"></a> Conectando a um banco de dados e criando um conjunto de dados  
 Ao criar um conjunto de dados que é baseado em um banco de dados, o Visual Studio cria um conjunto de classes que representa uma visão programável dos dados.  A classe principal é chamada de *conjunto de dados digitados*.  O conjunto de dados digitados contém objetos de tabela de dados que representam tabelas no banco de dados.  Para obter mais informações sobre conjuntos de dados digitados, consulte [Ferramentas do conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
 Após criar um conjunto de dados, é possível criar controles WPF ou Windows Forms associados a dados arrastando objetos de conjunto de dados da janela Fontes de Dados para o designer de WPF ou Windows Forms.  
  
#### Conectar o aplicativo a um banco de dados e criar um conjunto de dados  
  
1.  Abra um projeto existente no Visual Studio ou crie um novo projeto.  
  
2.  No menu **Dados**, clique em **Incluir Nova Fonte de Dados**.  
  
     O **Assistente de Configuração de Fonte de Dados** é aberto.  
  
3.  Na página **Escolher um Tipo de Fonte de Dados**, selecione **Banco de Dados** e clique em **Avançar**.  
  
4.  Na página **Escolher um Modelo de Banco de Dados**, selecione **Conjunto de Dados** e clique em **Avançar**.  
  
5.  Na página **Escolher Conexão de Dados**, selecione uma conexão de dados na lista de conexões disponíveis e clique em **Avançar**.  
  
     Se a conexão de dados desejada não estiver disponível, crie uma nova conexão seguindo as etapas de [Criar uma nova conexão de banco de dados](#CreatingDataConnection).  
  
6.  Na página **Salvar a Cadeia de Caracteres de Conexão no Arquivo de Configuração do Aplicativo**, opcionalmente desmarque a caixa de seleção **Sim, salve a conexão como** se desejar salvar a cadeia de conexão diretamente no aplicativo compilado.  Por padrão, a conexão é salva no arquivo de configuração do aplicativo.  Para obter mais informações, consulte [Como salvar e editar cadeias de conexão](../Topic/How%20to:%20Save%20and%20Edit%20Connection%20Strings.md).  
  
7.  Na página **Escolher Objetos de Banco de Dados**, selecione os objetos de banco de dados que serão utilizados no aplicativo.  Também existe a opção de substituir o **nome do DataSet** padrão.  
  
8.  Clique em **Finalizar**.  O conjunto de dados recém\-criado agora está disponível na janela **Fontes de Dados**.  
  
    > [!NOTE]
    >  Se a janela **Fontes de Dados** não estiver aberta, clique em **Mostrar Fontes de Dados** no menu **Dados** para abrir a janela.  
  
9. Agora é possível arrastar itens da janela **Fontes de Dados** para o designer de WPF, para o designer de Windows Forms ou parar o [Component Designer](../Topic/Component%20Designer.md) para criar controles associados a dados.  Para obter mais informações, consulte [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
##  <a name="edm"></a> Conectando ao banco de dados e criando um modelo de dados de entidade  
 Ao criar um Modelo de Dados de Entidade que é baseado em um banco de dados, o Visual Studio cria um conjunto de classes que representa uma visão programável dos dados.  Para obter mais informações sobre Modelos de Dados de Entidade e sobre ADO.NET Entity Framework, consulte [Visão geral do Entity Framework](../Topic/Entity%20Framework%20Overview.md).  
  
 Após criar um Modelo de Dados de Entidade, é possível criar controles WPF associados a dados arrastando objetos de entidade da janela Fontes de Dados para o designer de WPF.  
  
#### Conectar o aplicativo a um banco de dados e criar um Modelo de Dados de Entidade  
  
1.  Abra um projeto existente no Visual Studio ou crie um novo projeto.  
  
2.  Siga as etapas do **Assistente de Modelo de Dados de Entidade** para conectar a um banco de dados e especificar o conteúdo do modelo.  Para obter mais informações, consulte [How to: Create a New .edmx File](http://msdn.microsoft.com/pt-br/beb8189e-e51c-4051-839c-9902c224abf2).  
  
3.  Após concluir o **Assistente de Modelo de Dados de Entidade**, o Modelo de Dados de Entidade criado é aberto no Designer de Modelo de Dados de Entidade e os objetos de dados agora estão disponíveis na janela **Fontes de Dados**.  
  
    > [!NOTE]
    >  Se a janela **Fontes de Dados** não estiver aberta, clique em **Mostrar Fontes de Dados** no menu **Dados** para abrir a janela.  
  
4.  Se o designer de WPF estiver aberto, será possível arrastar itens da janela **Fontes de Dados** para o designer para criar controles que são associados ao Modelo de Dados de Entidade.  Para obter mais informações, consulte [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md).  
  
     Se o designer de Windows Forms estiver aberto, não será possível arrastar itens de **Fontes de Dados** para o designer.  Para criar controles associados ao Modelo de Dados de Entidade, é necessário compilar o projeto, incluir uma nova fonte de dados de objeto que é baseado no Modelo de Dados de Entidade e arrastar esses objetos para o designer.  
  
##  <a name="CreatingDataConnection"></a> Criando uma nova conexão de banco de dados  
 Ao usar o **Assistente de Configuração de Fonte de Dados** ou o **Assistente de Modelo de Dados de Entidade**, é necessário especificar uma conexão com o banco de dados que deseja utilizar.  Se a conexão com o banco de dados ainda não existir, realize as etapas a seguir para criar a conexão.  
  
 Essas instruções consideram que o **Assistente de Configuração de Fonte de Dados** ou o **Assistente de Modelo de Dados de Entidade** foi iniciado conforme descrito em [Conectando ao Banco de Dados e Criando um Conjunto de Dados](#dataset) e [Conectando ao Banco de Dados e Criando um Modelo de Dados de Entidade](#edm).  
  
#### Para criar uma nova conexão de banco de dados  
  
1.  Na página **Escolher Conexão de Dados** do **Assistente de Configuração de Fonte de Dados** ou do **Assistente de Modelo de Dados de Entidade**, clique em **Nova Conexão**.  
  
     Ocorrerá uma das seguintes ações:  
  
    -   Se uma conexão de dados já foi criada no Visual Studio, a caixa de diálogo **Incluir Conexão** será exibida.  
  
    -   Se esta for a primeira conexão de dados criada no Visual Studio, a caixa de diálogo **Escolher Fonte de Dados** será exibida.  Selecione o tipo de banco de dados ao qual deseja conectar e clique em **OK** para exibir a caixa de diálogo **Incluir Conexão**.  
  
2.  Na caixa de diálogo **Incluir Conexão**, insira as informações solicitadas.  A caixa de diálogo **Incluir Conexão** é diferente para cada tipo de provedor de dados.  
  
    > [!NOTE]
    >  Se a **Fonte de Dados** selecionada na caixa de diálogo **Incluir Conexão** não for a fonte de dados à qual deseja conectar, clique em **Alterar** para abrir a caixa de diálogo **Alterar Fonte de Dados** e escolha uma fonte de dados diferente.  
  
3.  Na caixa de diálogo **Adicionar Conexão**, clique em **OK**.  
  
     Você será retornado para a página **Escolher Conexão de Dados** do **Assistente de Configuração de Fonte de Dados** ou do **Assistente de Modelo de Dados de Entidade**.  
  
4.  Na página **Escolher Conexão de Dados**, certifique\-se de que a nova conexão de dados está selecionada e clique em **Avançar**.  
  
5.  Conclua as etapas restantes no **Assistente de Configuração de Fonte de Dados** ou do **Assistente de Modelo de Dados de Entidade**.  
  
## Segurança do .NET Framework  
 O armazenamento das informações confidenciais \(como uma senha\) pode afetar a segurança do aplicativo.  O uso da Autenticação do Windows \(também conhecida como segurança integrada\) é uma maneira mais segura de controlar o acesso a um banco de dados.  Para obter mais informações, consulte [Protegendo informações de conexão](../Topic/Protecting%20Connection%20Information.md).  
  
## Consulte também  
 [Adicionar novas fontes de dados](../data-tools/add-new-data-sources.md)   
 [Instruções passo a passo de dados](../Topic/Data%20Walkthroughs.md)   
 [Associar controles dos Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Conectando a dados no Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Conectando a uma fonte de dados](../Topic/Connecting%20to%20a%20Data%20Source%20in%20ADO.NET.md)