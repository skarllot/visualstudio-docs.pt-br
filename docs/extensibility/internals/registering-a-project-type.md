---
title: Registrar um tipo de projeto | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
caps.latest.revision: 21
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
ms.openlocfilehash: 121e38d20d2139619cdac46d5c3485c099297981
ms.lasthandoff: 02/22/2017

---
# <a name="registering-a-project-type"></a>Registrar um tipo de projeto
Quando você cria um novo tipo de projeto, você deve criar entradas do registro que permitem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] reconhecer e trabalhar com o tipo de projeto. Você normalmente cria essas entradas do registro usando um arquivo de script (. rgs) do registro.  
  
 No exemplo abaixo, as instruções do registro fornecem caminhos padrão e dados, onde aplicável, seguido por uma tabela que contém entradas do script do registro para cada instrução. As tabelas fornecem as entradas de script e informações adicionais sobre as instruções.  
  
> [!NOTE]
>  As seguintes informações de registro destina-se a ser um exemplo do tipo e fins de entradas nos scripts de registro, que você escreverá para registrar o tipo de projeto. Suas entradas reais e seus usos podem variar com base nos requisitos específicos do seu tipo de projeto. Você deve revisar os exemplos disponíveis para localizar um parecida com o tipo de projeto que você está desenvolvendo e, em seguida, revise o script de registro para esse exemplo.  
  
 Os exemplos a seguir são de HKEY_CLASSES_ROOT.  
  
## <a name="example"></a>Exemplo  
  
```  
\.figp  
   @="FigPrjFile"  
   "Content Type"="text/plain"  
\.figp\ShellNew  
   "NullFile"=""  
\FigPrjFile  
   @="Figure Project File"  
\DefaultIcon  
   @="<Visual Studio SDK installation path>\\9.0VSIntegration\\SomeFolder\\FigPkgs\\FigPrj\\Debug\\FigPrj.dll,-206"  
\shell\open  
   @="&Open in Visual Studio"  
\shell\open\command  
   @="devenv.exe \"%1\""  
```  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrjFile`|Nome e descrição dos arquivos de tipo de projeto que têm a extensão .figp.|  
|`Content Type`|REG_SZ|`Text/plain`|Tipo de conteúdo para os arquivos de projeto.|  
|`NullFile`|REG_SZ|`Null`||  
|`@`|REG_SZ|`%MODULE%,-206`|Ícone padrão usado para um projeto desse tipo. A instrução de % % módulo é concluída no registro para o local padrão do tipo de projeto DLL.|  
|`@`|REG_SZ|`&Open in Visual Studio`|Aplicativo padrão em que esse tipo de projeto será aberto.|  
|`@`|REG_SZ|`devenv.exe "%1"`|Comando padrão que será executado quando um projeto desse tipo é aberto.|  
  
 Os exemplos a seguir são de HKEY_LOCAL_MACHINE e estão localizados no registro na chave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages].  
  
## <a name="example"></a>Exemplo  
  
```  
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)  
   @="FigPrj Project Package"  
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"  
   "CompanyName"="Microsoft"  
   "ProductName"="Figure Project Sample"  
   "ProductVersion"="9.0"  
   "MinEdition"="professional"  
   "ID"=dword:00000001  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\SatelliteDLL  
   "DllName"="FigPrjUI.dll"  
   "Path"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\Debug\\"  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\Automation  
   "FigProjects"=""  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\AutomationEvents  
   "FigProjectsEvents"="Returns the FigProjectsEvents Object"  
   "FigProjectItemsEvents"="Returns the FigProjectItemsEvents Object"  
```  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|----------|-----------------|  
|`@`(Padrão)|REG_SZ|`FigPrj Project VSPackage`|Nome localizável dessa registrado VSPackage (tipo de projeto).|  
|`InprocServer32`|REG_SZ|`%MODULE%`|Caminho da DLL do tipo de projeto. O IDE carrega dessa DLL e passa o CLSID VSPackage para `DllGetClassObject` obter <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory>para construir o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>objeto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> </xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory>|  
|`CompanyName`|REG_SZ|`Microsoft`|Nome da empresa que desenvolveu o tipo de projeto.|  
|`ProductName`|REG_SZ|`Figure Project Sample`|Nome para o tipo de projeto.|  
|`ProductVersion`|REG_SZ|`9.0`|Número de versão do tipo de projeto de versão.|  
|`MinEdition`|REG_SZ|`professional`|Edição do VSPackage que está sendo registrado.|  
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|O pacote carregar a chave para o projeto de VSPackage. A chave é validada quando um projeto é carregado depois que o ambiente for iniciada.|  
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Nome do arquivo da DLL que contém recursos localizados para o tipo de projeto de satélite.|  
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Caminho da DLL satélite.|  
|`FigProjectsEvents`|REG_SZ|Consulte a declaração de valor.|Determina a sequência de caracteres de texto retornada para este evento de automação.|  
|`FigProjectItemsEvents`|REG_SZ|Consulte a declaração de valor.|Determina a sequência de caracteres de texto retornada para este evento de automação.|  
  
 Todos os exemplos a seguir estão localizados no registro na chave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Exemplo  
  
```  
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)  
   @="FigPrj Project"  
   "DisplayName"="#2"  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"  
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"  
   "DisplayProjectFileExtensions"="#3"  
   "PossibleProjectExtensions"="figp"  
   "DefaultProjectExtension"=".figp"  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)  
   @="#4"  
   "CommonOpenFilesFilter"=dword:00000000  
   "CommonFindFilesFilter"=dword:00000000  
   "NotAddExistingItemFilter"=dword:00000000  
   "FindInFilesFilter"=dword:00000000  
   "NotOpenFileFilter"=dword:00000000  
   "SortPriority"=dword:000003e8  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\2  
      (Folder 2 contains settings for Find in Files filters.)  
   @="#5"  
   "CommonOpenFilesFilter"=dword:00000000  
   "CommonFindFilesFilter"=dword:00000000  
   "NotAddExistingItemFilter"=dword:00000001  
   "FindInFilesFilter"=dword:00000001  
   "NotOpenFileFilter"=dword:00000000  
   "SortPriority"=dword:000003e8  
\{C061DB26-5833-11D2-96F5-000000000000}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (Second GUID indicates the registered project type for the Add Items templates.)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrj Project`|Nome padrão de projetos desse tipo.|  
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|ID de recurso de nome devem ser recuperados a DLL satélite registrados em pacotes.|  
|`Package`|REG_SZ|`%CLSID_Package%`|ID de classe do VSPackage é registrado em pacotes.|  
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Caminho padrão dos arquivos de modelo de projeto. Esses são os arquivos exibidos pelo modelo do novo projeto.|  
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Caminho padrão dos arquivos de modelo de Item de projeto. Esses são os arquivos exibidos pelo modelo Add New Item.|  
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Permite que o IDE implementar o **abrir** caixa de diálogo.|  
|`PossibleProjectExtensions`|REG_SZ|`figp`|Usado pelo IDE para determinar se o projeto que está sendo aberto é tratado por esse tipo de projeto (fábrica de projeto). O formato de mais de uma entrada é uma lista delimitada por-e-vírgula. Por exemplo "vdproj; vdp".|  
|`DefaultProjectExtension`|REG_SZ|`.figp`|Usado pelo IDE como a extensão de nome de arquivo padrão para a operação Salvar como.|  
|`Filter Settings`|REG_DWORD|Várias, consulte as instruções e comentários a tabela a seguir.|Essas configurações são usadas para definir vários filtros para exibir arquivos nas caixas de diálogo da interface do usuário.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|ID de recurso para Adicionar Item templates.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Caminho dos itens de projeto exibido na caixa de diálogo para o **Adicionar Novo Item** modelo.|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Determina a ordem de classificação no nó de árvore dos arquivos exibidos na **Adicionar Novo Item** caixa de diálogo.|  
  
 A tabela a seguir mostra as opções de filtros disponíveis no segmento de código anterior.  
  
|Opção de filtro|Descrição|  
|-------------------|-----------------|  
|`CommonFindFilesFilter`|Indica que o filtro é um dos filtros em comum o **localizar em arquivos** caixa de diálogo. Os filtros comuns são listados na lista de filtros antes dos filtros não marcado como comuns.|  
|`CommonOpenFilesFilter`|Indica que o filtro é um dos filtros em comum o **abrir arquivo** caixa de diálogo. Os filtros comuns são listados na lista de filtros antes dos filtros não marcado como comuns.|  
|`FindInFilesFilter`|Indica que o filtro será um dos filtros no **localizar em arquivos** caixa de diálogo caixa e será listado após os filtros comuns.|  
|`NotOpenFileFilter`|Indica que o filtro não será usado no **abrir arquivo** caixa de diálogo.|  
|`NotAddExistingItemFilter`|Indica que o filtro não será usado no adicionar **Item existente** caixa de diálogo.|  
  
 Por padrão, se um filtro não tem um ou mais dos seguintes sinalizadores de conjunto, o filtro é usado no **Add Existing Item** caixa de diálogo e o **abrir arquivo** caixa de diálogo após os filtros comuns são listados. O filtro não é usado no **localizar em arquivos** caixa de diálogo.  
  
 Todos os exemplos a seguir estão localizados no registro na chave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Exemplo  
  
```  
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)  
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|ID de recurso para modelos de projeto novo.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Caminho para projetos do tipo de projeto registrado padrão.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Conjuntos de ordem de classificação dos projetos exibidos na caixa de diálogo do Assistente para novos projetos.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 indica que os projetos deste tipo são exibidos somente na caixa de diálogo Novo projeto.|  
  
 Todos os exemplos a seguir estão localizados no registro na chave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Exemplo  
  
```  
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)  
   @="Miscellaneous Files Project"  
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1  
                                 (CLSID for Figures Project projects)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|Nenhum|Valor padrão que indica que as entradas a seguir são para as entradas de projetos arquivos diversos.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Valor de ID de recurso para os arquivos de modelo de adicionar novos itens.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|O caminho padrão dos itens que serão exibidos no **Adicionar Novo Item** caixa de diálogo.|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Estabelece a ordem de classificação para exibição no nó de árvore de **Adicionar Novo Item** caixa de diálogo.|  
  
 O exemplo a seguir encontra-se no registro na chave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus].  
  
## <a name="example"></a>Exemplo  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 A entrada de menu aponta o IDE para o recurso usada para recuperar as informações de menu. Quando esses dados foi mesclados com o banco de dados do menu, a mesma chave será adicionada na seção MenusMerged do registro. O VSPackage não deve modificar nada na seção MenusMerged diretamente. No campo de dados na tabela a seguir, há três vírgula--campos separados. O primeiro campo identifica um caminho completo de um arquivo de recurso do menu:  
  
-   Se o primeiro campo for omitido, o recurso de menu é carregado da DLL identificado pelo GUID VSPackage satélite.  
  
 O segundo campo identifica uma ID de recurso do menu do tipo CTMENU:  
  
-   Se a ID de recurso é especificada, e o caminho do arquivo é fornecido pelo primeiro parâmetro, um recurso do menu é carregado do caminho de arquivo completo.  
  
-   Se a ID de recurso é fornecida, mas o caminho do arquivo não é, o recurso de menu é carregado da DLL satélite.  
  
-   Se o caminho completo é fornecido e a ID de recurso é omitido, o arquivo a ser carregado deve ser um arquivo CTO.  
  
 O último campo identifica o número de versão para o recurso CTMENU. Você pode mesclar o menu novamente, alterando o número de versão.  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|----------|-----------------|  
|% CLSID_Package %|REG_SZ|`,1000,1`|O recurso para recuperar as informações de menu.|  
  
 Todos os exemplos a seguir estão localizados no registro na chave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates].  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Valor de ID de recurso para os modelos de projeto figuras novo projeto.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Caminho padrão do diretório novos projetos. Itens nessa pasta serão exibidos na **Assistente de novo projeto** caixa de diálogo.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Estabelece a ordem na qual projetos serão exibidos no nó de árvore de **novo projeto** caixa de diálogo.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 indica que os projetos deste tipo são exibidos somente no **novo projeto** caixa de diálogo.|  
  
 O exemplo a seguir encontra-se no registro na chave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts].  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|----------|-----------------|  
|`Package`|REG_SZ|`%CLSID_Package%`|ID de classe do VSPackage registrado.|  
|`UseInterface`|REG_DWORD|`1`|1 indica que a interface do usuário será usada para interagir com este projeto. 0 indica que não há nenhuma interface do usuário.|  
  
 Arquivos de the.vsz que controlam os novos tipos de projeto frequentemente contêm uma entrada RELATIVE_PATH. Esse caminho é relativo ao caminho especificado na entrada \ProductDir do tipo de projeto na seguinte chave de instalação:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup  
  
 Por exemplo, os modelos de projeto do Enterprise Frameworks adicione as seguintes entradas de registro:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files\Microsoft Visual Studio\EnterpriseFrameworks\  
  
 Isso significa que se você incluir um PROJECT_TYPE = entrada EF no arquivo. vsz, localiza o ambiente que seu vsz arquivos no diretório ProductDir especificado anteriormente.  
  
## <a name="see-also"></a>Consulte também  
 [Lista de verificação: Criar novos tipos de projeto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Elementos de um modelo de projeto](../../extensibility/internals/elements-of-a-project-model.md)   
 [Criação de instâncias de projetos usando fábricas de projeto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
