---
title: "Como se conectar ao banco de dados Northwind | Microsoft Docs"
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
  - "conexões [Visual Studio], banco de dados Northwind"
  - "banco de dados de exemplo Northwind"
ms.assetid: cc6cb79f-d035-41f8-b398-8d4a45922bfb
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Como se conectar ao banco de dados Northwind
À medida que aprender a criar aplicativos de banco de dados usando o Visual Studio, você precisará se conectar ao banco de dados Northwind para seguir vários dos exemplos na documentação desse produto.  Dependendo do exemplo seguido, você se conectará ao banco de dados no SQL Server ou em um arquivo de banco de dados, tal como o Microsoft Access ou o SQL Server.  
  
## Criando conexões de dados com o banco de dados Northwind  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Para criar uma conexão de dados com o banco de dados Northwind \(SQL Server\)  
  
1.  No menu **Exibir**, escolha **Gerenciador de Servidores**\/**Gerenciador de Banco de Dados**.  
  
2.  No **Gerenciador de Servidores**\/**Gerenciador de Banco de Dados**, abra o menu de atalho para **Conexões de Dados** e escolha **Adicionar Conexão**.  
  
     Depois de escolher **Adicionar Conexão**, a caixa de diálogo **Escolher Fonte de Dados** ou **Adicionar Conexão** será exibida.  
  
3.  Se a caixa de diálogo **Escolher Fonte de Dados** for exibida, escolha **Microsoft SQL Server** e **OK**.  
  
     Se a caixa de diálogo **Adicionar Conexão** aparecer e **Fonte de dados** não for **Microsoft SQL Server \(SqlClient\)**, escolha o botão **Alterar** para abrir a caixa de diálogo **Alterar Fonte de Dados**, escolha **Microsoft SQL Server** e **OK**.  
  
4.  Na lista **Nome do servidor**, especifique o nome do servidor no qual o banco de dados Northwind está localizado.  
  
5.  Dependendo dos requisitos de sua versão do SQL Server e do banco de dados Northwind, escolha **Usar Autenticação do Windows** ou **Usar Autenticação do SQL Server** e insira um nome de usuário e uma senha para fazer logon no computador que está executando o SQL Server.  
  
6.  Escolha o banco de dados Northwind na lista **Selecionar ou digitar um nome de banco de dados**.  
  
7.  Escolha **Testar Conexão** para verificar a conectividade com o banco de dados Northwind.  
  
8.  Escolha **OK**.  
  
     Uma conexão de dados com o banco de dados Northwind é adicionada ao **Gerenciador de Servidores**\/**Gerenciador de Banco de Dados**.  
  
 Além de conectar a uma instância remota de um banco de dados do SQL Server, também é possível se conectar diretamente aos arquivos reais que contêm o banco de dados.  Isso permite que você adicione os arquivos de banco de dados diretamente em um projeto em que eles possam ser implantados como parte do aplicativo.  No momento, há suporte para os seguintes arquivos de banco de dados local: arquivos de bancos de dados do SQL Server Compact \(.sdf\), arquivos de banco de dados do [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] e do SQL Server Express \(.mdf\) e arquivos de bancos de dados do Microsoft Access \(.mdb ou .accdb\).  
  
#### Para criar uma conexão de dados com o banco de dados Northwind – arquivo de banco de dados do SQL Server \(.mdf\)  
  
1.  No menu **Exibir**, escolha **Gerenciador de Servidores**\/**Gerenciador de Banco de Dados**.  
  
2.  No **Gerenciador de Servidores**\/**Gerenciador de Banco de Dados**, abra o menu de atalho para **Conexões de Dados** e escolha **Adicionar Conexão**.  
  
     Depois de escolher **Adicionar Conexão**, a caixa de diálogo **Adicionar Conexão** ou **Escolher Fonte de Dados** será exibida.  
  
3.  Se a caixa de diálogo **Escolher Fonte de Dados** for exibida, selecione **Arquivo de Banco de Dados do Microsoft SQL Server** e escolha **OK**.  
  
4.  Se a caixa de diálogo **Adicionar Conexão** for exibida, verifique se **Fonte de dados** está definida como **Arquivo de Banco de Dados do Microsoft SQL Server \(SqlClient\)**.  Se ela não estiver definida como **Arquivo de Banco de Dados do Microsoft SQL Server \(SqlClient\)**, escolha **Alterar** para abrir a caixa de diálogo **Alterar Fonte de Dados**, escolha **Arquivo de Banco de Dados do Microsoft SQL Server** e **OK**.  
  
5.  Escolha **Procurar** para encontrar o arquivo .mdf que contém o banco de dados Northwind.  
  
6.  Dependendo dos requisitos de sua versão do Northwind e do banco de dados Northwind, escolha **Usar Autenticação do Windows** ou **Usar Autenticação do SQL Server** e insira um nome de usuário e uma senha para fazer logon no computador que está executando o SQL Server.  
  
7.  Escolha o botão **OK**.  
  
     Uma conexão de dados com o banco de dados Northwind é adicionada ao **Gerenciador de Servidores**\/**Gerenciador de Banco de Dados**.  
  
> [!NOTE]
>  [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] possui alterações que se aplicam ao arquivo de banco de dados Northwind \(.mdf\).  Para obter informações, consulte [Como instalar bancos de dados de exemplo](../data-tools/how-to-install-sample-databases.md).  
  
#### Para criar uma conexão de dados com o banco de dados Northwind – arquivo de banco de dados do Access \(.mdb ou .accdb\)  
  
1.  No menu **Exibir**, escolha **Gerenciador de Servidores**\/**Gerenciador de Banco de Dados**.  
  
2.  No **Gerenciador de Servidores**\/**Gerenciador de Banco de Dados**, abra o menu de atalho para **Conexões de Dados** e escolha **Adicionar Conexão**.  
  
     Depois de escolher **Adicionar Conexão**, a caixa de diálogo **Adicionar Conexão** ou **Escolher Fonte de Dados** será exibida.  
  
3.  Se a caixa de diálogo **Escolher Fonte de Dados** for exibida, selecione **Arquivo do Banco de Dados do Microsoft Access** e escolha **OK**.  
  
4.  Se a caixa de diálogo **Adicionar Conexão** for exibida, verifique se a **Fonte de dados** está definida como **Arquivo de Banco de Dados do Microsoft Access**.  Se ela não estiver definida como **Arquivo de Banco de Dados do Microsoft Access**, escolha **Alterar** para abrir a caixa de diálogo **Alterar Fonte de Dados**, escolha **Arquivo de Banco de Dados do Microsoft Access** e **OK**.  
  
5.  Escolha **Procurar** para encontrar o arquivo .mdb ou .accdb que contém o banco de dados Northwind.  
  
6.  Insira um nome de usuário e uma senha caso sua versão do banco de dados Northwind exija.  
  
7.  Escolha **OK**.  
  
     Uma conexão de dados com o banco de dados Northwind é adicionada ao **Gerenciador de Servidores**\/**Gerenciador de Banco de Dados**.  
  
## Consulte também  
 [Como instalar bancos de dados de exemplo](../data-tools/how-to-install-sample-databases.md)   
 [programação de dados com o Microsoft Access 2010](http://msdn.microsoft.com/library/office/ff965871.aspx)   
 [Instruções passo a passo de dados](../Topic/Data%20Walkthroughs.md)