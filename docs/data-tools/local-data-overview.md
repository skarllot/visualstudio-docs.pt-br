---
title: "Vis&#227;o geral de dados local | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
  - "SQL Server Express"
  - "dados locais"
  - "LocalDB do SQL Server"
  - "LocalDB"
  - "SQLEXPRESS"
  - "SQL Server, locais de dados"
  - "SQL Express"
  - "SQL Server Compact"
  - "acesso a dados [Visual Studio], solução de problemas"
  - "Acesso, arquivos. mdb no Visual Studio"
  - "local dos dados [Visual Studio]"
ms.assetid: d6afa5ac-2bb8-49f2-a50e-f71f611ed506
caps.latest.revision: 71
caps.handback.revision: 66
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Vis&#227;o geral de dados local
Ao usar dados locais, você conecta seu aplicativo a um arquivo base de dados no computador local, em vez a uma base de dados em um servidor separado.  Por exemplo, você pode conectar um aplicativo que esteja desenvolvendo no Visual Studio para os seguintes arquivos de banco de dados local:  
  
-   Arquivos de banco de dados do SQL Server Express LocalDB \(.mdf\)  
  
-   Arquivos de banco de dados do SQL Server Express \(.mdf\)  
  
-   Arquivos de banco de dados do Microsoft Access \(.mdb\)  
  
 A tabela a seguir fornece links para páginas descrevendo como conectar seu aplicativo para dados locais:  
  
|Tópico|Descrição|  
|------------|---------------|  
|[Criar um banco de dados SQL usando um designer](../data-tools/create-a-sql-database-by-using-a-designer.md)|Fornece instruções passo a passo para criar um arquivo de banco de dados local que pode ser usado para testar recursos de dados e compilar aplicativos.|  
|[Instruções passo a passo: conectando a dados em um arquivo de banco de dados local \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Local%20Database%20File%20\(Windows%20Forms\).md)|Fornece instruções passo a passo para se conectar a um banco de dados SQL Server Express LocalDB ao criar um aplicativo do Windows simples.|  
|[Instruções passo a passo: conectando a dados em um banco de dados do Access \(Windows Forms\)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)|Fornece instruções passo a passo para se conectar a um banco de dados do Microsoft Access.|  
|[Como se conectar ao banco de dados Northwind](../data-tools/how-to-connect-to-the-northwind-database.md)|Fornece instruções para conexão com o banco de dados de exemplo Northwind no [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)], SQL Server Compact, SQL Server Express e Access.|  
  
 Após você criar uma fonte de dados e configurá\-la para acessar um arquivo de dados local, você trabalha com os dados usando as mesmas tecnologias e objetos que usaria para trabalhar com os dados de qualquer outra origem.  Para obter mais informações, consulte [Criando aplicativos de dados](../data-tools/creating-data-applications.md).  
  
## Integrando o banco de dados a seu aplicativo  
 Se você se conectar a dados locais, não só poderá se conectar a um arquivo de banco de dados como também o integrará ao seu aplicativo.  Por exemplo, você pode abrir o menu **Projeto**, navegar até um arquivo .sdf, .mdf ou .mdb existente e então adicioná0lo a seu projeto.  
  
 Se você adicionar arquivos de dados local, criará um conjunto de dados tipado e uma cadeia de conexão dinâmica que aponta para o arquivo de banco de dados em seu aplicativo.  Quando você adiciona um arquivo de banco de dados ao seu projeto, você usa o **Assistente de Configuração da Fonte de Dados** para especificar os objetos a serem incluídos.  
  
> [!NOTE]
>  Você pode configurar automaticamente sua conexão e iniciar o **Assistente de configuração de origem de dados** arrastando um arquivo .sdf, .mdf, ou .mdb do Explorador de Arquivos para o **Gerenciador de Soluções**.  Você pode então especificar os objetos para usar em seu aplicativo.  
  
 Se você usa o **Assistente de Configuração de Fonte de Dados** para criar a fonte de dados para um arquivo de dados local, será solicitado que você inclua o arquivo no seu projeto.  Se você não incluí\-lo, seu aplicativo conterá somente a cadeia de conexão para a qual o caminho embutido aponta, e não o arquivo de dados real.  Para obter mais informações, consulte [Como gerenciar arquivos de dados locais no projeto](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
 Depois que você concluir o assistente, o arquivo de banco de dados e o dataset aparecem no **Gerenciador de Soluções**\/**Gerenciador de Banco de Dados**, e os objetos de banco de dados especificados aparecem na janela **Fontes de Dados**.  Arrastando os itens da janela **Fontes de Dados** até seu formulário, você poderá criar controles associados aos dados subjacentes.  Para abrir a janela **Fontes de Dados**, abra o menu **Dados** e selecione **Exibir Fontes de Dados**.  Para obter mais informações, consulte [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## Usando um arquivo de banco de dados  
 Antes que você possa usar um arquivo existente de banco de dados \(.mdf\) no Visual Studio, você provavelmente deve converter o arquivo em um arquivo de banco de dados [!INCLUDE[sql_Denali_short](../data-tools/includes/sql_denali_short_md.md)].  Quando você se conecta a um arquivo de banco de dados existente, uma caixa de mensagem pergunta se você deseja atualizar.  
  
> [!IMPORTANT]
>  Se você atualizar o arquivo de banco de dados \(.mdf\), não poderá abri\-lo em uma versão anterior do SQL Server.  
  
 Você não precisa converter o arquivo base de dados \(.mdf\) se **SQL Server Instance Name** for definido como SQLEXPRESS e SQL Server 2008 Express estiver instalado.  O SQL Server 2008 Express está instalado se o Visual Studio 2010 estiver instalado.  Para alterar o nome da instância para este arquivo do banco de dados, abra o Visual Studio, abra a caixa de diálogo **Adicionar Conexão**, especifique `.\SQLEXPRESS` como o nome do servidor e especifique o banco de dados ou o nome do arquivo do banco de dados.  
  
## SQL Server Express LocalDB e SQL Server Express  
 Você pode adicionar um arquivo de base de dados baseado em serviço \(.mdf\) para qualquer projeto no Visual Studio.  Você pode usar designers do Visual Studio para criar tabelas e outros objetos de base de dados, e pode executar consultas.  
  
 Quando você cria um banco de dados baseado em serviço no Visual Studio, ele usa o mecanismo SQL Server Express LocalDB para acessar o arquivo do banco de dados \(.mdf\), onde as versões anteriores do Visual Studio usaram o mecanismo SQL Server Express.  
  
 O SQL Server Express LocalDB é uma versão leve do SQL Server que você pode programar em muitas das mesmas formas que um banco de dados do SQL Server.  O SQL Server Express LocalDB é executado no modo de usuário, e você pode instalá\-lo mais rapidamente e com menos pré\-requisitos e nenhuma configuração.  
  
> [!NOTE]
>  Para obter mais informações sobre o LocalDB do SQL Server Express, consulte [Introdução ao LocalDB, um SQL Express aprimorado](http://go.microsoft.com/fwlink/?LinkId=234375) e [LocalDB: onde está o meu banco de dados?](http://go.microsoft.com/fwlink/?LinkId=234376) no site da Microsoft.  
  
 No Visual Studio, você pode usar o SQL Server Express por padrão em vez do LocalDB do SQL Server Express.  Na barra de menus, escolha **Ferramentas**, **Opções**.  Sob o nó **Ferramentas de Banco de Dados**, escolha **Conexões de Dados**.  Na caixa de texto **Nome da Instância do SQL Server**, insira `SQLEXPRESS`.  Como alternativa, você pode incorporar outros valores para o nome da instância do SQL Server \(por exemplo, `SQL2008`\).  
  
 A tabela a seguir descreve as diferenças entre os mecanismos do SQL Server Express LocalDB e SQL Server Express.  
  
||SQL Server Express LocalDB|SQL Server Express|  
|-|--------------------------------|------------------------|  
|Tipo de banco de dados quando você cria um banco de dados baseado em serviço|No [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] e [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)], SQL Server Express LocalDB|No Visual Studio 2010 e anteriores, SQL Server Express|  
|Nome da instância do SQL Server em Ferramentas\/Opções|\(LocalDB\)\\v11.0|SQLEXPRESS|  
|Valor da fonte de dados na cadeia de conexão|\(LocalDB\)\\v11.0|.\\SQLEXPRESS|  
|Valor de AttachDbFilename na cadeia de conexão|caminho de arquivo|caminho de arquivo|  
|A instância do usuário é necessária \(“Instância do usuário\=Verdadeiro” na cadeia de conexão\)|Não|Sim|  
|Extensão do arquivo de banco de dados|.mdf|.mdf|  
  
## Benefícios do SQL Server Express LocalDB  
  
-   SQL Server Express LocalDB é compatível com edições com base no serviço do SQL Server para recursos que SQL Server Express LocalDB permite.  No SQL Server, você pode mover qualquer banco de dados ou código de Transact\-SQL do SQL Server Express LocalDB para SQL Server ou SQL Azure sem nenhuma etapa de atualização.  Portanto, você pode usar o SQL Server Express LocalDB para desenvolver aplicativos que usam as edições do SQL Server.  
  
-   SQL Server Express LocalDB suporta o mesmo otimizador de consulta e processador de consulta como as edições mais recentes do SQL Server fazem.  
  
## Cada projeto contém duas cópias do banco de dados  
 Quando você cria um projeto, o arquivo de banco de dados pode ser copiado da pasta raiz do projeto para a pasta de saída, **bin**.  Esse comportamento depende da propriedade **Copiar para Diretório de Saída** do arquivo, e o valor padrão dessa propriedade depende do tipo de arquivo de banco de dados que você está usando.  
  
 Para exibir a pasta **bin**, no **Gerenciador de Soluções**, escolha o botão **Mostrar Todos os Arquivos** na barra de ferramentas.  
  
> [!NOTE]
>  A propriedade **Copiar para Diretório de Saída** não é aplicada a Web ou projetos C\+\+.  
  
 O arquivo banco de dados na sua pasta raiz do projeto é alterado ao editar o esquema do banco de dados ou dados usando o **Gerenciador de Servidores**, **Gerenciador de Bancos de Dados**, ou outros [Visual Database Tools](http://msdn.microsoft.com/pt-br/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 À medida que você altera os dados durante o desenvolvimento de aplicativos, você está alterando a base de dados na pasta **bin**.  Por exemplo, quando você pressiona a tecla F5 para depurar seu aplicativo, você está conectado ao banco de dados nessa pasta.  
  
|Valor de propriedade **Copiar para Diretório de Saída**|Comportamento|  
|-------------------------------------------------------------|-------------------|  
|**Copiar se mais recente** \(valor padrão para arquivos .sdf\)|O arquivo de banco de dados é copiado do diretório projeto para o diretório **bin** na primeira vez que você compilar o projeto.  A propriedade **Data de Modificação** dos arquivos é comparada sempre que você compilar novamente o projeto.  Se o arquivo na pasta de projeto for mais recente, ele é copiado para a pasta **bin**, substituindo o arquivo anterior.  Caso contrário, nenhum arquivo será copiado. **Caution:**  Não recomendamos este valor para arquivos .mdb ou .mdf.  O arquivo de banco de dados pode ser alterado mesmo que os dados não sejam alterados.  O arquivo pode ser marcada como mais recente se você simplesmente abrir uma conexão \(por exemplo, expandir o nó de **Tabelas** no **Gerenciador de Soluções**\).|  
|**Copiar sempre** \(valor padrão para arquivos .mdf e .mdb\)|O arquivo de banco de dados é copiado do diretório projeto para o diretório **bin** sempre que você criar seu aplicativo.  Quaisquer alterações feitas no arquivo de dados na pasta de saída serão sobrescritas na próxima vez que você executar o aplicativo.|  
|**Não copiar**|O sistema nunca sobrescreve o arquivo no diretório de **bin**.  Seu aplicativo cria uma cadeia caracteres de conexão dinâmica que aponta para o arquivo base de dados no diretório de saída.  Portanto, você deve copiar manualmente o arquivo para o diretório de saída se desejar que os dados no diretório de saída correspondam com os dados no diretório do projeto.|  
  
## Problemas comuns com os dados locais  
 A tabela a seguir explica os problemas comuns que você pode encontrar quando trabalha com arquivos de dados locais.  
  
|Problema|Explicação|  
|--------------|----------------|  
|Sempre que testar meu aplicativo e modificar dados, minhas alterações são perdidas na próxima vez que eu executar o aplicativo.|O valor da propriedade **Copiar para Diretório de Saída** é como **Copiar se for mais novo** ou **Copiar sempre**.  O banco de dados na sua pasta de saída \(o banco de dados que está sendo modificado ao testar seu aplicativo\) é substituído sempre que você compila seu projeto.  Para obter mais informações, consulte [Como gerenciar arquivos de dados locais no projeto](../data-tools/how-to-manage-local-data-files-in-your-project.md).|  
|Uma mensagem aparece, informando que o arquivo de dados está bloqueado.|Acesso \(arquivos.mdb\): verificar que o arquivo não esteja aberto em outro programa como Access.<br /><br /> SQL Server Express \(arquivos .mdf\): SQL Express bloqueia o arquivo de dados se você tentar copiá\-lo, movê\-lo ou renomeá\-lo fora da IDE do Visual Studio.|  
|O acesso é negado quando mais de um usuário tenta acessar ao mesmo tempo o mesmo banco de dados.|Visual Studio se beneficia de *instâncias de usuário*, um recurso do SQL Server Express que cria uma instância separada do SQL Server para cada usuário.  Após um usuário acessar o arquivo, quaisquer usuários subsequentes não poderão se conectar.  Esse problema pode ocorrer se, por exemplo, se você tentar executar um aplicativo da Web no servidor de desenvolvimento do ASP.NET e IIS ao mesmo tempo, porque o IIS geralmente executa em uma conta diferente.|  
  
## Consulte também  
 [Instruções passo a passo: conectando a dados em um arquivo de banco de dados local \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Local%20Database%20File%20\(Windows%20Forms\).md)   
 [Instruções passo a passo: conectando a dados em um banco de dados do Access \(Windows Forms\)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)