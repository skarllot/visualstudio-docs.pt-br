---
title: "Página Opções, Propriedades do Nó de Ambiente | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio], controlling Tools Options
- Tools Options settings, Environment node properties
ms.assetid: 26dca41f-91fc-4ca7-9103-3da402baa1d5
caps.latest.revision: 18
author: kempb
ms.author: kempb
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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: ac450b7e414596632d56117813907ee4406ad69d
ms.lasthandoff: 02/22/2017

---
# <a name="options-page-environment-node-properties"></a>Página de Propriedades, Ambiente, Propriedades do Nó
Este documento descreve as páginas (ou coleções de propriedades) associadas a uma categoria **Ambiente**, `DTE.Properties("Environment", <Property Page>)`, da caixa de diálogo **Opções**. O título de cada subseção é a chamada usada para acessar a coleção Propriedades e a tabela em cada subseção lista as propriedades na coleção.  
  
## <a name="general"></a>Geral  
 `DTE.Properties("Environment", "General")`  
  
|Nome do item de propriedade|Valor|Descrição|  
|------------------------|-----------|-----------------|  
|ShowStatusBar|Get/Set (Booliano)|Determina se a barra de status está visível.|  
|WindowMenuContainsNItems|Get/Set (Curto)|Determina como as janelas de documento são contidas na parte inferior do menu do Windows.|  
|MRUListContainsNItems|Get/Set (Curto)|Determina quantos arquivos são exibidos no submenu "Usados Mais Recentemente".|  
|Animations|Get/Set (Booliano)|Determina se o IDE (ambiente de desenvolvimento integrado) usa animação na barra de status.|  
|AnimationSpeed|Get/Set (Curto)||  
|AutoAdjustExperience|Get/Set (Booliano)|Ajusta automaticamente a experiência visual conforme o desempenho do cliente.|  
|RichClientExperienceOptions|Get/Set (Enum)|Habilita a experiência visual do cliente avançado com valores em <xref:EnvDTE100.vsRichClientExperienceOptions>.|  
|CloseButtonActiveTabOnly|Get/Set (Booliano)|Determina se o botão **Fechar** é exibido somente na guia ativa.|  
|AutohidePinActiveTabOnly|Get/Set (Booliano)|Determina se o botão **Ocultar Automaticamente** afeta somente a guia ativa.|  
  
## <a name="add-inmacros-security"></a>Segurança de Suplemento/Macros  
 `DTE.Properties("Environment", "AddinMacrosSecurity")`  
  
|Nome do item de propriedade|Valor|Descrição|  
|------------------------|-----------|-----------------|  
|MacrosEnabled|Get/Set (Booliano)|Permite a execução de macros.|  
|AddinsEnabled|Get/Set (Booliano)|Permite o carregamento de suplementos.|  
|LoadAddinsFromTheWeb|Get/Set (Booliano)|Permite o carregamento de suplementos de uma URL na Web.|  
  
## <a name="documents"></a>Documentos  
 `DTE.Properties("Environment", "Documents")`  
  
|Nome do item de propriedade|Valor|Descrição|  
|------------------------|-----------|-----------------|  
|ReuseSavedActiveDocWindow|Get/Set (Booliano)|Determina se abrir um novo arquivo reutiliza a janela do documento atual se o documento atual for salvo. `false` significa sempre abrir uma nova janela do documento para cada documento aberto.|  
|DetectFileChangesOutsideIDE|Get/Set (Booliano)|Determina se o ambiente recarrega automaticamente arquivos abertos no IDE quando o sistema operacional notifica o IDE de que os arquivos foram modificados no disco.|  
|AutoloadExternalChanges|Get/Set (Booliano)|Determina se modificações externas detectadas a documentos abertos recarregarão automaticamente o arquivo modificado se o documento aberto não for modificado. Se o documento aberto for modificado e essa propriedade for `true`, o IDE avisará como se essa propriedade fosse `false`.|  
|InitializeOpenFileFromCurrentDocument|Get/Set (Booliano)|Determina se o comando <xref:EnvDTE.DTEClass.OpenFile%2A> propaga o nome de arquivo e diretório do último documento ativo ou do último lugar em que você abriu um arquivo.|  
|MiscFilesProjectSavesLastNItems|Get/Set (Curto)|Determina quantos arquivos o projeto Arquivos Diversos registra. Como resultado, você poderá ver o que você abriu mais recentemente como um arquivo diverso no disco na próxima vez que usar o IDE.|  
|ShowMiscFilesProject|Get/Set (Booliano)|Determina se o projeto Arquivos Diversos é mostrado.|  
|CheckForConsisentLineEndings|Get/Set (Booliano)|Verifica se há terminações consistentes de linha no carregamento do arquivo.|  
|SaveDocsAsUnicodeWhenDataLoss|Get/Set (Booliano)|Salva documentos como Unicode quando os dados não podem ser salvos na página de código.|  
|DontShowGlobalUndoChangeLossDialog|Get/Set (Booliano)|Exibe um aviso quando desfazer global for modificar outros arquivos editados.|  
|AllowEditingReadOnlyFiles|Get/Set (Booliano)|Permite a edição de arquivos somente leitura, mas fornece um aviso quando há uma tentativa de salvá-los.|  
|DocumentDockPreference|Get/Set (Enum)|<xref:EnvDTE100.vsDocumentDockPreferenceOptions>. Posição na guia bem na qual inserir o documento aberto.|  
  
## <a name="extension-manager"></a>Gerenciador de Extensões  
 `DTE.Properties("Environment", "ExtensionManager")`  
  
|Nome do item de propriedade|Valor|Descrição|  
|------------------------|-----------|-----------------|  
|EnableAdminExtensions|Get/Set (Booliano)|Carrega extensões por usuário quando o Visual Studio é executado com credenciais de Administrador. O Visual Studio deve ser reiniciado depois da alteração desse valor.|  
|EnableOnline|Get/Set (Booliano)|Permite acesso a extensões na Galeria do Visual Studio.|  
|AutomaticallyCheckForUpdates|Get/Set (Booliano)|Verifica automaticamente atualizações a extensões instaladas.|  
  
## <a name="find-and-replace"></a>Localizar e Substituir  
 `DTE.Properties("Environment", "FindAndReplace")`  
  
|Nome do item de propriedade|Valor|Descrição|  
|------------------------|-----------|-----------------|  
|ShowWarningMessages|Get/Set (Booliano)|Exibe mensagens de aviso.|  
|InitializeFromEditor|Get/Set (Booliano)|Preenche automaticamente a caixa **O Que Localizar** do editor.|  
|ShowMessageBoxes|Get/Set (Booliano)|Exibe mensagens informativas.|  
|HideWindowsAfterMatchFromQuickFindReplace|Get/Set (Booliano)|Oculta a janela **Localizar e Substituir** depois que uma correspondência é localizada usando **Localização Rápida** ou **Substituição Rápida**.|  
  
## <a name="import-and-export-settings"></a>Importar e exportar configurações  
 `DTE.Properties("Environment", "Import and Export Settings")`  
  
|Nome do item de propriedade|Valor|Descrição|  
|------------------------|-----------|-----------------|  
|TrackTeamSettings|Get/Set (Booliano)|Usa as configurações no arquivo especificado por TeamSettingsFile.|  
|TeamSettingsFile|Get/Set (Cadeia de Caracteres)|Nome do arquivo que tem configurações de equipe.|  
|AutoSaveFile|Get/Set (Cadeia de Caracteres)|Nome do arquivo no qual as configurações do usuário são salvas automaticamente.|  
  
## <a name="international-settings"></a>Configurações internacionais  
 `DTE.Properties("Environment", "International")`  
  
|Nome do item de propriedade|Valor|Descrição|  
|------------------------|-----------|-----------------|  
|Linguagem|Get/Set (Cadeia de Caracteres)|Valor LCID para o idioma atual do Visual Studio.|  
  
## <a name="keyboard"></a>Teclado  
 `DTE.Properties("Environment", "Keyboard")`  
  
|Nome do item de propriedade|Valor|Descrição|  
|------------------------|-----------|-----------------|  
|Esquema|Get/Set (Cadeia de Caracteres)|Retornará uma cadeia de caracteres que contém um esquema interno, uma cadeia de caracteres que contém o caminho completo do arquivo .vsk que é carregado ou "(Padrão)" se nenhum arquivo .vsk for carregado.|  
  
## <a name="projects-and-solution"></a>Projetos e Solução  
 `DTE.Properties("Environment", "ProjectsAndSolution")`  
  
|Nome do item de propriedade|Valor|Descrição|  
|------------------------|-----------|-----------------|  
|OnRunOrPreview|Get/Set (Cadeia de Caracteres)|Determina se o IDE salva tudo antes de visualizar ou executar um projeto compilado.|  
|ProjectsLocation|Get/Set (Cadeia de Caracteres)|Determina o diretório padrão no qual a caixa de diálogo **Adicionar Projeto** salva novos projetos.|  
|ShowOutputWindowBeforeBuild|Get/Set (Booliano)|Determina se iniciar um build exibe a Janela de **Saída**.|  
|ShowTaskListAfterBuild|Get/Set (Booliano)|Determina se uma operação de build bem-sucedida exibe a **Lista de Tarefas** quando o build é concluído.|  
|TrackFileSelectionInExplorer|Get/Set (Booliano)|Determina se o item atual é rastreado no **Gerenciador de Soluções**.|  
|AlwaysShowSolutionNode|Get/Set (Booliano)|Determina se o nó da solução é exibido.|  
|OnlySaveStartupProjectsAndDependencies|Get/Set (Booliano)|Determina se operações de salvar estão limitadas a projetos de inicialização e seus arquivos dependentes.|  
|ShowAdvancedBuildConfigurations|Get/Set (Booliano)|Determina se configurações de build avançadas são exibidas.|  
|ConcurrentBuilds|Get/Set (Cadeia de Caracteres)|Determina o número máximo de compilações paralelas de projetos que podem ocorrer.|  
|SaveNewProjects|Get/Set (Booliano)|Determina se os novos projetos são salvos automaticamente após a criação.|  
|PromptForRenameSymbol|Get/Set (Booliano)|Especifica se renomeação simbólica deverá ser solicitada quando os arquivos forem renomeados.|  
|OnRunWhenErrors|Get/Set (Enum)|Especifica o comportamento em Execução quando um build é concluído com erros.|  
|OnRunWhenOutOfDate|Get/Set (Enum)|Especifica o comportamento em Execução quando um projeto está desatualizado.|  
|ProjectTemplatesLocation|Get/Set (Cadeia de Caracteres)|Diretório que contém modelos de projeto do usuário.|  
|ProjectItemTemplatesLocation|Get/Set (Cadeia de Caracteres)|Diretório que contém modelos de item do usuário.|  
|DefaultBehaviorForStartupProjects|Get/Set (Cadeia de Caracteres)||  
|MSBuildOutputVerbosity|Get/Set (Cadeia de Caracteres)|Especifica o nível de detalhamento para a saída de Build.|  
  
## <a name="startup"></a>Inicialização  
 `DTE.Properties("Environment", "Startup")`  
  
|Nome do item de propriedade|Valor|Descrição|  
|------------------------|-----------|-----------------|  
|OnStartUp|Get/Set (Enum)|Ação a ser adotada na inicialização, de <xref:EnvDTE.vsStartUp>, com valores de 0 a 5:<br /><br /> –   0: Abrir Página Inicial<br />–   1: Carregar última solução carregada<br />–   2: Mostrar caixa de diálogo **Abrir Projeto**<br />–   3: Mostrar caixa de diálogo **Novo Projeto**<br />–   4: Mostrar ambiente vazio<br />–   5: Mostrar Página Inicial|  
|StartPageRSSUrl|Get/Set (Cadeia de Caracteres)|URL para o RSS feed usado na inicialização.|  
|StartPageRefreshDownloadedContent|Get/Set (Booliano)|Atualiza a Página Inicial após cada passagem do intervalo especificado em StartPageRefreshInterval.|  
|StartPageRefreshInterval|Get/Set (Curto)|Intervalo em minutos para atualizar a Página Inicial.|  
  
## <a name="tasklist"></a>TaskList  
 `DTE.Properties("Environment", "TaskList")`  
  
|Nome do item de propriedade|Valor|Descrição|  
|------------------------|-----------|-----------------|  
|ConfirmTaskDeletion|Get/Set (Booliano)|Especifica se uma caixa de confirmação será exibida ao excluir tarefas da **Lista de Tarefas**.|  
|WarnOnAddingHiddenItem|Get/Set (Booliano)|Especifica se você será avisado ao adicionar uma tarefa do usuário que não será exibida.|  
|DontShowFilePaths|Get/Set (Booliano)|Especifica se serão mostrados caminhos completos de arquivos na Lista de Tarefas.|  
|CommentTokens|SafeArray|Retorna um SafeArray de valores do token de comentário. Cada um tem os campos, `Name` (cadeia de caracteres) e `Priority` (<xref:EnvDTE.vsTaskPriority>, alta, média ou baixa).|  
  
## <a name="web-browser"></a>Navegador da Web  
 `DTE.Properties("Environment", "WebBrowser")`  
  
|Nome do item de propriedade|Valor|Descrição|  
|------------------------|-----------|-----------------|  
|HomePage|Get/Set (Cadeia de Caracteres)|Representa a URL da home page.|  
|SearchPage|Get/Set (Cadeia de Caracteres)|Representa a URL da página de pesquisa.|  
|ViewSourceIn|Get/Set (Enum)|<xref:EnvDTE.vsBrowserViewSource> (Fonte, Design, Externo).|  
|ViewSourceExternalProgram|Get/Set (Cadeia de Caracteres)|O caminho do visualizador da fonte externa.|  
  
## <a name="see-also"></a>Consulte também  
 [Controlando configurações de opções](http://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)   
 [Determinando os nomes de itens de propriedades em páginas de opções](http://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)   
 [Página Opções, Propriedades do Nó de Fontes e Cores](../../ide/reference/options-page-fonts-and-colors-node-properties.md)   
 [Página Opções, Propriedades do Nó de Editor de Texto](../../ide/reference/options-page-text-editor-node-properties.md)   
 [Caixa de diálogo Opções do Ambiente](../../ide/reference/environment-options-dialog-box.md)
