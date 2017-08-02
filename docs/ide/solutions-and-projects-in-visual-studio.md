---
title: "Soluções e projetos no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 06/12/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.savedeferredsaveprojectonclose
- vs.untrustedtemplateopeningdocuments
- Project Properties.FullPath
- vs.addnewsolutionitem
- vs.environment.projects
- vs.openproject
- vs.getopenfilename
- vs.addnewitem
- vs.encoding
- vs.addexistingitem
- Project Properties.URL
- VS.SolutionExplorer
- Project Properties.FileName
- SolutionProperties.Name
- VS.SaveChangesDlg
- vs.newproject
- VS.SolutionExplorer.Selection
- SolutionProperties.Path
- vs.getdirectoryname
- vs.addexistingsolutionitem
- SolutionProperties.Description
- vs.environment.solutions
- vs.saveordiscarddeferredsaveproject
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- vs.solutionpropertypages
- vs.solutionpropertypages.startupproject
- vs.solutionpropertypages.configurationsettings
- solution items, folder in Solution Explorer
- solution items, shared
- solutions [Visual Studio]
- project items [Visual Studio], about project items
- workspaces
- solutions [Visual Studio], designing
- projects [Visual Studio]
- solutions [Visual Studio], projects and
- vs.solutionpropertypages.projectdependencies
- applications [Visual Studio]
- projects [Visual Studio], setting up
- miscellaneous files
ms.assetid: aeaf56cb-c2dd-47f6-b012-23b84b7a7254
caps.latest.revision: 35
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 8ce85525f6af336682f6f8547c2f6c13dde73c8c
ms.openlocfilehash: 28dfbb85790cfda2c3d840ce2d57468b5421bee0
ms.contentlocale: pt-br
ms.lasthandoff: 06/23/2017

---
# <a name="solutions-and-projects-in-visual-studio"></a>Soluções e projetos no Visual Studio
Quando você cria um app, aplicativo, site da Web, aplicativo Web, script, plug-in, etc no Visual Studio, você começa com um *projeto*. Em um sentido lógico, um projeto contém de todos os arquivos de código-fonte, ícones, imagens, arquivos de dados e qualquer outra coisa que será compilada em um programa executável ou site, ou o que mais for necessário para executar a compilação.  Um projeto também contém todas as configurações de compilador e outros arquivos de configuração que podem ser necessários para diversos serviços ou componentes com os quais seu programa se comunicará.

> [!NOTE]
>  Você não será obrigado a usar soluções ou projetos se não desejar. Você pode simplesmente abrir os arquivos no Visual Studio e começar a editar seu código. Consulte [Abrir qualquer pasta com o Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2016/04/12/open-any-folder-with-visual-studio-15-preview/) para obter mais informações.


 Em um sentido literal, um projeto é um arquivo XML (*. vbproj, \*.csproj, \*.vcxproj) que define uma hierarquia de pasta virtual junto com os caminhos para todos os itens que ela "contém" e todas as configurações de build. No Visual Studio, o arquivo de projeto é usado pelo Gerenciador de Soluções para exibir as configurações e o conteúdo do projeto. Quando você compila seu projeto, o mecanismo do MSBuild consome o arquivo de projeto para criar o executável. Você também pode personalizar projetos para produzir outros tipos de saída.  

 Um projeto está contido, em um sentido lógico e no sistema de arquivos, em uma *solução*; esta pode conter um ou mais projetos, juntamente com informações de build, configurações de janela do Visual Studio e arquivos diversos que não estão associados a nenhum projeto. Em um sentido literal, a solução é um arquivo de texto com seu próprio formato exclusivo; ele geralmente não se destina a ser editado manualmente.  

 Uma solução tem um arquivo *.suo* associado que armazena as configurações, preferências e informações de configuração de cada usuário que trabalhou no projeto.  

 O diagrama a seguir mostra a relação entre projetos e soluções e os itens que eles contêm logicamente.  

 ![Projetos e solução do Visual Studio](~/ide/media/vside-project-diagram.png)  

 Também é possível criar modelos de item e de projeto personalizados. Para obter mais informações, consulte [Criando modelos de item e de projeto](../ide/creating-project-and-item-templates.md).  

## <a name="creating-new-projects"></a>Criando novos projetos  
 A maneira mais fácil de criar um novo projeto é começar com um modelo de projeto predefinido, que consiste em um conjunto básico de arquivos de código, arquivos de configuração, configurações e ativos gerados previamente que permitem que você comece a criar um tipo específico de aplicativo ou site em uma linguagem de programação específica. Esses modelos são o que você vê na **caixa de diálogo Novo Projeto** quando você escolhe **Arquivo &#124; Novo &#124; Projeto** ou **Arquivo &#124; Novo &#124; Site** no menu principal e, em seguida, navega. Para obter mais informações, consulte [Criando soluções e projetos](../ide/creating-solutions-and-projects.md).  

## <a name="managing-projects-in-solution-explorer"></a>Gerenciamento de projetos no Gerenciador de Soluções  
 Depois de criar um novo projeto, você usa o **Gerenciador de Soluções** para exibir e gerenciar projetos e soluções e seus itens associados. A ilustração a seguir mostra o Gerenciador de Soluções com uma solução em C# que contém dois projetos.  

 ![Gerenciador de Soluções](../ide/media/vs2015_solution_explorer.png "vs2015_solution_explorer")  

## <a name="in-this-section"></a>Nesta seção  

-   [Criando soluções e projetos](../ide/creating-solutions-and-projects.md)  

-   [Adicionando e removendo itens de projeto](../ide/adding-and-removing-project-items.md)  

-   [Gerenciando propriedades de solução e de projeto](../ide/managing-project-and-solution-properties.md)  

-   [Gerenciando referências em um projeto](../ide/managing-references-in-a-project.md)  

-   [Propriedades do aplicativo](../ide/application-properties.md)  

-   [Gerenciando Assinatura de Assembly e Manifesto](../ide/managing-assembly-and-manifest-signing.md)  

-   [Como especificar um ícone do aplicativo (Visual Basic, C#)](../ide/how-to-specify-an-application-icon-visual-basic-csharp.md)  

-   [Direcionamento de uma versão específica do .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)  

-   [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)  

## <a name="see-also"></a>Consulte também  
 [Visual Studio IDE](../ide/visual-studio-ide.md)

