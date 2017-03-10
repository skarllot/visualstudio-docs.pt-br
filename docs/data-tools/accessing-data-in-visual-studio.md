---
title: "Acessando dados no Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "80025080"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "ADO.NET, acesso a dados"
  - "dados [C#]"
  - "dados [Visual Studio]"
  - "acesso a dados [Visual Studio]"
ms.assetid: 9812a6d5-23d2-4427-8b98-70a2abfec3bc
caps.latest.revision: 100
caps.handback.revision: 81
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Acessando dados no Visual Studio
No Visual Studio, você pode criar aplicativos que se conectam aos dados de praticamente qualquer produto de banco de dados ou serviço, em qualquer formato, de qualquer lugar\-\- em um computador local, em um servidor de rede local ou na nuvem.  
  
 Para aplicativos em JavaScript, Python, PHP, Ruby ou C\+\+, você se conectar a dados como qualquer outra coisa, obtendo bibliotecas e escrever código. Para aplicativos .NET, Visual Studio fornece ferramentas que permitem que você explore as fontes de dados, criar modelos de objeto para armazenar e manipular os dados na memória e vincular dados à interface do usuário.     Microsoft Azure fornece SDKs para .NET, Java, Node. js, PHP, Python, Ruby e aplicativos móveis e ferramentas no Visual Studio para se conectar ao armazenamento do Azure.  
  
 A tabela a seguir mostra algumas as muitos sistemas de armazenamento e banco de dados podem ser usados no Visual Studio.  
  
||||  
|-|-|-|  
|**Microsoft Azure \(SQL e NoSQL\)**|||  
|Banco de dados SQL \(Azure\)|Armazenamento do Azure \(Blobs, tabelas, filas, arquivos\)|SQL Data Warehouse \(Azure\)|  
|Banco de dados do SQL Server \(Azure\)|StorSimple \(Azure\)|Documentos \(Azure\)|  
|Cache Redis do Azure|||  
|**SQL**|||  
|SQL Server 2005 \* \- 2016|MySQL|Oracle|  
|Firebird|PostgreSQL|SQLite|  
|**NoSQL**|||  
|MongoDB|Apache Cassandra|NDatabase|  
|OrientDB|RavenDB|VelocityDB|  
  
 As ofertas do Microsoft Azure na tabela anterior são serviços de banco de dados completo. A maioria dos outros sistemas, incluindo o SQL Server, pode ser hospedada no Azure em uma máquina virtual.  
  
 Muitos fornecedores de banco de dados e terceiros suporte para integração do Visual Studio com pacotes do NuGet. Você pode explorar as ofertas em nuget.org ou por meio do Gerenciador de pacotes do NuGet no Visual Studio \(**Ferramentas &#124; O NuGet Package Manager &#124; Gerenciar pacotes NuGet para solução**\). Outros produtos de banco de dados integram ao Visual Studio como uma extensão.   Você pode procurar essas ofertas na Galeria do Visual Studio, navegando até **Ferramentas &#124; Extensões e atualizações** e, em seguida, escolhendo **Online** no painel esquerdo da caixa de diálogo.  
  
> [!NOTE]
>  O suporte estendido para o SQL Server 2005 termina em 12 de abril de 2016.   Não há nenhuma garantia de que as ferramentas de dados no Visual Studio 2015 e posteriormente continuarão a funcionar com o SQL Server 2005 após essa data. Para obter mais informações, consulte o [final do anúncio de suporte para o SQL Server 2005](https://www.microsoft.com/en-us/server-cloud/products/sql-server-2005/).  
  
### Plataforma Universal do Windows  
 UWP aplicativos em c\# ou Visual Basic podem usar o SDK do Microsoft Azure para .NET para acessar o armazenamento do Azure e outros serviços do Azure. A classe Windows.Web.HttpClient permite a comunicação com qualquer serviço RESTful. Para obter mais informações, consulte [como se conectar a um servidor HTTP usando Windows.Web.Http](https://msdn.microsoft.com/en-us/library/windows/apps/dn469430.aspx)  
  
 Armazenamento de dados no computador local, a abordagem recomendada é usar o SQLite, que é executado no mesmo processo que o aplicativo. Se uma camada ORM for necessária, você pode usar o Entity Framework. Para obter mais informações, consulte [acesso a dados](https://msdn.microsoft.com/windows/uwp/data-access/index) no Centro de desenvolvedores do Windows.  
  
### Linguagens .NET  
 Qualquer acesso a dados .NET, incluindo o .NET Core, baseia\-se no ADO.NET, um conjunto de classes que define uma interface para acessar qualquer tipo de fonte de dados relacional e não relacionais. O Visual Studio tem várias ferramentas e designers que trabalham com o ADO.NET para ajudá\-lo a se conectar a bancos de dados, manipular os dados na memória e apresentar os dados para o usuário. A documentação nesta seção descreve como usar essas ferramentas. Você também pode programar diretamente em objetos de comando do ADO.NET. Para obter mais informações sobre como chamar as APIs do ADO.NET diretamente, consulte [ADO.NET](https://msdn.microsoft.com/en-us/library/e80y5yhx\(v=vs.110\).aspx) na biblioteca MSDN.  
  
 Para documentação de acesso a dados relacionados especificamente ao **ASP.NET**, consulte  [Trabalhando com dados](http://www.asp.net/web-forms/overview/presenting-and-managing-data) no site do ASP.NET. Para obter um tutorial sobre como usar o Entity Framework com o ASP.NET MVC, consulte [Introdução ao Entity Framework 6 Code First usando MVC 5](http://www.asp.net/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).  
  
 Se você estiver se conectando aos serviços do Azure, certifique\-se de baixar a versão mais recente [ferramentas SDK do Azure](https://azure.microsoft.com/en-us/downloads/).  
  
#### Provedores de dados  
 Para um banco de dados a ser utilizado no ADO.NET, ele deve ter um personalizado *provedor de dados ADO.NET* ou else deve expor uma interface ODBC ou OLE DB. A Microsoft fornece provedores de dados ADO.NET para produtos do SQL Server, bem como provedores ODBC e OLE DB.[Você pode encontrar uma lista de provedores de dados aqui.](https://msdn.microsoft.com/en-us/data/dd363565).  
  
#### Modelagem de dados  
 No .NET, você tem três opções de modelagem e manipulação de dados na memória depois de recuperá\-la de uma fonte de dados:  
  
 Entity Framework  
 A tecnologia de mapeamento relacional de objeto Microsoft preferida. Permite que você programe em relação aos dados relacionais como objetos do .NET de primeira classe. Novos aplicativos, ele deve ser considerado como a primeira opção padrão quando um modelo é necessário. Requer suporte personalizado do provedor do ADO.NET subjacente.  
  
 LINQ to SQL  
 Um mapeador relacional de objetos da geração anterior. Ele funciona bem para cenários menos complexos, mas não está mais no desenvolvimento ativo.  
  
 Conjuntos de dados  
 O mais antigo dos três tecnologias de modelagem. Ele destina\-se principalmente para desenvolvimento rápido de aplicativos "formulários sobre dados" no qual você não é enormes quantidades de dados de processamento ou executar consultas complexas ou transformações. Um objeto de conjunto de dados é composto de DataTables e DataRows logicamente semelhantes a objetos de banco de dados SQL muito mais do que objetos .NET. Para aplicativos relativamente simples com base em fontes de dados SQL, datasets ainda pode ser uma boa opção.  
  
 Não há nenhum requisito para usar qualquer uma dessas tecnologias. Em alguns cenários, especialmente quando o desempenho é crítico, você pode simplesmente usar um DataReader para ler do banco de dados e copie os valores que necessários para um objeto de coleção como List \< T \>.  
  
### C\+\+ nativo  
 Aplicativos C\+\+ que se conectar ao SQL Server devem usar o [SQL Native Client](https://msdn.microsoft.com/en-us/sqlserver/aa937733.aspx) você pode acessar outros bancos de dados usando [ODBC](https://msdn.microsoft.com/en-us/library/ms710252\(v=vs.85\).aspx) ou drivers de OLE DB diretamente. O ODBC é a interface padrão do banco de dados atual, mas a maioria dos sistemas de banco de dados fornecem funcionalidade personalizada que não pode ser acessada por meio da interface do ODBC.  OLE DB é uma tecnologia de acesso de dados COM legados que ainda tem suporte, mas não é recomendada para novos aplicativos.  Para obter mais informações, consulte [de acesso a dados no Visual C\+\+](https://msdn.microsoft.com/en-us/library/7wtdsdkh.aspxMicrosoft).  
  
 Programas do C\+\+ que consumirem serviços REST podem usar o [C\+\+ REST SDK](https://github.com/Microsoft/cpprestsdk).  
  
 Programas do C\+\+ que funcionam com o armazenamento do Microsoft Azure podem usar o [cliente de armazenamento do Microsoft Azure](http://www.nuget.org/packages/wastorage).  
  
#### Modelagem de dados  
 Visual Studio não fornece uma camada de mapeamento relacional de objeto para C\+\+.[ODB](http://www.codesynthesis.com/products/odb/) é um ORM do código\-fonte aberto popular para C\+\+.  
  
 Para obter mais informações sobre tecnologias de acesso a dados herdadas do Visual C\+\+, consulte  [Acesso a dados](../Topic/Data%20Access%20in%20Visual%20C++.md)  
  
### JavaScript  
 [JavaScript no Visual Studio](https://msdn.microsoft.com/en-us/library/hh334522.aspx) é uma linguagem de primeira classe para a criação de aplicativos de plataforma cruzada, UWP aplicativos, serviços de nuvem, sites e aplicativos web. Você pode usar Bower, Grunt, Gulp, npm e claro NuGet no Visual Studio para instalar seu favoritas bibliotecas Javascript e produtos de banco de dados. Conecte ao armazenamento do Azure e serviços baixando SDKs do windowsazure.com.  Edge.js é uma biblioteca Javascript do lado do servidor \(Node. js\) conecta\-se a fontes de dados do ADO.NET.  
  
### Python  
 Instalar  [Ferramentas Python para Visual Studio](http://microsoft.github.io/PTVS/) juntamente com sua estrutura de Python favorita para criar aplicativos CPython ou IronPython \(.NET\).  O site do PTVS tem vários tutoriais sobre como se conectar a dados, inclusive [Django e banco de dados do SQL Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure), [Django e MySQL no Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure) e [Bottle e MongoDB no Azure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure).  
  
## Nesta seção  
 [Instalar sistemas de banco de dados, ferramentas e exemplos](../data-tools/installing-database-systems-tools-and-samples.md)  
 Discute como obter produtos de banco de dados e as extensões do Visual Studio ou drivers que oferecem suporte a eles e onde encontrar os bancos de dados de exemplo para experimentação e fins de aprendizagem.  
  
 [Ferramentas de dados do Visual Studio para .NET](http://msdn.microsoft.com/pt-br/6b145922-2f00-47db-befc-bf351b4809a1)  
 Descreve como usar janelas de ferramentas do Visual Studio para se conectar a fontes de dados, criar conjuntos de dados ou entidade modelos do framework e associar os dados a controles de interface do usuário.  
  
## Tópicos relacionados  
 [Dados, dispositivos e análise](https://msdn.microsoft.com/en-us/data-and-devices)  
 Introdução à nuvem inteligente da Microsoft, incluindo suporte para Internet das coisas e Cortana Analytics Suite.  
  
 [Armazenamento do Microsoft Azure](https://azure.microCsoft.com/en-us/documentation/services/storage/)  
 Descreve o armazenamento do Azure e como criar aplicativos que usam arquivos, tabelas, filas e blobs do Azure.  
  
 [Banco de dados do SQL Azure](https://azure.microsoft.com/en-us/documentation/services/sql-database/)  
 Descreve como se conectar ao banco de dados do SQL Azure, um banco de dados\-como\-serviço relacional.  
  
 [Ferramentas de banco de dados do SQL Server](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx)  
 Descreve as ferramentas que simplificam o design, exploração, teste e implantação de bancos de dados e aplicativos conectados a dados.  
  
 [ADO.NET](../Topic/ADO.NET.md)  
 Descreve a arquitetura do ADO.NET e como usar as classes ADO.NET para gerenciar dados de aplicativo e interagir com fontes de dados e XML.  
  
 [ADO.NET Entity Framework](https://msdn.microsoft.com/en-us/data/ef)  
 Descreve como criar aplicativos de dados que permitem aos desenvolvedores de programas em um modelo conceitual em vez de diretamente em um banco de dados relacional.  
  
 [WCF Data Services 4.5](../Topic/WCF%20Data%20Services%204.5.md)  
 Descreve como usar [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] para implantar serviços de dados na Web ou em uma intranet que implementam o [Open Data Protocol \(OData\)](http://go.microsoft.com/fwlink/?LinkID=182204).  
  
 [Dados em soluções do Office](/office-dev/office-dev/data-in-office-solutions)  
 Contém links para tópicos que explicam como dados funcionam em soluções do Office. Isso inclui informações sobre programação orientada a esquema, caching de dados e acesso a dados do lado do servidor.  
  
 [LINQ \(Consulta Integrada à Linguagem\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)  
 Descreve os recursos de consulta incorporados em c\# e Visual Basic e o modelo comum para consultar bancos de dados relacionais, documentos XML, conjuntos de dados e coleções na memória.  
  
 [Ferramentas XML no \(Visual Studio\)](../xml-tools/xml-tools-in-visual-studio.md)  
 Discute como trabalhar com dados XML, depuração XSLT, recursos XML do .NET Framework e arquitetura de consulta XML.  
  
 [XML Documents and Data](../Topic/XML%20Documents%20and%20Data.md)  
 Fornece uma visão geral de um conjunto abrangente e integrado de classes que funcionam com documentos XML e dados no .NET Framework.