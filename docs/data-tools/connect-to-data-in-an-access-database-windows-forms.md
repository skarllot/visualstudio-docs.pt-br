---
title: "Instru&#231;&#245;es passo a passo: conectando a dados em um banco de dados do Access (Windows Forms) | Microsoft Docs"
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
  - "Acessar bancos de dados, conectando"
  - "conectando-se a dados, de Acessar bancos de dados"
  - "dados [Visual Studio], conectando"
  - "bancos de dados, Acesso"
  - "bancos de dados, conectando a"
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
caps.latest.revision: 29
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Instru&#231;&#245;es passo a passo: conectando a dados em um banco de dados do Access (Windows Forms)
É possível se conectar a um banco de dados do Access \(um arquivo .mdf ou um arquivo .accdb\) usando\-se o Visual Studio.  Depois de definir a conexão, os dados são exibidos na **Janela Fontes de Dados**.  Nela, é possível arrastar tabelas ou exibições para os formulários.  Se você quiser compreender como o sistema de projeto no Visual Studio gerencia esses arquivos de banco de dados locais, consulte [Como gerenciar arquivos de dados locais no projeto](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
## Pré-requisitos  
 Para usar esses procedimentos, você precisa de um Aplicativo Windows Forms e de um banco de dados do Access \(arquivo .accdb\) ou um banco de dados do Access 2000\-2003 \(arquivo .mdb\).  Siga o procedimento correspondente ao tipo de arquivo.  
  
## Criando o Conjunto de Dados para um arquivo .accdb  
 É possível se conectar aos bancos de dados criados com Access 2013, Office 365, Access 2010 ou Access 2007 usando\-se o procedimento a seguir.  
  
#### Para criar o conjunto de dados  
  
1.  Abra o Aplicativo Windows Forms ao qual você deseja se conectar dados.  
  
2.  No menu **Exibir**, escolha **Outras Janelas** \> **Fontes de Dados**.  
  
     ![View Other Windows Data Sources](~/docs/data-tools/media/viewdatasources.png "ViewDataSources")  
  
3.  Na janela **Fontes de Dados**, clique em **Adicionar Nova Fonte de Dados**.  
  
     ![Add New Data Source](~/docs/data-tools/media/dataaddnewdatasource.png "dataAddNewDataSource")  
  
4.  Escolha **Base de Dados** na página **Escolher um Tipo de Fonte de Dados** e, em seguida, escolha **Próximo**.  
  
5.  Escolha **Dataset** na página **Escolha um Modelo de Banco de Dados** e, em seguida, escolha **Próximo**.  
  
6.  Na página **Escolha a Conexão de Dados**, selecione **Nova Conexão** para configurar uma nova conexão de dados.  
  
7.  Altere **Fonte de dados** para **Provedor de Dados .NET Framework para OLE DB**.  
  
     ![Change Data Provider to OLE DB](../data-tools/media/datachangedatasourceoledb.png "dataChangeDataSourceOLEDB")  
  
    > [!IMPORTANT]
    >  Embora uma fonte de dados de **Arquivo de Banco de Dados do Microsoft Access \(OLE DB\)** possa ser aparentemente a escolha certa, você usa esse tipo de fonte de dados apenas para o banco de dados .mdb.  
  
8.  No **Provedor OLE DB**, escolha **Provedor OLE DB do Mecanismo de Banco de Dados do Microsoft Office 12.0 Access**.  
  
     ![OLE DB Provider Microsoft Office 12.0 Access](../data-tools/media/dataoledbprovideroffice12access.png "dataOLEDBProviderOffice12Access")  
  
9. Em **Nome do servidor ou do arquivo**, especifique o caminho e o nome do arquivo .accdb ao qual você deseja se conectar e, em seguida, escolha **OK**.  
  
    > [!NOTE]
    >  Se o arquivo do banco de dados tiver um nome de usuário e uma senha, especifique\-os antes de escolher **OK**.  
  
10. Escolha **Próximo** na página **Escolha a Conexão de Dados**.  
  
11. Escolha **Próximo** na página **Salvar cadeia de conexão no arquivo de configuração do aplicativo**.  
  
12. Expanda o nó **Tabelas** na página **Escolher Objetos do Banco de Dados**.  
  
13. Escolha as tabelas ou as exibições desejadas no Conjunto de Dados e **Finalizar**.  
  
     O Conjunto de Dados é adicionado ao projeto, e as tabelas e as exibições são mostradas na janela **Fontes de Dados**.  
  
## Criando o Conjunto de Dados para um arquivo .mdb  
 Você cria o conjunto de dados executando o **Assistente de Configuração de Fonte de Dados**.  
  
#### Para criar o conjunto de dados  
  
1.  Abra o Aplicativo Windows Forms ao qual você deseja se conectar dados.  
  
2.  No menu **Exibir**, escolha **Outras Janelas** \> **Fontes de Dados**.  
  
     ![View Other Windows Data Sources](~/docs/data-tools/media/viewdatasources.png "ViewDataSources")  
  
3.  Na janela **Fontes de Dados**, clique em **Adicionar Nova Fonte de Dados**.  
  
     ![Add New Data Source](~/docs/data-tools/media/dataaddnewdatasource.png "dataAddNewDataSource")  
  
4.  Escolha **Base de Dados** na página **Escolher um Tipo de Fonte de Dados** e, em seguida, escolha **Próximo**.  
  
5.  Escolha **Dataset** na página **Escolha um Modelo de Banco de Dados** e, em seguida, escolha **Próximo**.  
  
6.  Na página **Escolha a Conexão de Dados**, selecione **Nova Conexão** para configurar uma nova conexão de dados.  
  
7.  Se a **Fonte de dados** não for **Arquivo de Banco de Dados do Microsoft Access \(OLE DB\)**, escolha **Alterar** para abrir a caixa de diálogo **Alterar Fonte de Dados** e **Arquivo de Banco de Dados do Microsoft Access**, além de **OK**.  
  
8.  No **Nome do arquivo de banco de dados**, especifique o caminho e o nome do arquivo .mdb ao qual você deseja se conectar e, em seguida, escolha **OK**.  
  
     ![Add Connection Access Database File](../data-tools/media/dataaddconnectionaccessmdb.png "dataAddConnectionAccessMDB")  
  
9. Escolha **Próximo** na página **Escolha a Conexão de Dados**.  
  
10. Escolha **Próximo** na página **Salvar cadeia de conexão no arquivo de configuração do aplicativo**.  
  
11. Expanda o nó **Tabelas** na página **Escolher Objetos do Banco de Dados**.  
  
12. Escolha as tabelas ou as exibições desejadas no Conjunto de Dados e **Finalizar**.  
  
     O Conjunto de Dados é adicionado ao projeto, e as tabelas e as exibições são mostradas na janela **Fontes de Dados**.  
  
## Segurança  
 O armazenamento das informações confidenciais \(como uma senha\) pode afetar a segurança do aplicativo.  O uso da Autenticação do Windows \(também conhecida como segurança integrada\) é uma maneira mais segura de controlar o acesso a um banco de dados.  Para obter mais informações, consulte [Protegendo informações de conexão](../Topic/Protecting%20Connection%20Information.md).  
  
## Próximas etapas  
 O conjunto de dados recém\-criado agora está disponível na janela **Fontes de Dados**.  Agora é possível realizar qualquer uma das seguintes tarefas:  
  
-   Selecione itens na janela **Fontes de Dados** e os arraste para o formulário \(consulte [Associar controles dos Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)\).  
  
-   Abra a fonte de dados no [Designer de Conjunto de Dados](../data-tools/creating-and-editing-typed-datasets.md) para adicionar ou editar os objetos que constituem o conjunto de dados.  
  
-   Adicione a lógica de validação ao evento <xref:System.Data.DataTable.ColumnChanging> or <xref:System.Data.DataTable.RowChanging> das tabelas de dados no conjunto de dados \(consulte [Validar dados em conjuntos de dados](../data-tools/validate-data-in-datasets.md)\).  
  
## Consulte também  
 [Conectando a dados no Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparando o aplicativo para receber dados](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscando dados no aplicativo](../data-tools/fetching-data-into-your-application.md)   
 [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Editando dados no aplicativo](../data-tools/editing-data-in-your-application.md)   
 [Validando dados](../Topic/Validating%20Data.md)   
 [Salvando dados](../data-tools/saving-data.md)   
 [Instruções passo a passo de dados](../Topic/Data%20Walkthroughs.md)