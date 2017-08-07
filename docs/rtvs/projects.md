---
title: Projetos nas Ferramentas do R para Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 6/29/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 732b73cf-2014-4f98-838e-4141ef9dedac
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: 00ccd6319f13fc6be32ca7bde4e2c5f76a5cbc49
ms.contentlocale: pt-br
ms.lasthandoff: 07/12/2017

---

# <a name="creating-r-projects-in-visual-studio"></a>Criando projeto R no Visual Studio

Um projeto do R (um arquivo `.rxproj`) identifica todos os arquivos de origem e de conteúdo associados ao projeto. Ele também contém informações de build de cada arquivo, mantém as informações para integração com sistemas de controle do código-fonte e ajuda a organizar o aplicativo em componentes lógicos. As informações relacionadas ao espaço de trabalho, como a lista de pacotes instalados, no entanto, são mantidas separadamente no próprio espaço de trabalho.

Os projetos são sempre gerenciados em uma *solução* do Visual Studio, que pode conter vários projetos que podem fazer referências entre si. Consulte [Usar vários tipos de projeto no Visual Studio](#use-multiple-project-types-in-visual-studio).

## <a name="creating-a-new-r-project"></a>Criando um novo projeto R

1. Inicie o Visual Studio.
1. Escolha **Arquivo > Novo > Projeto...** (Ctrl + Shift + N)
1. Selecione "Projeto R" em **Modelos > R**, dê ao projeto um nome e um local e selecione **OK**:

    ![Caixa de diálogo Novo Projeto para R no Visual Studio (RTVS no VS2017)](media/getting-started-01-new-project.png)

Esse comando cria um projeto com um arquivo `script.R` vazio aberto no editor. Observe também no **Gerenciador de Soluções** que há outros dois arquivos no projeto:

![Conteúdo de um projeto R criado usando um modelo](media/projects-template-results.png)

O `.Rhistory` registra todos os comandos que você insere na janela [R Interativo](interactive-repl.md). Você pode abrir uma janela de histórico dedicada com o comando **Ferramentas do R > Janelas > Histórico**. Essa janela tem um botão de barra de ferramentas e itens do menu de contexto para limpar o conteúdo do histórico.

O arquivo `rproject.rproj` mantém determinadas configurações do projeto específicas do R que não são gerenciadas pelo Visual Studio de nenhum outro modo:

| Propriedade | Padrão | Descrição |
| --- | --- | --- |
| Versão | 1.0 | A versão das Ferramentas do R para Visual Studio usadas para criar o projeto. |
| RestoreWorkspace | Padrão | Carregar automaticamente as variáveis do Espaço de trabalho anteriores do arquivo `.RData` no diretório do projeto. |
| SaveWorkspace | Padrão | Salvar as variáveis de espaço de trabalho atual no arquivo `.RData` no diretório do projeto ao fechar um projeto. |
| AlwaysSaveHistory | Padrão | Salvar o histórico da janela interativa atual no arquivo `.RHistory` no diretório do projeto ao fechar um projeto. |
| EnableCodeIndexing | Sim | Determina se deseja executar uma tarefa de indexação em segundo plano para acelerar as pesquisas de código. |
| UseSpacesForTab | Sim | Determina se deseja inserir espaços (Sim) ou um caractere de tabulação (Não) quando a tecla Tab é pressionada no editor. |
| NumSpacesForTab | 2 | O número de espaços a serem inseridos se UseSpacesForTab for Sim. |
| Codificando | UTF-8 | A codificação padrão para arquivos `.R`. |
| RnwWeave | Sweave | Pacote a ser usado ao introduzir um arquivo Rnw. |
| LaTeX | pdfLaTeX | Biblioteca a ser usada ao converter RMarkdwon em PDF. |

### <a name="converting-a-folder-of-files-to-an-r-project"></a>Converter uma pasta de arquivos em um projeto R

Se você tiver uma pasta existente de arquivos `.R` que deseje gerenciar em um projeto, siga as etapas a seguir:

1. Crie um novo projeto no Visual Studio como na seção anterior.
1. Copie os arquivos para a pasta do projeto.
1. No Gerenciador de Soluções do Visual Studio, clique com botão direito do mouse no projeto, selecione **Adicionar > Item Existente** e navegue até os arquivos que deseja adicionar. Esses arquivos aparecem na árvore do projeto depois de selecionar **OK**.
1. Para organizar o código em subpastas, clique com botão direito do mouse no projeto, selecione **Adicionar > Nova Pasta** primeiro, copie os arquivos para essa pasta e adicione todos os itens existentes na etapa 3.

## <a name="project-properties"></a>Propriedades de projeto

Para abrir as páginas de propriedades do projeto, clique com botão direito do mouse no projeto no **Gerenciador de Soluções** e selecione **Propriedades** ou selecione o item de menu **Projeto > Propriedades do (nome do projeto)...*. A janela aberta exibe propriedades do projeto:

| Tabulação | Propriedade | Descrição |
| --- | --- | --- |
| Executar | Arquivo de inicialização | O nome do arquivo que é executado com o comando **Arquivo de inicialização de origem**, F5, **Depurar > Iniciar depuração** ou **Depurar > Iniciar sem depuração**. Clicar com o botão direito do mouse no arquivo no projeto e selecionar **Definir como script de inicialização do R** também o define como o arquivo de inicialização. |
| | Redefinir R Interativo em execução | Limpa todas as variáveis de espaço de trabalho da janela interativa ao executar o projeto. Isso garante que não haja nenhum conteúdo no espaço de trabalho que restou das execuções anteriores. |
| | Caminho do projeto remoto | Caminho para um espaço de trabalho remoto. |
| | Transferir arquivos em execução | Indica se os arquivos do projeto, sujeitos ao filtro em **Arquivos para transferir**, devem ser copiados para um espaço de trabalho remoto com cada execução. |
| | Arquivos para transferir | Nomes de arquivo e curingas que indicam os arquivos específicos para copiar em um espaço de trabalho remoto se **Transferir arquivos em execução** estiver selecionado. |
| Configurações | (Arquivo Settings.R) | As configurações do projeto R vêm dos arquivos `Settings.R` ou `*.Settings.R` que estão localizados dentro do projeto. Se não houver nenhum arquivo de configurações, você poderá adicionar variáveis, salvar a página e um arquivo padrão `Settings.R` será criado para você. Você também pode adicionar o arquivo de configurações ao projeto por meio do comando de menu **Arquivo > Adicionar Novo Item...* . <br/> As configurações são armazenadas como código R e o arquivo pode ser obtido antes da execução de outros módulos, portanto, pré-populando o ambiente com configurações predefinidas. |

## <a name="r-specific-project-commands"></a>Comandos de projeto específico do R

Os projetos do Visual Studio dão suporte a vários comandos gerais por meio do menu acionado por clique com o botão direito do mouse e o menu **Projeto**. Para obter detalhes sobre esses recursos gerais, consulte [Soluções e projetos no Visual Studio](../ide/solutions-and-projects-in-visual-studio.md). Tenha em mente, no entanto, que 

As RTVS (Ferramentas do R para Visual Studio) adicionam vários comandos próprios ao menu acionado por clique com o botão direito do mouse para projetos R e também arquivos e pastas dentro do projeto.

| Comando | Descrição |
| --- | --- |
| Definir diretório de trabalho aqui | Define o diretório de trabalho da janela do R Interativo para a pasta do projeto, que também pode ser usado em qualquer subpasta dentro de um projeto. |
| Abrir pasta que contém | Abre o Windows Explorer no local do arquivo selecionado. | 
| Adicionar script R | Cria e abre um novo arquivo `.R` com um nome padrão. Você também pode usar o comando **Adicionar > Novo Item...** para criar arquivos `.R`, além de vários outros tipos de arquivo. Consulte [Modelos de item específicos do R](#r-specific-item-templates). |
| Adicionar R Markdown | Cria e abre um novo documento `.rmd` com um nome padrão. Você também pode usar o comando **Adicionar > Novo Item...** para criar arquivos `.rmd`, além de vários outros tipos de arquivo. Consulte [Modelos de item específicos do R](#r-specific-item-templates).  | 
| Publicar procedimentos armazenados | Inicia um processo para publicar todos os procedimentos armazenados contidos em scripts R. Consulte [Trabalhando com procedimentos armazenados do SQL Server](sql-server.md#working-with-sql-server-stored-procedures). | 

## <a name="r-specific-item-templates"></a>Modelos de item específicos do R

As RTVS incluem vários modelos para tipos de arquivo específicos. Você pode acessar os modelos clicando com o botão direito do mouse em um projeto R e selecionando **Adicionar > Novo Item...**, selecionando **Projeto > Adicionar Novo Item...** ou usando **Arquivo > Novo > Arquivo...** e selecionando a guia **R**. A melhor maneira de explorar um modelo é criar um novo projeto e inserir arquivos de cada tipo.

> [!Note]
> Os comandos **Adicionar > Novo Item...** também exibem tipos de arquivos gerais que não estão listados na tabela, com **Arquivo > Novo > Arquivo...** esses tipos estão contidos na guia **Geral**.

| Tipo de arquivo | Descrição |
| --- | --- |
| Script R | Um arquivo de texto que contém os mesmos comandos que podem ser inseridos na linha de comando R. |
| R Markdown | Um arquivo contendo um documento [R Markdown](rmarkdown.md). |
| Configurações do R | Um arquivo que contém as configurações do aplicativo R. | 
| Documentação do R | Um arquivo de documentação do R genérico que contém apenas os campos nome, alias e título. |
| Documentação do R (função) | Um arquivo de documentação do R que contém vários campos com comentários para descrever uma função. |
| Documentação do R (conjunto de dados) | Um arquivo de documentação do R que contém vários campos com comentários para descrever um conjunto de dados. |
| Consulta SQL | E um arquivo `.sql` vazio. Consulte [Integração do SQL Server](sql-server.md). |
| Procedimento armazenado com R | Um arquivo R com uma consulta SQL filho e um arquivo de modelo de procedimento armazenado filho. Consulte [Integração do SQL Server](sql-server.md). |


## <a name="use-multiple-project-types-in-visual-studio"></a>Usar vários tipos de projeto no Visual Studio

As soluções do Visual Studio fornecem um local conveniente para reunir e gerenciar projetos relacionados em um único lugar lógico. As soluções ajudam você a manter seu código organizado e facilita a colaboração entre equipes.

No exemplo abaixo, a solução contém um projeto R com um modelo criado usando R e Azure Machine Learning, um projeto Python/scikit-learn, um projeto C++ que contém módulos para trabalho com uso intensivo de computação, um projeto SQL para gerenciamento de dados e um projeto Python/Bottle para o site da web que publica o resultado:

![Gerenciador de Soluções do Visual Studio mostrando vários projetos relacionados em uma solução](media/projects-polyglot.png)

O projeto realçado em negrito é o projeto de "inicialização" da solução. Para alterá-lo, clique com o botão direito do mouse em um projeto diferente e selecione **Definir como projeto de inicialização**.

> [!Note]
> No momento, não há nenhum R explícito para integração com a linguagem C#/C++ em vigor (como há para Python, consulte [Criando uma extensão do C++ para o Python](../python/cpp-and-python.md)).  No entanto, há bibliotecas disponíveis que fornecem o pontes de C# e C++ para R.

Para obter mais informações sobre como gerenciar projetos e soluções em geral, consulte [Soluções e projetos no Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).

