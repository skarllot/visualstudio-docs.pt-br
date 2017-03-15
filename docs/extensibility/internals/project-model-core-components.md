---
title: Componentes principais do modelo de projeto | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
caps.latest.revision: 17
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
ms.openlocfilehash: 7d00960ab559fe24ec811017e7b73c3d5b6416d5
ms.lasthandoff: 02/22/2017

---
# <a name="project-model-core-components"></a>Componentes principais do projeto modelo
As tabelas a seguir expandem o modelo de projeto. As tabelas presentes breves descrições de interfaces e serviços identificados no modelo e as interfaces e os serviços associados a objetos específicos. Além disso, as tabelas de detalham sobre outras interfaces são opcionais na criação do projeto e na manutenção dependendo dos requisitos do seu tipo de projeto específico.  
  
 Para obter mais informações, consulte [ferramentas de navegação de símbolo de suporte](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
### <a name="package-object"></a>Objeto de pacote  
  
|Interface|Comentários|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage></xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Inicializa um VSPackage no IDE e disponibiliza os serviços ao IDE.|  
  
### <a name="project-factory-object"></a>Objeto de fábrica de projeto  
  
|Interface|Comentários|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory></xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Gerencia a criação de novos projetos e abrir projetos existentes.|  
  
### <a name="project-objects"></a>Objetos do projeto  
  
|Interfaces|Comentários|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Gerencia a adição e remoção de itens de projeto abre editores e mantém o mapeamento entre cada moniker do documento e o `VSITEMID`. Herda de `IVsProject` e `IVsProject2`.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Gerencia as propriedades de navegação e exibição e fornece eventos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Habilita o comando execução similar do `IOleCommandTarget` para comandos como Recortar e renomeie que se aplicam somente quando o foco está no Gerenciador de soluções.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Serve como a interface de destino principal comando para uma hierarquia de projeto. É a interface padrão para consultar os objetos para os comandos de status ou o estado e a execução do comando. Disponível quando você não estiver concentrado na janela do projeto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat></xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Coordena a persistência do estado do projeto. Normalmente, o estado do projeto é armazenado como um arquivo de projeto, mas pode ser adaptado para sistemas de armazenamento que não são baseados em arquivo.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Permite que o projeto gerenciar todos os aspectos de persistência para seus itens de projeto, como arquivos em disco ou objetos em outros sistemas de armazenamento. O `IVsPeristHierarchyItem2` interface é usada para itens que não implementam o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Coordena as interações com controle do código fonte.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Permite que os projetos gerenciar informações de configuração.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Gerencia objetos de configuração de projeto, como configurações de Debug/Release. Compilar, implantar e depurar as operações são coordenadas por meio de objetos de configuração do projeto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Implementado por hierarquias para controlar a exclusão (destrutiva) ou remover opções (não-destrutiva) para os itens de hierarquia. Chamar a Interface de consulta o `IVsHierarchyDeleteHandler` de interface do `IVsHierarchy` interface.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Fornece a opção de implementação de ter o objeto que suporta o `IVsCfgProvider2` interface em uma identidade diferente do COM que o objeto de projeto que implementa o `IVsHierarchy` interface.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices></xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Interface opcional implementada para tornar seu projeto extensível por outros desenvolvedores. O `IVsProjectStartupServices` interface permite que um VSPackage de terceiros registrar um GUID que você persistir em seu arquivo de projeto para que toda vez que o projeto for carregado, você carrega o GUID do serviço de terceiros em seu arquivo de projeto e chame `QueryService` para GUID.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Implementado por hierarquias de origem em um `UIHierarchy` janela coordenar operações da área de transferência como Recortar, copiar e colar. Use o `AdviseClipboardHelperEvents` interface para registrar eventos de área de transferência.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Fornece informações sobre um item arrastado em relação a sua fonte de dados durante uma operação de arrastar e soltar em uma janela de hierarquia de interface do usuário. Chamado a partir do `IVsHierarchy` interface.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Fornece informações sobre um item arrastado em relação ao seu destino de soltar durante uma operação de arrastar e soltar em uma janela de hierarquia de interface do usuário. Chamado a partir do `IVsHierarchy` interface.|  
  
### <a name="configuration-object"></a>Objeto de configuração  
  
|Interfaces|Comentários|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Fornece informações sobre uma configuração.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2></xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Permite que os projetos gerenciar informações de configuração.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg></xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Permite que um projeto ser executado sob o controle do depurador.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg></xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Implementado por projetos de implantação que executam operações de implantação para outros projetos.|  
  
### <a name="configuration-builder-object"></a>Objeto de configuração do construtor  
  
|Interfaces|Comentários|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg></xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Gerencia a operação de criação de uma configuração projeto.|  
  
### <a name="additional-project-objects"></a>Objetos de projeto adicionais  
  
|Interfaces|Comentários|  
|----------------|--------------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages></xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Exibe propriedades de item de **propriedades** janela.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2></xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs></xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Exibe os resultados para implantação.|  
  
 A tabela a seguir apresenta breves descrições dos serviços identificados no modelo de projeto.  
  
### <a name="services"></a>Serviços  
  
|Serviço|Comentários|  
|-------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes></xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Usado por VSPackages que implementam os tipos de projeto para registrar que sua fábrica de projeto existe no IDE. O VSPackage deverá chamar `QueryService` para este serviço e registrar sua fábrica de projeto quando `IVsPackage::SetSite` método é chamado. Se o `SetSite` método não é chamado, o projeto não seja instanciado.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution></xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fornece acesso a noção de internos, interna do IDE da solução atual, como a capacidade de enumerar os projetos, criar novos projetos, observar alterações no projeto e assim por diante.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager></xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Chamado por projetos que deseja participar no controle de origem.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable></xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Mantém uma tabela de documentos abertos para determinar se um ou mais dos seus itens de projeto já estiverem aberto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument></xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Contém as interfaces e métodos chamados para realmente abrir um item de projeto usando o editor padrão ou um editor específico.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments></xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Deve ser chamado por todos os projetos quando adicionar, remover ou renomear seus itens.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx></xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Gerencia as alterações em um arquivo ou diretório e notifica os clientes quando os arquivos selecionados foram alterados no disco.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave></xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Deve ser chamado por todos os projetos e editores antes de serem sujos itens ou salvá-los.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager></xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Gerencia a ordem das operações de compilação e implantação de configurações de projeto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger></xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Fornece acesso a serviços de depurador de nível baixo usados para a maioria dos controles de depuração.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection></xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Habilita os VSPackages acesso a informações sobre seleções atuais e permite a comunicação com o **propriedades** janela.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell></xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fornece a funcionalidade básica do IDE relacionados à interface do usuário, como a capacidade de criar e enumerar janelas de ferramentas ou janelas de documento ou relatar um erro para o usuário.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar></xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Fornece acesso à barra de status do IDE.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3></xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Usado para implementar o modelo de automação. O modelo de projeto, você retornará um objeto de propriedades que permite que você cria uma instância desse objeto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper></xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Usado para implementar eventos de área de transferência no objeto de projeto na hierarquia. `SVsUIHierWinClipboardHelper`permite que você corretamente identificador recortar, copiar e colar.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Lista de verificação: Criar novos tipos de projeto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Não na compilação: usando Classes do projeto HierUtil7 para implementar um tipo de projeto (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Suporte a ferramentas de navegação de símbolo](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Elementos de um modelo de projeto](../../extensibility/internals/elements-of-a-project-model.md)
