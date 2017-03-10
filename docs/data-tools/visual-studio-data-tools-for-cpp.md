---
title: "Ferramentas de dados do Visual Studio para C++ | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a3849d9-1bc7-47d1-805e-1755223ccba2
caps.latest.revision: 9
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Ferramentas de dados do Visual Studio para C++
C\+\+ nativo com freqüência pode fornecer o desempenho mais rápido ao acessar fontes de dados. No entanto, os dados das ferramentas para aplicativos do C\+\+ no Visual Studio não são tão avançados quanto para aplicativos .NET. Por exemplo, as janelas de fontes de dados não podem ser usadas para arrastar e soltar fontes de dados em uma superfície de design de C\+\+. Se você precisar de uma camada de objeto relacional, você precisará escrever sua própria ou então usar um produto de terceiros.  O mesmo vale para a funcionalidade de associação de dados, embora os aplicativos MFC podem usar as classes de banco de dados como CDatabase e CRecordset e CRecordview junto com documentos e exibições para armazenar dados na memória e exibi\-lo ao usuário. Para obter mais informações, consulte [acesso a dados no Visual C\+\+](https://msdn.microsoft.com/en-us/library/7wtdsdkh.aspx) .  
  
 Para se conectar a bancos de dados SQL, os aplicativos nativos do C\+\+ podem usar os drivers ODBC e OLE DB e o provedor ADO que estão incluídos no Windows.     Eles podem se conectar a qualquer banco de dados que oferece suporte a essas interfaces. O driver ODBC é o padrão. OLE DB é fornecido para compatibilidade com versões anteriores. Para obter mais informações sobre essas tecnologias de dados, consulte [Windows Data Access Components](https://msdn.microsoft.com/en-us/library/windows/desktop/aa968814\(v=vs.85\).aspx)  
  
 Para tirar proveito da funcionalidade personalizada no SQL Server 2005 e posterior, use o [SQL Server Native Client](https://msdn.microsoft.com/en-us/sqlserver/aa937733). O native client também contém o driver ODBC do SQL Server e o provedor OLE DB do SQL Server em uma biblioteca de vínculo dinâmico \(DLL\) com suporte a aplicativos que usam APIs de código nativo \(ODBC, OLE DB e ADO\) para o Microsoft SQL Server.  SQL Server Native Client é instalado com o SQL Server Data Tools. O guia de programação está aqui: [SQL Server Native Client de programação](https://msdn.microsoft.com/en-us/library/ms130892.aspx).  
  
## Para conectar\-se ao localDB via ODBC e SQL Native Client em um aplicativo C\+\+  
  
1.  Instale o SQL Server Data Tools.  
  
2.  Se você precisar de um banco de dados SQL de exemplo para se conectar ao, baixe o banco de dados Northwind e descompacte\-o em um novo local.  
  
3.  Use o SQL Server Management Studio para anexar o arquivo mdf descompactado para o localDB. Quando o SSMS é iniciado, se conecte ao \(localdb\) \\MSSQLLocalDB.  
  
     ![SSMS connect dialog](../data-tools/media/raddata-ssms-connect-dialog.png "raddata SSMS connect dialog")  
  
     Em seguida, clique com botão direito no nó do localdb na página esquerda e escolha anexar.  
  
     ![SSMS Attach database](../data-tools/media/raddata-ssms-attach-database.png "raddata SSMS Attach database")  
  
4.  Baixe o exemplo de SDK do Windows ODBC e descompacte para um novo local. Este exemplo mostra os comandos básicos do ODBC que são usados para se conectar a um banco de dados e emitir consultas e comandos. Você pode aprender mais sobre essas funções no [Microsoft ODBC Open Database Connectivity \(\)](https://msdn.microsoft.com/en-us/library/windows/desktop/ms710252\(v=vs.85\).aspx). Quando você carrega primeiro a solução \(está na pasta C\+\+\), o Visual Studio oferecerá para atualizar a solução para a versão atual do Visual Studio. Clique em Sim.  
  
5.  Para usar o native client, você precisa de seu arquivo de cabeçalho e o arquivo lib que contêm funções e definições específicas para o SQL Server, além de funções ODBC definidas no SQL. Em **projeto &#124; Propriedades &#124; Diretórios VC \+ \+**, adicione o seguinte incluir diretório:  
  
 **\< unidade do sistema \>: \\Program Files\\Microsoft Server\\110\\SDK\\Include SQL**     E esse diretório de biblioteca:  
  
 **c:\\Program Files\\Microsoft SQL Server\\110\\SDK\\Lib**  
  
6.  Adicione essas linhas em odbcsql.cpp, o \#define impede irrelevantes definições de OLE DB do que está sendo compilado:  
  
    ```  
    #define _SQLNCLI_ODBC_  
    #include <sqlncli.h>  
    ```  
  
     Observe que o exemplo não usa realmente qualquer funcionalidade cliente nativo, portanto, as etapas anteriores não são necessárias compilar e executar, mas o projeto agora está configurado para usar essa funcionalidade. Consulte [SQL Server Native Client de programação](https://msdn.microsoft.com/en-us/library/ms130892\(v=sql.130\).aspx)para obter mais informações.  
  
7.  Precisamos dizer ao subsistema ODBC qual driver usar. O exemplo passa o atributo de cadeia de caracteres de conexão do DRIVER em como um argumento de linha de comando. Em **projeto &#124; Propriedades &#124; Depuração** adicione este argumento de comando:  
  
    ```  
    DRIVER="SQL Server Native Client 11.0"  
    ```  
  
8.  Pressione F5 para compilar e executar o aplicativo. Você deve ver uma caixa de diálogo do driver que solicita que você insira um banco de dados. Digite `(localdb) \MSSQLLocalDB` e verificar **Usar conexão confiável**. Pressione OK. Você deve ver um console com mensagens indicando uma conexão bem\-sucedida e um prompt de comando onde você pode digitar em uma instrução SQL. A tela a seguir mostra um exemplo de consulta e os resultados:  
  
     ![ODBC Sample query output](../data-tools/media/raddata-odbc-sample-query-output.png "raddata ODBC Sample query output")  
  
## Consulte também  
 [Acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)