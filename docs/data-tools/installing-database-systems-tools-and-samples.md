---
title: "Instalar sistemas de banco de dados, ferramentas e exemplos | Microsoft Docs"
ms.custom: ""
ms.date: "09/16/2016"
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
  - "bancos de dados de exemplo"
  - "bancos de dados, exemplos"
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
caps.latest.revision: 28
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Instalar sistemas de banco de dados, ferramentas e exemplos
Visual Studio não inclui quaisquer sistemas de banco de dados que não sejam aqueles que usa internamente. Para desenvolver um aplicativo conectado por dados no Visual Studio, você normalmente instala o sistema de banco de dados no seu computador de desenvolvimento e, em seguida, implantar o aplicativo e o banco de dados em um ambiente de produção quando estiverem prontas. O sistema de banco de dados deve ter um provedor de dados ADO.NET em ordem para que ele seja acessado de aplicativos .NET e fique visível nas janelas de ferramentas de dados do Visual Studio. Um provedor deve suportar especificamente o Entity Framework se você planeja usar os modelos de dados de entidade em seu aplicativo .NET.     Muitos provedores são oferecidos por meio do Gerenciador de pacotes do NuGet ou por meio da Galeria do Visual Studio.  
  
 Para o desenvolvimento do SQL, certifique\-se de que você tenha o SQL Server Data Tools instalado no Visual Studio. Clique no menu Exibir. Se você não vir o Pesquisador de objetos do SQL Server, em seguida, vá para painel de controle e altere o Visual Studio. O instalador, verifique **Microsoft SQL Server Data Tools**.  
  
 Se você estiver usando APIs de armazenamento do Azure, instale os emuladores do armazenamento do Azure em sua máquina local durante o desenvolvimento para evitar encargos até estar pronto para implantar na produção. Para obter mais informações, consulte [usar o emulador de armazenamento do Azure para desenvolvimento e teste](https://azure.microsoft.com/en-us/documentation/articles/storage-use-emulator/).  
  
## Instalar as ferramentas, drivers e produtos de banco de dados SQL  
 A lista a seguir inclui alguns dos mais populares sistemas de banco de dados que podem ser usados em projetos do Visual Studio. A lista não é exaustiva. Para obter a lista de fornecedores que oferecem provedores de dados ADO.NET que permitem a total integração com ferramentas do Visual Studio, consulte [provedores de dados ADO.NET](https://msdn.microsoft.com/en-us/library/dd363565.aspx).  
  
### Microsoft SQL Server  
 O SQL Server é da Microsoft oferta de banco de dados principal. SQL Server 2016 fornece desempenho inovador, segurança avançada e rico e integrado, relatórios e análises. Ele é fornecido em várias edições, que são projetadas para usos diferentes de análise empresarial altamente escalonável e de alto desempenho, para usar em um único computador. SQLExpress é uma edição completa do SQL Server que seja adequado para redistribuição e incorporação.  O LocalDB é uma edição simplificada do SQLExpress que não requer nenhuma configuração e é executado no processo do aplicativo. Você pode baixar um ou ambos os produtos de [página de download do SQLExpress](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx).    Muitos dos exemplos nesta seção SQL usam LocalDB do SQL Server. SQL Server Management Studio \(SSMS\) é um aplicativo de gerenciamento de banco de dados autônomo que possui mais funcionalidade que é fornecido no Visual Studio SQL Server Object Explorer. Você pode obter o SSMS do mesmo link acima.  
  
### Oracle  
 Você pode baixar uma edição gratuita ou paga do banco de dados Oracle do [Oracle Technology Network](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) página. Para suporte em tempo de design para adaptadores de tabela e o Entity Framework, será necessário o [Oracle Developer Tools for Visual Studio](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html). Outros produtos oficiais da Oracle, incluindo o Oracle Instant Client estão disponíveis por meio de **NuGet Package Manager**.  Você pode baixar esquemas de exemplo do Oracle seguindo as instruções de [documentação on\-line Oracle](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm)  
  
### MySQL  
 O MySQL é um sistema de banco de dados de código\-fonte aberto popular é amplamente usado em empresas e sites. Downloads para MySQL, MySQL do Visual Studio e produtos relacionados, estão em [MySQL no Windows](http://www.mysql.com/why-mysql/windows/).  Terceiros oferecem várias extensões do Visual Studio e autônomo aplicativos de gerenciamento para MySQL. Você pode procurar as ofertas no Gerenciador de pacotes do NuGet \(**Ferramentas &#124; O NuGet Package Manager &#124; Gerenciar pacotes NuGet para solução**\).  
  
### PostgreSQL  
 PostgreSQL é um sistema de banco de dados relacional de objeto de código\-fonte aberto gratuita. A página de download para instalar o Windows está aqui..  Você também pode criar PostgresSQL do código\-fonte.  O sistema de núcleo PostgreSQL inclui uma interface de linguagem C. Muitos terceiros fornecem pacotes NuGet para usar o PostgreSQL nos aplicativos .NET.  Você pode procurar as ofertas no Gerenciador de pacotes do NuGet \(**Ferramentas &#124; O NuGet Package Manager &#124; Gerenciar pacotes NuGet para solução**\). Talvez o pacote mais popular é fornecido por [npgsql.org](http://www.npgsql.org).  
  
### SQLite  
 SQLite é um mecanismo de banco de dados SQL inserido que é executado no processo do aplicativo. Você pode baixá\-lo do [página de Download do SQLLite](http://www.sqlite.org/download.html). Muitos pacotes do NuGet de terceiros para SQLLite também estão disponíveis. Você pode procurar as ofertas no Gerenciador de pacotes do NuGet \(**Ferramentas &#124; O NuGet Package Manager &#124; Gerenciar pacotes NuGet para solução**\).  
  
### Firebird  
 Firebird é um sistema de banco de dados SQL do código\-fonte aberto. Você pode baixá\-lo do [página de download de Firebird](http://firebirdsql.org/en/downloads/). Um provedor de dados ADO.NET está disponível por meio do Gerenciador de pacotes do NuGet.  
  
## Consulte também  
 [Como determinar a versão e edição do SQL Server e seus componentes](http://support.microsoft.com/kb/321185)