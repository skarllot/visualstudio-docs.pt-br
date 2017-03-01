---
title: "Propriedades e métodos estendidos por subtipos de projeto | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
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
ms.openlocfilehash: 38bb86636edeaeda4485b7ebe6c8a6349450343c
ms.lasthandoff: 02/22/2017

---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Propriedades e métodos estendidos por subtipos de projeto
Um subtipo de projeto tem uma grande quantidade de energia para influenciar o comportamento do projeto porque ele é criado como um agregador de um projeto de base. Esta seção resume alguns dos recursos que podem ser aprimorados ou modificados por subtipos de projeto.  
  
## <a name="features-gained-by-aggregation"></a>Recursos obtidos pela agregação  
 A tabela a seguir resume a muitos dos métodos de agregação permite subtipos de projeto substituir em projetos de base.  
  
|Métodos substituídos pela agregação|Subtipo de projeto|  
|---------------------------------------|---------------------|  
|De <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Permite que um subtipo de projeto para<br /><br /> -Altere a legenda e o ícone do nó do projeto.<br />-Substituir completamente o projeto `Browse` objeto.<br />-Controla se o projeto pode ser renomeado.<br />-Controle de ordem de classificação.<br />-Contexto de usuário control para obter ajuda dinâmica.|  
|De <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Permite que um subtipo de projeto controlar quais serviços contextuais são fornecidos para designers e editores.|  
|De <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Permite que um subtipo de projeto para<br /><br /> -Participe de roteamento de comando para comandos do projeto.<br />-Adicionar, remover ou desabilitar comandos do ambiente de projeto e comandos ativos do Gerenciador de soluções.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2></xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Habilita o subtipo de projeto filtrar o que o usuário vê no **Adicionar Novo Item** caixa de diálogo.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory></xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Permite que um subtipo de projeto para<br /><br /> -Determine o gerador de padrão dado uma extensão de arquivo.<br />-Mapear um nome de gerador legível humana para um objeto COM.|  
  
## <a name="properties-used-by-project-subtypes"></a>Propriedades usadas pelo projeto subtipos  
 O sistema de projeto de ambiente e base pode usar as propriedades de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID>e <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2>enumerações detalhadas na tabela a seguir para habilitar um subtipo de projeto controlar vários recursos do sistema de projeto.</xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> </xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID>  
  
|Propriedade VSHPROPID|Subtipo de projeto|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|Permite que um subtipo de projeto controlar o conteúdo de **Adicionar Item** caixa de diálogo. O subtipo de projeto pode fornecer uma nova especificação de diretórios de modelo, adicionar novos tipos de itens, remover itens existentes e reorganizar um subconjunto dos itens do projeto base **Adicionar Item** caixa de diálogo.|  
|`PropertyPagesCLSIDList`|Permite que um subtipo de projeto Adicionar ou remover páginas de propriedades de configuração independente.|  
|`CfgPropertyPagesCLSIDList`|Permite que um subtipo de projeto Adicionar ou remover páginas de propriedades de configuração dependente.|  
|`ExtObjectCATID`|Permite que um subtipo de projeto fornecer um extensor de automação para o projeto ou item objetos Conhecendo o CATID de extensor. Por exemplo, um subtipo de projeto pode fornecer um personalizado `Project.Extender("<subtype>")` objeto.|  
|`BrowseObjectCATID`|Permite que um subtipo de projeto fornecer um extensor de automação para o `Browse` objeto Conhecendo o CATID de extensor. Por exemplo, um subtipo de projeto pode adicionar propriedades extras para o <xref:EnvDTE.Project.Properties%2A>coleção.</xref:EnvDTE.Project.Properties%2A>|  
|`CfgBrowseObjectCATID`|Permite que um subtipo de projeto fornecer um extensor de automação para o objeto de procura de configuração do projeto. Por exemplo, um subtipo de projeto pode adicionar propriedades extras para o <xref:EnvDTE.Configuration.Properties%2A>coleção.</xref:EnvDTE.Configuration.Properties%2A>|  
|`CfgExtObjectCATID`|Permite que um subtipo de projeto fornecer um extensor de automação para o objeto de configuração.|  
|`DefaultPlatformName`|Permite que um subtipo de projeto determinar o nome da plataforma para objetos de configuração do projeto.|  
  
 O projeto básico fornece uma implementação padrão das propriedades acima. O projeto base obtém essas chamando `QueryInterface` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>no subtipo projeto externo, permitindo que o subtipo de projeto substituir a implementação das propriedades.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
## <a name="see-also"></a>Consulte também  
 [Design de subtipos de projeto](../../extensibility/internals/project-subtypes-design.md)
