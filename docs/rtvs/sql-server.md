---
title: "Integrando o SQL Server às Ferramentas do R para Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 919dfc34-234a-489e-91bf-74a4cefae26c
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 44ae1fd825997ff5eab1448ebd86f88a130172a1
ms.contentlocale: pt-br
ms.lasthandoff: 05/12/2017

---


# <a name="working-with-sql-server-and-r"></a>Trabalhando com o SQL Server e R

As RTVS (Ferramentas do R para Visual Studio) usufruem do excelente suporte do Visual Studio para o SQL Server facilitando o trabalho com bancos de dados SQL para os cientistas de dados, ou seja, criar e executar consultas SQL e trabalhar com procedimentos armazenados.

> [!Note]
> Para trabalhar com SQL e R juntos, você deve ter o SQL Server Data Tools instalado:
> - Visual Studio de 2017: execute o instalador do Visual Studio e selecione a carga de trabalho Armazenamento e processamento de dados, que inclui o SQL Server Data Tools.
> - Visual Studio 2015: siga as instruções em [Baixar o SQL Server Data Tools](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt).

O vídeo a seguir (3m 03s) fornece uma visão geral do SQL Server e do R:

<iframe width="560" height="315" src="https://www.youtube.com/embed/n4AYr0QIwdQ" frameborder="0" allowfullscreen></iframe>

## <a name="creating-and-running-sql-queries"></a>Criando e executando consultas SQL

As RTVS dão suporte para adição de consultas SQL em projetos R, permitindo que você desenvolva consultas SQL iterativamente em um contexto separado até obter os resultados que está procurando.

Para adicionar um arquivo de consulta SQL, clique com botão direito do mouse no projeto no Gerenciador de Soluções, selecione **Adicionar > Novo Item...** e selecione o tipo de arquivo de **Consulta SQL**:

![Adicionar item de consulta SQL a um projeto](~/docs/rtvs/media/sql-add-item.png)

Isso abre o arquivo no editor Transact-SQL do Visual Studio, que fornece o IntelliSense completo para SQL e a capacidade de executar consultas. Para que esses recursos funcionem, no entanto, você precisa se conectar a um banco de dados usando o botão Conectar na barra de ferramentas do editor ou simplesmente tentando executar uma consulta (Ctrl + Shift + E, que também funciona em uma seleção). As duas formas abrem a caixa de diálogo de conexão:

![Caixa de diálogo de conexão SQL](~/docs/rtvs/media/sql-connection-dialog.png)

Quando uma conexão é estabelecida, você pode executar consultas e ver os resultados:

![Resultados da consulta da janela SQL](~/docs/rtvs/media/sql-query-results.png)

O editor Transact-SQL dá suporte a uma variedade de outros recursos, como exibir o plano de execução da consulta, um depurador de consulta e a vários outros recursos. Para obter detalhes, consulte [Usar o Editor Transact-SQL para editar e executar scripts](https://msdn.microsoft.com/library/hh272706.aspx).

## <a name="working-with-sql-server-stored-procedures"></a>Trabalhando com procedimentos armazenados do SQL Server

Os [SQL Server R Services](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services) (Serviços do R para SQL Server) (SQL Server 2016 e posterior) permitem inserir e executar código R de um procedimento armazenado do T-SQL. Isso significa que é possível executar código R em um computador SQL Server, operar em dados retornados de uma consulta SQL e gerar um conjunto de resultados SQL que pode ser processado por SQL adicional ou retornado ao cliente.

As RTVS simplificam o processo, que seria complicado e sujeito a erros, de combinar código SQL e R dentro de uma única instrução SQL, conforme descrito nas seções a seguir:

- [Adicionar uma conexão de banco de dados](#add-a-database-connection)
- [Escrever e testar um procedimento armazenado SQL](#write-and-test-a-sql-stored-procedure)
- [Publicar um procedimento armazenado SQL](#publish-a-sql-stored-procedure)

O vídeo a seguir (6m 09s) também fornece uma visão geral desses recursos:

<iframe width="560" height="315" src="https://www.youtube.com/embed/dFKIT2OitWQ" frameborder="0" allowfullscreen></iframe>

### <a name="add-a-database-connection"></a>Adicionar uma conexão de banco de dados

1. Selecione **Ferramentas do R > Dados > Adicionar Conexão de Banco de Dados** para abrir a caixa de diálogo **Propriedades de Conexão**, no qual você especifica o nome da fonte de dados (SQL Server, neste caso), o nome do servidor, o modo de autenticação e o nome do banco de dados. Você pode selecionar **Testar Conexão** para verificar sua entrada antes de fechar a caixa de diálogo.
 
    ![Caixa de diálogo Conexão SQL](~/docs/rtvs/media/sql-connection-string-dialog.png)

1. Depois de selecionar **OK** com uma conexão válida, o Visual Studio gera uma cadeia de conexão chamada `dbConnection` em um novo arquivo `settings.R`. As RTVS origina (executa) automaticamente esse arquivo, permitindo usar imediatamente a conexão dos scripts R:

![Arquivo SQL Settings.R](~/docs/rtvs/media/sql-settings-dot-r.png)

### <a name="write-and-test-a-sql-stored-procedure"></a>Escrever e testar um procedimento armazenado SQL

Para adicionar um novo procedimento armazenado SQL, clique com o botão direito do mouse em seu projeto, selecione **Adicionar > Novo Item...**, selecione **Procedimento Armazenado SQL com R** na lista de modelos, nomeie o arquivo (`StoredProcedure.R`, neste exemplo) e selecione **OK**.
 
As RTVS criam três arquivos para o procedimento armazenado, um arquivo `.R` para o código R, um arquivo `.Query.sql` para o código SQL e um arquivo `.Template.sql` que combina os dois arquivos. Os dois aparecem no Gerenciador de Soluções como filhos do arquivo `.R`:

![Exibição do Gerenciador de Soluções expandido com o procedimento armazenado SQL com R](~/docs/rtvs/media/sql-solution-explorer-expanded.png)

`StoredProcedure.R` (neste exemplo) é onde você escreverá seu código R. O conteúdo padrão é o seguinte:

```R
# @InputDataSet: input data frame, result of SQL query execution
# @OutputDataSet: data frame to pass back to SQL

# Test code
# library(RODBC)
# channel <- odbcDriverConnect(dbConnection)
# InputDataSet <- sqlQuery(channel, )
# odbcClose(channel)

OutputDataSet <- InputDataSet
```

Em poucas palavras, o código recebe um dataframe R chamado `InputDataSet` e retorna os resultados em `OutputDataSet`, com o código de modelo, simplesmente copiando a entrada para a saída.

> [!Note]
> Os nomes desses dataframes são controlados pelos parâmetros `@input_data_1_name` e `@output_data_1_name` na chamada para o procedimento armazenado do sistema `sp_execute_external_script`. Para obter mais detalhes sobre o design desta convenção de chamada e alguns exemplos de uso, [sp_execute_external_script (Transact-SQL)](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

O outro código gerado nos comentários é um script de teste pequeno que usa o [Pacote RODBC](https://cran.r-project.org/web/packages/RODBC/index.html) para transmitir uma instrução SQL ao SQL Server, executá-la e recuperar seu conjunto de resultados como um dataframe R. Você pode remover a marca de comentário desse código de teste para escrever seu código R interativamente em relação ao conjunto de resultados obtido do SQL Server.

`StoredProcedure.Query.sql` é onde você escreve e testa a consulta SQL que gera os dados para `InputDataSet`. Como esse é um arquivo `.sql`, você tem todos os recursos do editor Transact-SQL disponíveis para você.

Depois que estiver satisfeito com seu código SQL, você poderá integrá-lo facilmente ao código R em `StoredProcedure.R`, bastando arrastar o arquivo `.sql` para o editor aberto do arquivo `.R`. Na imagem abaixo, `StoredProcedure.Query.sql` foi arrastado para o ponto após a vírgula em `sqlQuery(channel, )`:

![Lendo o arquivo SQL na variável de cadeia de caracteres de R](~/docs/rtvs/media/sql-reference-sql-file-from-r.png)

Como você pode ver, essa etapa simples gera automaticamente o código R para abrir o arquivo `.sql`, ler seu conteúdo em uma cadeia de caracteres e passá-lo para o pacote RODBC para enviá-lo ao SQL Server.

Com isso funcionando, é possível escrever interativamente o código R que manipula o dataframe `InputDataSet`, conforme o desejado. Lembre-se de que basta selecionar o código R no editor e enviá-lo à [janela interativa](interactive-repl.md) pressionando Ctrl + Enter.

`StoredProcedure.Template.sql`, por fim, contém o modelo para gerar o procedimento armazenado SQL:

```sql
CREATE PROCEDURE [StoredProcedure]
AS
BEGIN
EXEC sp_execute_external_script @language = N'R'
    , @script = N'_RCODE_'
    , @input_data_1 = N'_INPUT_QUERY_'
--- Edit this line to handle the output data frame.
    WITH RESULT SETS (([MYNEWCOLUMN] NVARCHAR(max)));
END;
```

- O espaço reservado `_RCODE_` é substituído pelo conteúdo do `StoredProcedure.R`.
- O espaço reservado `_INPUT_QUERY_` é substituído pelo conteúdo do `StoredProcedure.Query.sql`.
- Você precisa descrever o esquema do conjunto de resultados retornado pelo procedimento armazenado, editando a cláusula `WITH RESULT SETS`. Identifique especificamente as colunas do dataframe `OutputDataSet` que deseja retornar ao chamador do procedimento armazenado. 

Por exemplo, na seguinte consulta:

```sql
SELECT TOP 100 medallion, hack_license FROM nyctaxi_sample
```

Você usaria a cláusula `WITH RESULT SETS` a seguir para especificar os tipos de dados dos valores retornados:

```sql
WITH RESULT SETS ((medallion NVARCHAR(max), hack_license NVARCHAR(max)));
```

### <a name="publish-a-sql-stored-procedure"></a>Publicar um procedimento armazenado SQL

1. Selecione o comando de menu **Ferramentas do R > Dados > Publicar com Opções...**.
1. Na caixa de diálogo que aparece, altere **Publicar em:** para **Banco de dados**, especifique o destino, selecione **Publicar** e as RTVS criarão e publicarão o procedimento armazenado:

    ![Caixa de diálogo Publicar procedimento armazenado](~/docs/rtvs/media/sql-publish-with-options.png)

1. Para publicar todos os procedimentos armazenados em um projeto, você também pode usar o comando **Ferramentas do R > Dados > Publicar Procedimentos Armazenados**, que também estão disponíveis ao clicar com o botão direito do mouse no projeto no Gerenciador de Soluções.

> [!Tip]
> Se o Pesquisador de Objetos do SQL Server estiver aberto no Visual Studio, você também verá o procedimento armazenado publicado na pasta **Modo Programático > Procedimentos Armazenados** do banco de dados. Você também pode executar isso no Pesquisador de Objetos clicando com o botão direito do mouse e selecionando **Executar Procedimento** ou chamando interativamente de uma janela de consulta `.sql`.

