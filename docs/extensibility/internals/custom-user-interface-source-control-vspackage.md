---
title: "Interface do usuário personalizada (VSPackage de controle de origem) | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
caps.latest.revision: 28
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
ms.openlocfilehash: 0d4940ea62ac65671ffcb3bb29958e3d2e544c09
ms.lasthandoff: 02/22/2017

---
# <a name="custom-user-interface-source-control-vspackage"></a>Interface do usuário personalizada (VSPackage de controle de origem)
Um VSPackage declara seus itens de menu e seus estados padrão por meio do arquivo de tabela de comando do Visual Studio (VSCT). O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE) exibe os itens de menu em seus estados padrão até que o VSPackage é carregado. Em seguida, o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>método é chamado para habilitar ou desabilitar itens de menu.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>  
  
 Um VSPackage pode definir uma chave do registro para que o VSPackage possa ser carregado automaticamente dependendo do contexto de interface do usuário de um usuário de comando, embora geralmente controlam a uma fonte de VSPackage deverá ser carregado sob demanda em vez de simplesmente alternar para um determinado contexto de interface do usuário. Para obter mais informações sobre a chave de registro AutoLoadPackages, consulte [Gerenciando VSPackages](../../extensibility/managing-vspackages.md).  
  
## <a name="vspackage-ui"></a>Interface de usuário de VSPackage  
 Um pacote de controle de origem é implementado como um VSPackage e não usa nenhuma interface de usuário do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Cada controle de origem VSPackage deve especificar seus próprios elementos de interface do usuário, como itens de menu, grupos de menus, janelas de ferramentas, barras de ferramentas e nenhuma interface de usuário necessário para definir opções específicas para o controle de origem VSPackage. Esses elementos de interface do usuário podem ser habilitados estática ou dinamicamente. Elementos de interface do usuário estáticos são definidos em um arquivo. VSCT e são exibidos se o VSPackage é carregado ou não. Elementos de interface do usuário dinâmicos podem ser visíveis dependendo do contexto de interface de usuário um comando específico, como <xref:EnvDTE.Constants.vsContextNoSolution>, ou como resultado de uma chamada para o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>método.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> </xref:EnvDTE.Constants.vsContextNoSolution> A visibilidade dos elementos de interface do usuário dinâmicos está em conformidade com a estratégia de carregamento atrasado de VSPackages.  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>Restrições de interface do usuário em VSPackages de controle de origem  
 Como o controle de origem VSPackage não pode ser removido do IDE depois que ele é carregado, o VSPackage deve ser capaz de entrar em um estado inativo. Quando um VSPackage recebe notificação que ele não está mais ativo o VSPackage desabilita sua interface do usuário e ignora qualquer interação externa do IDE. Implementação do VSPackage o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>método deve ocultar comandos quando o VSPackage não está ativo.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>  
  
 Cada controle de origem VSPackage deve implementar o `IVsSccProvider` interface. Dois métodos na interface, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>, devem ser implementados por VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>  
  
 O VSPackage pode se inscrever para vários eventos IDE, que são implementados pelo controle da fonte de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>e assim por diante.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> Além disso, o VSPackage pode ter implementado interfaces de retorno de chamada do registro habilitado, como <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> Elas devem todos ser ignoradas quando inativo.  
  
 A lista a seguir mostra as interfaces afetadas pelo estado ativo de um controle de origem VSPackage:  
  
-   Rastrear eventos de documentos de projeto.  
  
-   Eventos de solução.  
  
-   Interfaces de persistência da solução. Quando estiver inativo, pacotes não devem gravar arquivos. sln e. suo.  
  
-   Extensores de propriedade.  
  
 Necessário <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, e também quaisquer interfaces opcionais associados com o controle de origem, não são chamados quando o controle de origem VSPackage está inativo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> </xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
  
 Quando o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE é iniciado, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] define o contexto de interface do usuário de comando para a identificação do controle de origem de padrão atual ID VSPackage. Isso faz com que a interface do usuário estática do controle de origem ativa VSPackage apareça no IDE sem realmente carregar o VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]pausa para registrar com o VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] por meio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>antes de fazer as chamadas para o VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>  
  
 A tabela a seguir descreve detalhes específicos sobre como o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE oculta diferentes itens de interface do usuário.  
  
|Item de interface do usuário|Descrição|  
|-------------|-----------------|  
|Menus e barras de ferramentas|O pacote de controle de origem deve definir os estados iniciais de visibilidade de menu e barra de ferramentas para a ID do pacote do controle de origem no [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) seção do arquivo. VSCT. Isso permite que o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE para definir o estado dos itens de menu apropriadamente sem carregar o VSPackage e chamar uma implementação de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>método.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>|  
|Janelas de ferramenta|O controle de origem VSPackage oculta quaisquer janelas de ferramenta que ela possui quando ela se torna inativo.|  
|Páginas de opções de VSPackage específico de controle de origem|A chave do registro HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts permite que um VSPackage defina os contextos em que ele requer que suas páginas de opções a serem exibidos. Uma entrada de registro sob essa chave precisa ser criada usando o serviço de ID (SID) do serviço de controle de origem e atribuindo um valor DWORD de 1. Sempre que ocorre um evento de interface do usuário em um contexto de VSPackage é registrado com o controle de origem, o VSPackage será chamado se ele está ativo.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2></xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution></xref:EnvDTE.Constants.vsContextNoSolution>   
 [Gerenciando os VSPackages](../../extensibility/managing-vspackages.md)
