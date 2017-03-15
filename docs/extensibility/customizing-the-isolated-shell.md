---
title: Personalizando o Shell isolado | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f36bfb81f311db0f49d399f86007f10d618b7ba3
ms.lasthandoff: 02/22/2017

---
# <a name="customizing-the-isolated-shell"></a>Personalizando o Shell isolado
Você pode personalizar seu aplicativo de shell do Visual Studio isolada alterando diferentes aspectos da interface de usuário do Visual Studio e restringindo os comandos e recursos incluídos no seu aplicativo especializado.  
  
## <a name="using-the-applicationpkgdef-file"></a>Usando o arquivo Application.pkgdef  
 A solução de modelo do shell isolado inclui um *SolutionName*. Arquivo de Application.pkgdef que permite que você modifique os seguintes recursos:  
  
##### <a name="the-application-title"></a>O título do aplicativo  
 Você pode personalizar o título do aplicativo, que é o nome que é exibido na barra de título do aplicativo, alterando o valor da linha "AppName" o *SolutionName*. Arquivo Application.pkgdef. Para obter mais detalhes, consulte [passo a passo: Criando um aplicativo de Shell isolado básico](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
 Se você não quiser que o título do aplicativo para exibir o projeto que está atualmente carregado, altere o valor da linha "ShowHierarchyRootInTitle" o *SolutionName*. Arquivo de Application.pkgdef de DWORD:&00000;001 para DWORD:&00000;000.  
  
##### <a name="the-application-icon"></a>O ícone do aplicativo  
 Você pode personalizar o ícone do aplicativo, que é o ícone que é exibido pelo nome do aplicativo na barra de título do aplicativo. Copie um ícone diferente para o diretório de ícone. Em **Solution Explorer**, adicione o ícone para a pasta de arquivos de recurso. Em seguida, abra o arquivo VSShellStub.rc e substitua o valor de IDI_STUBPROGRAM com o nome do novo ícone. Para obter mais detalhes, consulte [passo a passo: Criando um aplicativo de Shell isolado básico](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-command-line-logo"></a>O logotipo de linha de comando  
 Você pode personalizar o logotipo de linha de comando, que é o texto que aparece quando o aplicativo é iniciado na linha de comando, alterando o valor da linha "CommandLineLogo" o *SolutionName*. Arquivo Application.pkgdef. Para obter mais detalhes, consulte [passo a passo: Criando um aplicativo básico de Shell isolado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>O nome da subpasta de arquivos do usuário  
 Você pode alterar o nome da pasta do seu aplicativo mantém arquivos de usuário alterando o valor da linha "UserFilesSubFolderName" *SolutionName*. Arquivo Application.pkgdef.  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>O título do nó de árvore solution na caixa de diálogo Novo projeto  
 Você pode personalizar o título do nó de solução na caixa de diálogo Novo projeto, alterando o valor da linha "NewProjDlgSlnTreeNodeTitle" o *SolutionName*. Arquivo Application.pkgdef.  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>O cabeçalho de modelos instalados na caixa de diálogo Novo projeto  
 Você pode alterar o cabeçalho de modelos instalados na caixa de diálogo Novo projeto, alterando o valor da linha "NewProjDlgInstalledTemplatesHdr" o *SolutionName*. Arquivo Application.pkgdef.  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>Se deseja ou não ocultar arquivos diversos por padrão  
 Você pode especificar se deseja ou não ocultar arquivos diversos por padrão, alterando o valor da linha "HideMiscellaneousFilesByDefault" o *SolutionName*. Arquivo Application.pkgdef. Para ocultar arquivos diversos, defina o valor `dword:00000001`e para mostrar os arquivos, defina o valor `dword:00000000`.  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>Se deseja ou não desabilitar a janela de saída  
 Você pode especificar se deseja ou não desabilitar a janela de saída no seu aplicativo, alterando o valor da linha "DisableOutputWindow" o *SolutionName*. Arquivo Application.pkgdef. Para desativar a janela de saída, defina o valor `dword:00000001`e para mostrar a janela de saída, defina o valor `dword:00000000`.  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>Se deseja ou não permitir que os arquivos ignorados na janela principal do  
 Você pode especificar se deseja ou não permitir que arquivos ignorados na janela principal em seu aplicativo alterando o valor da linha "AllowsDroppedFilesOnMainWindow" o *SolutionName*. Arquivo Application.pkgdef. Para permitir que os arquivos ignorados, defina o valor `dword:00000001`e para impedir que os arquivos ignorados, defina o valor `dword:00000000`.  
  
##### <a name="the-default-search-page"></a>A página de pesquisa padrão  
 Você pode personalizar a página do navegador da web, que é exibido quando a janela do navegador é aberta, alterando o valor da linha "DefaultSearchPage" na página de *SolutionName*. Arquivo Application.pkgdef.  
  
##### <a name="the-default-home-page"></a>A home page padrão  
 Você pode personalizar a home page, alterando o valor da linha "DefaultHomePage" o *SolutionName*. Arquivo Application.pkgdef. Para obter mais detalhes, consulte [passo a passo: Criando um aplicativo básico de Shell isolado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>Se deseja ou não ocultar o conceito da solução  
 Você pode especificar se deseja ou não ocultar a solução em seu aplicativo, alterando o valor da linha "HideSolutionConcept" o *SolutionName*. Arquivo Application.pkgdef. Para ocultar a solução, defina o valor `dword:00000001`e para mostrar a solução, defina o valor `dword:00000000`.  
  
##### <a name="the-default-debug-engine"></a>O mecanismo de depuração padrão  
 Você pode alterar o mecanismo de depurar seu aplicativo usa, alterando o valor da linha "DefaultDebugEngine" o *SolutionName*. Arquivo Application.pkgdef o GUID de seu mecanismo de depuração.  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>A extensão de arquivo do arquivo de opções de usuário  
 Você pode alterar o nome da pasta do seu aplicativo mantém arquivos de usuário alterando o valor da linha "UserOptsFileExt" *SolutionName*. Arquivo Application.pkgdef.  
  
##### <a name="the-solution-file-extension"></a>A extensão de arquivo da solução  
 Você pode alterar a extensão usada para os arquivos de solução, alterando o valor da linha "SolutionFileExt" o *SolutionName*. Arquivo Application.pkgdef.  
  
##### <a name="the-default-user-files-folder-root"></a>A pasta raiz de arquivos de usuário padrão  
 Você pode alterar o nome da pasta raiz dos arquivos de usuário para seu aplicativo, alterando o valor da linha "UserFilesSubFolderName" o *SolutionName*. Arquivo Application.pkgdef.  
  
##### <a name="the-solution-file-creator-identifier"></a>O identificador de criador do arquivo de solução  
 Você pode alterar o identificador usado para os arquivos da solução, alterando o valor da linha "SolutionFileCreatorIdentifier" o *SolutionName*. Arquivo Application.pkgdef.  
  
##### <a name="the-default-projects-location"></a>O local padrão dos projetos  
 Você pode alterar o nome do local de projetos padrão alterando o valor da linha "DefaultProjectsLocation" o *SolutionName*. Arquivo Application.pkgdef.  
  
##### <a name="the-application-localization-package"></a>O pacote de localização do aplicativo  
 Você pode alterar o pacote de localização usado para seu aplicativo, alterando o valor da linha "AppLocalizationPackage" o *SolutionName*. Arquivo Application.pkgdef.  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>Se deseja ou não mostrar a raiz da hierarquia do título  
 Você pode especificar se deseja ou não mostrar a raiz da hierarquia na barra de título do seu aplicativo, alterando o valor da linha "ShowHierarchyRootInTitle" o *SolutionName*. Arquivo Application.pkgdef. Para mostrar a raiz da hierarquia, defina o valor `dword:00000001`e para ocultar a raiz da hierarquia, defina o valor `dword:00000000`.  
  
##### <a name="specifying-a-start-page"></a>Especificar uma página inicial  
 Para especificar uma página inicial de seu aplicativo personalizado, no *SolutionName*. Arquivo Application.pkgdef, defina o valor de "DisableStartPage" como `dword:00000000`e, em `[$RootKey$\StartPage\Default]` definir o URI para o local do arquivo. XAML:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 No arquivo Applicationcommands.vsct o *SolutionName*da interface do usuário do projeto, comente a entrada "No_ShellPkg_startPageCommand":  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 Você deve adicionar o arquivo. XAML e quaisquer arquivos de gráficos que você precisa para o *SolutionName* projeto. Esses arquivos, na verdade, devem ser copiados para o *SolutionName* diretório do projeto, não são adicionado de algum outro diretório.  
  
 Em todos os arquivos, defina o **o tipo de Item** propriedade **arquivos Shell isolado** para que os arquivos a serem copiados para o *$RootFolder$* directory. (Para definir o **o tipo de Item** propriedade, clique no arquivo e selecione **propriedades**. Essa propriedade é encontrada em **propriedades de configuração**, **geral**.)  
  
 Para obter mais informações sobre como personalizar páginas iniciais, consulte [Personalizando a página Iniciar](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>Usando outros elementos do shell isolado  
 Você pode usar outros arquivos e projetos que são incluídos no modelo de solução de shell isolado para personalizar ainda mais seu aplicativo.  
  
##### <a name="enabledisable-visual-studio-packages"></a>Habilitar/desabilitar pacotes do Visual Studio  
 O *SolutionName*.pkgundef arquivo permite que você desabilite a determinados tipos de funcionalidade do Visual Studio, excluindo certos pacotes. Por exemplo, a seguinte linha:  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 Remove o projeto de arquivos diversos do conjunto de modelos de projeto exibidos na **novo projeto** caixa de diálogo. Para obter mais detalhes, consulte [passo a passo: Criando um aplicativo de Shell isolado básico](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="enabledisable-menu-commands"></a>Habilitar/desabilitar comandos de menu  
 O *SolutionName*UI.vsct arquivo inclui uma lista comentada de todos os comandos de menu disponíveis para o shell isolado. Para desabilitar um determinado comando, remova a linha correspondente. Por exemplo, para desabilitar o comentário/divisão da janela, remova o `<Define name="No_SplitCommand"/>` linha. Para obter mais detalhes, consulte [passo a passo: Criando um aplicativo de Shell isolado básico](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>O bitmap usado na tela inicial  
 Você pode personalizar o bitmap usado na tela inicial, que é a janela que é exibida quando o aplicativo é iniciado, alterando o valor da linha "SplashScreenBitmap" o *SolutionName*. Arquivo Application.pkgdef. Para obter mais detalhes, consulte [passo a passo: Criando um aplicativo de Shell isolado básico](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-helpabout-window"></a>A Ajuda/sobre a janela  
 No modelo de shell isolado, há um projeto separado, você pode usar para personalizar a Ajuda/sobre caixa para seu aplicativo. Para obter mais detalhes, consulte [passo a passo: Criando um aplicativo de Shell isolado básico](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).
