---
title: "Atualizar os arquivos. mdf | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "LocalDB do SQL Server"
  - "LocalDB"
  - "SQLEXPRESS"
  - "atualizando o SQLExpress para SQLExpress"
  - "atualizando para LocalDB"
ms.assetid: 14ca6f76-f80e-4926-8020-3fee2d802b75
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Atualizar os arquivos. mdf
Este tópico descreve as opções para atualizar o arquivo de banco de dados \(. mdf\) depois de instalar uma versão mais recente do Visual Studio. Ele inclui instruções para as seguintes tarefas:  
  
-   Atualizar um arquivo de banco de dados para usar uma versão mais recente do SQL Server Express LocalDB  
  
-   Atualizar um arquivo de banco de dados para usar uma versão mais recente do SQL Server Express  
  
-   Trabalhar com um arquivo de banco de dados no Visual Studio, mas manter a compatibilidade com uma versão anterior do SQL Server Express ou LocalDB  
  
-   Verifique o SQL Server Express o mecanismo de banco de dados padrão  
  
 Você pode usar o Visual Studio para abrir um projeto que contém um arquivo de banco de dados \(. mdf\) que foi criado usando uma versão anterior do SQL Server Express ou LocalDB. No entanto, para continuar a desenvolver o projeto no Visual Studio, você deve ter a versão do SQL Server Express ou LocalDB instalada no mesmo computador que o Visual Studio, ou você deve atualizar o arquivo de banco de dados. Se você atualizar o arquivo de banco de dados, você não poderá acessá\-lo usando versões anteriores do SQL Server Express ou LocalDB.  
  
 Você também precisará atualizar um arquivo de banco de dados que foi criado por meio de uma versão anterior do SQL Server Express ou LocalDB se a versão do arquivo não é compatível com a instância do SQL Server Express ou LocalDB está instalado. Para resolver o problema, Visual Studio solicitará que você atualize o arquivo.  
  
> [!IMPORTANT]
>  É recomendável que você faça backup do arquivo de banco de dados antes de atualizá\-lo.  
  
> [!WARNING]
>  Se você atualizar um arquivo. mdf criado no LocalDB 2014 \(V12\) 32 bits para o LocalDB 2016 \(V13\), você não poderá abri\-lo novamente na versão de 32 bits do LocalDB.  Na atualização 2, LocalDB V13 é apenas de 64 bits.  
  
 Antes de atualizar um banco de dados, considere os seguintes critérios:  
  
-   Não atualize para trabalhar em seu projeto em uma versão mais antiga e uma versão mais recente do Visual Studio.  
  
-   Não atualize se seu aplicativo será usado em ambientes que usam o SQL Server Express em vez de LocalDB.  
  
-   Não atualize se seu aplicativo usa conexões remotas, como LocalDB não aceitá\-los.  
  
-   Não atualize se seu aplicativo se basear no Internet Information Services \(IIS\).  
  
-   Considere a atualização se você deseja testar os aplicativos de banco de dados em um ambiente de área restrita, mas não deseja administrar um banco de dados.  
  
### Para atualizar um arquivo de banco de dados  
  
1.  Em **Server Explorer**, selecione o **conectar\-se ao banco de dados** botão.  
  
2.  No **Add Connection** caixa de diálogo, especifique as seguintes informações:  
  
    -   **Fonte de dados**: `Microsoft SQL Server (SqlClient)`  
  
    -   **Nome do servidor**:  
  
        -   Para usar a versão padrão: `(localdb)\MSSQLLocalDB`.  Isso especificará ProjectV12 ou ProjectV13, dependendo de qual versão do Visual Studio está instalado e quando a primeira instância de LocalDB foi criada. O **MSSQLLocalDB** nó **SQL Server Object Explorer** mostra qual versão apontando para.  
  
        -   Para usar uma versão específica: `(localdb)\ProjectsV12` ou `(localdb)\ProjectsV13`, onde V12 é LocalDB 2014, e V13 é 2016 LocalDB.  
  
    -   **Anexar um arquivo de banco de dados**: O caminho físico do arquivo. mdf primário.  
  
    -   **Nome lógico**: O nome que você deseja usar com o arquivo.  
  
3.  Selecione o **OK** botão.  
  
4.  Quando solicitado, selecione o **Sim** botão para atualizar o arquivo.  
  
 O banco de dados é atualizado, é anexado ao mecanismo de banco de dados LocalDB e não é mais compatível com a versão mais antiga do LocalDB.  
  
 Você também pode modificar uma conexão do SQL Server Express para usar o LocalDB abrindo o menu de atalho para a conexão e, em seguida, selecionando **Modificar conexão**. No **Modificar conexão** caixa de diálogo, altere o nome do servidor para `(LocalDB)\MSSQLLocalDB`. No **Propriedades avançadas** caixa de diálogo caixa, certifique\-se de que **instância de usuário** é definido como **False**.  
  
### Para atualizar para uma versão mais recente do SQL Server Express  
  
1.  No menu de atalho para a conexão com o banco de dados, selecione **Modificar conexão**.  
  
2.  No **Modificar conexão** caixa de diálogo, selecione o **Avançado** botão.  
  
3.  No **Propriedades avançadas** caixa de diálogo, selecione o **OK** botão sem alterar o nome do servidor.  
  
 O arquivo de banco de dados é atualizado para corresponder à versão atual do SQL Server Express.  
  
### Para trabalhar com o banco de dados no Visual Studio, mas manter a compatibilidade com o SQL Server Express  
  
-   No Visual Studio, abra o projeto sem atualizá\-lo.  
  
    -   Para executar o projeto, selecione a tecla F5.  
  
    -   Para editar o banco de dados, abra o arquivo. mdf no **Solution Explorer**, e expanda o nó no **Server Explorer** para trabalhar com seu banco de dados.  
  
### Para tornar o SQL Server Express o mecanismo de banco de dados padrão  
  
1.  Na barra de menus, selecione **ferramentas** \> **opções**.  
  
2.  No **opções** caixa de diálogo caixa, expanda o **Data Tools** opções e selecione o **conexões de dados** nó.  
  
3.  No **nome da instância do SQL Server** texto, especifique o nome da instância do SQL Server Express ou LocalDB que você deseja usar. Se a instância não é nomeada, especifique `.\SQLEXPRESS or (localdb)\MSSQLLocalDB`.  
  
4.  Selecione o **OK** botão.  
  
 SQL Server Express será o mecanismo de banco de dados padrão para seus aplicativos.  
  
## Consulte também  
 [Visão geral de dados local](../data-tools/local-data-overview.md)   
 [Instruções passo a passo: conectando a dados em um arquivo de banco de dados local \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Local%20Database%20File%20\(Windows%20Forms\).md)