---
title: "Como instalar bancos de dados de exemplo | Microsoft Docs"
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
  - "banco de dados de exemplo AdventureWorks"
  - "dados [Visual Studio], bancos de dados de exemplo"
  - "banco de dados de exemplo Northwind"
  - "bancos de dados de exemplo, Adventure Works"
  - "bancos de dados de exemplo, Northwind"
ms.assetid: ed1291f6-604c-4972-ae22-0345c6dea12e
caps.latest.revision: 56
caps.handback.revision: 56
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Como instalar bancos de dados de exemplo
Muitos exemplos de dados exigem a capacidade de conectar\-se ao Northwind, Pubs, bancos de dados de exemplo andAdventureWorks.  Você pode instalar e conectar\-se a esses bancos de dados usando os procedimentos a seguir.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Instalando os bancos de dados  
 Muitos exemplos de dados exigem a disponibilidade dos bancos de dados de exemplo que podem ser baixados de sites da web.  Os bancos de dados de exemplo incluem os bancos de dados AdventureWorks, Northwind e Pubs.  
  
#### Para instalar os bancos de dados de exemplo Northwind e Pubs para o SQL Server  
  
1.  Acesse o site [Bancos de dados de exemplo Northwind e Pubs](http://go.microsoft.com/fwlink?linkid=64296).  
  
2.  Baixe e execute o instalador.  
  
     O instalador adiciona uma pasta **Bancos de Dados de Exemplo do SQL Server 2000** na pasta raiz do seu computador.  \(Por exemplo: **C:\\SQL Server 2000 Sample Databases**\).  
  
3.  Localize o script SQL para o banco de dados desejado, Northwind ou Pubs.  
  
    > [!WARNING]
    >  O arquivo de banco de dados .MDF não pode ser facilmente convertido em um formato que pode ser usado nas versões atuais do SQL Server, portanto, é melhor usar o script para criar o banco de dados.  
  
4.  No **Server Explorer**, criar uma conexão com uma instância do SQL Server onde você deseja instalar o banco de dados.  Se você não tiver um SQL Server específico que você deseja usar, poderá usar o banco de dados instalado automaticamente com o Visual Studio.  Para fazer isso, especifique `(localdb) \v11.0` como o nome do servidor.  
  
     Para criar a conexão, siga estas etapas.  
  
    ###### Para criar uma conexão com uma instância do SQL Server  
  
    1.  No **Gerenciador de Servidores**, abra o menu de atalho para o nó **Conexões de Dados** e escolha **Adicionar Conexão**.  
  
         A caixa de diálogo **Adicionar Conexão** será exibida.  
  
    2.  Insira o nome do SQL Server onde você deseja criar o banco de dados Northwind ou Pubs ou digite \(localdb\)\\v11.0.  
  
    3.  Em **Selecione ou digite um nome de banco de dados**, escolha qualquer banco de dados na lista, por exemplo, tempdb.  
  
    4.  Selecione o botão **Testar conexão** para verificar se tudo está funcionando e, em seguida, pressione o botão **OK**.  
  
         Um novo nó de conexão aparecerá no **Gerenciador de Servidores**.  
  
5.  No menu de atalho para o nó de conexão para o servidor, escolha o botão **Nova consulta**.  
  
     Uma janela do editor é aberta e mostra um arquivo de script .sql vazio.  
  
6.  Cole o conteúdo de instnwnd.sql ou instpubs.sql na janela do editor.  
  
7.  Escolha o botão executar consulta \(o ícone do triângulo verde aberto na parte superior direita da janela da consulta\).  
  
     Se a consulta for bem\-sucedida, a mensagem **Comandos concluídos com êxito** é exibida.  Isso significa que o banco de dados Northwind ou pubs foi criado.  
  
     Ainda será necessário adicionar uma conexão com o banco de dados de exemplo.  No **Gerenciador de Servidores**, abra o menu de atalho para o nó **Conexões de Dados** e escolha **Adicionar Conexão**.  
  
8.  Escolha o mesmo servidor de banco de dados que você escolheu antes, mas desta vez, em Selecione ou digite um nome de banco de dados, escolha o banco de dados Northwind ou pubs e escolha o botão **OK**.  
  
     Um novo nó aparece em Conexões de dados para o banco de dados de exemplo.  
  
9. Feche a janela do editor e confirme que você não deseja salvar o arquivo de consulta.  Não é necessário salvar o script de criação de banco de dados depois de criar o banco de dados.  
  
#### Para instalar os bancos de dados de exemplo AdventureWorks  
  
-   Baixe os bancos de dados de exemplo do AdventureWorks no [site da web do CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  
  
#### Para instalar o banco de dados de exemplo Northwind do Microsoft Access  
  
1.  No Microsoft Access 2010 ou posterior, pesquisar modelos do Northwind online e escolha **Banco de dados de amostra do Desktop Northwind 2007**.  
  
2.  No Microsoft Access, salve o arquivo de banco de dados como Northwind.accdb.  
  
 A nova extensão para bancos de dados do Access .accdb.  Consulte [programação de dados com o Microsoft Access 2010](http://msdn.microsoft.com/library/office/ff965871.aspx).  Para se conectar ao banco de dados Northwind usando o Access, consulte [Como se conectar ao banco de dados Northwind](../data-tools/how-to-connect-to-the-northwind-database.md).  
  
## Segurança do .NET Framework  
 Os bancos de dados de amostra são apenas para ilustrar e não necessariamente demonstram as práticas recomendadas de segurança.  
  
## Consulte também  
 [Como determinar a versão e edição do SQL Server e seus componentes](http://support.microsoft.com/kb/321185)   
 [Criar um banco de dados SQL usando um designer](../data-tools/create-a-sql-database-by-using-a-designer.md)   
 [Como se conectar ao banco de dados Northwind](../data-tools/how-to-connect-to-the-northwind-database.md)