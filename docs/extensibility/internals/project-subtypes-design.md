---
title: Design de subtipos de projeto | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
caps.latest.revision: 32
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
ms.openlocfilehash: 57be337a2fd1261d79ec4d5525da48d8afb90a23
ms.lasthandoff: 02/22/2017

---
# <a name="project-subtypes-design"></a>Design de subtipos de projeto
Subtipos de projeto permitem que os VSPackages estender projetos baseados em Microsoft Build Engine (MSBuild). O uso de agregação lhe permite reutilizar a maior parte do sistema de projeto principal gerenciado implementado em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ainda ainda personalizar o comportamento de um determinado cenário.  
  
 Os tópicos a seguir detalham o design básico e a implementação de subtipos de projeto:  
  
-   Design de subtipo do projeto.  
  
-   Agregação de vários nível.  
  
-   Suporte a Interfaces.  
  
## <a name="project-subtype-design"></a>Design de subtipo de projeto  
 A inicialização de um subtipo de projeto é obtida ao agregar principal <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>objetos.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> </xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Essa agregação permite um subtipo de projeto substituir ou aumentar a maioria dos recursos do projeto base. Subtipos de projeto obtém a primeira oportunidade para lidar com propriedades usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, comandos usando <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>e o item de projeto gerenciamento usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> </xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Também podem estender os subtipos de projeto:  
  
-   Objetos de configuração do projeto.  
  
-   Objetos dependentes de configuração.  
  
-   Configuração independente procurar objetos.  
  
-   Objetos de automação do projeto.  
  
-   Coleções de propriedade de automação de projetos.  
  
 Para obter mais informações sobre extensibilidade por subtipos de projeto, consulte [propriedades e métodos estendida pelo projeto subtipos](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).  
  
##### <a name="policy-files"></a>Arquivos de política  
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente fornece um exemplo de estender o sistema de projeto básico com um subtipo de projeto em sua implementação de arquivos de política. Um arquivo de política permite a modelagem do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente por meio do gerenciamento de recursos que incluem o Gerenciador de soluções, **Adicionar projeto** caixa de diálogo, **Adicionar Novo Item** caixa de diálogo e o **propriedades** caixa de diálogo. O subtipo de política substitui e aprimora esses recursos por meio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>, `IOleCommandTarget` e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>implementações.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>  
  
##### <a name="aggregation-mechanism"></a>Mecanismo de agregação  
 Mecanismo de agregação de subtipo de projeto do ambiente oferece suporte a vários níveis de agregação, permitindo assim que um subtipo avançado ser implementada por mais de um projeto do tipo flavoring. Além disso, os objetos de suporte de um projeto de subtipo, como <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>, foram projetados para permitir vários níveis de camadas.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> Para manter as restrições de COM e COM regras de agregação, subtipos de projeto e projetos base precisam ser programados de forma cooperativa para permitir o subtipo interno ou o projeto base participem adequadamente em chamadas de método de delegação e gerenciar contagens de referência. Ou seja, o projeto prestes a ser agregado precisa ser programado para dar suporte a agregação.  
  
 A ilustração a seguir mostra uma representação esquemática de uma agregação de subtipo de projeto de vários níveis.  
  
 ![Gráfico de projectflavor do vários níveis de Studio Visual](../../extensibility/internals/media/vs_multilevelprojectflavor.gif "VS_MultilevelProjectFlavor")  
Subtipo de vários níveis de projeto  
  
 Uma agregação de subtipo de vários níveis de projeto consiste em três níveis, um projeto base, que é agregadas por um subtipo de projeto e agregadas por um subtipo de projeto avançadas. A figura se concentra em algumas das interfaces de suporte que são fornecidas como parte do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] arquitetura subtipo de projeto.  
  
##### <a name="deployment-mechanisms"></a>Mecanismos de implantação  
 Entre os muitos do sistema de projeto base funcionalidades aprimoradas por um subtipo de projeto são mecanismos de implantação. Um subtipo de projeto influencia mecanismos de implantação implementando interfaces de configuração (como <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>) que são recuperados pela chamada QueryInterface em <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> </xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> </xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> Em um cenário onde o subtipo de projeto e o subtipo de projeto avançado adicionam implementações de configuração diferentes, o projeto base chama `QueryInterface` sobre o subtipo de projeto avançado `IUnknown`. Se o subtipo de projeto interno contém a implementação de configuração que está solicitando o projeto de base para os representantes de subtipo de projeto avançadas para a implementação oferecida pelo subtipo de projeto interno. Como um mecanismo para manter o estado do nível de uma agregação para outro, todos os níveis de subtipos de projeto implementam <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>manter a compilação não relacionados dados XML em arquivos de projeto.</xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> Para obter mais informações, consulte [persistência de dados no arquivo de projeto MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider>é implementado como um mecanismo para recuperar os extensores de automação de subtipos de projeto.</xref:EnvDTE80.IInternalExtenderProvider>  
  
 A ilustração a seguir se concentra na implementação do extensor de automação, o objeto de procura de configuração de projeto em particular, usado pelo subtipos de projeto para estender o sistema de base do projeto.  
  
 ![Gráfico de extensor de automático de tipo de projeto do VS](../../extensibility/internals/media/vs_projectflavorautoextender.gif "VS_ProjectFlavorAutoExtender")  
Extensor de automação de subtipo do projeto.  
  
 Subtipos de projeto podem ampliar ainda mais o sistema de projeto base estendendo o modelo de objeto de automação. Eles são definidos como parte do objeto de automação DTE e são usados para estender o objeto de projeto, o `ProjectItem` objeto e o `Configuration` objeto. Para obter mais informações, consulte [estendendo o modelo de objeto do projeto Base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).  
  
## <a name="multi-level-aggregation"></a>Agregação de vários nível  
 Uma implementação de subtipo de projeto que encapsula um subtipo de projeto de nível inferior precisa ser programado cooperativamente para permitir que o subtipo de projeto interno funcionar corretamente. Inclui uma lista de responsabilidades de programação:  
  
-   O <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>implementação do subtipo do projeto que está encapsulando o subtipo interno deve delegar para o <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>implementação do subtipo do projeto interno para ambas <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A>e <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A>métodos.</xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> </xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>  
  
-   O <xref:EnvDTE80.IInternalExtenderProvider>implementação do subtipo do projeto de wrapper deve delegar para que seu subtipo de projeto interno.</xref:EnvDTE80.IInternalExtenderProvider> Em particular, a implementação de <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A>precisa obter a cadeia de caracteres de nomes de subtipo do projeto interna e, em seguida, concatenar as cadeias de caracteres que deseja adicionar como extensores.</xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A>  
  
-   O <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>implementação de um subtipo de projeto de wrapper deve instanciar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>objeto do seu interna subtipo do projeto e mantê-la como um delegado particular, pois somente do projeto base projeto objeto de configuração diretamente sabe que existe o objeto de configuração de subtipo de projeto de wrapper.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> </xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> O subtipo de projeto externa pode escolher inicialmente interfaces de configuração que deseja manipular diretamente e delegar o restante para implementação do subtipo projeto interna de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>  
  
## <a name="supporting-interfaces"></a>Suporte a Interfaces  
 O projeto base delega chamadas ao suporte a interfaces adicionadas por um subtipo de projeto, para estender a vários aspectos da sua implementação. Isso inclui a extensão de objetos de configuração do projeto e vários objetos de navegador de propriedade. Essas interfaces são recuperadas chamando `QueryInterface` na `punkOuter` (um ponteiro para o `IUnknown`) do agregador de subtipo de projeto externo.  
  
|Interface|Subtipo de projeto|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg></xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Permite que o subtipo de projeto para:<br /><br /> -Forneça uma implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg><br />-Controle a inicialização do depurador, permitindo que o subtipo de projeto fornecer sua própria implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg><br />-Desativar a avaliação da expressão de tempo de design ao manipular adequadamente a `DBGLAUNCH_DesignTimeExprEval` maiusculas em sua implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>|  
|<xref:EnvDTE80.IInternalExtenderProvider></xref:EnvDTE80.IInternalExtenderProvider>|Permite que o subtipo de projeto para:<br /><br /> -Estender o <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>do projeto para adicionar ou remover propriedades independente de configuração do projeto.</xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID><br />-Estender o objeto de automação do projeto (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>) do projeto.</xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID><br /><br /> Valores de propriedade acima são obtidos <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>enumeração.</xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Permite que o subtipo de projeto mapear novamente para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>objeto dado o objeto de configuração do projeto procurar.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject></xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Permite que o subtipo de projeto mapear novamente para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>ou o `VSITEMID` objeto, dado o objeto de configuração do projeto procurar.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment></xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Permite que o subtipo de projeto persistir dados XML estruturado arbitrários para o arquivo de projeto (. vbproj ou. csproj). Esses dados não são visíveis para MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage></xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Permite que o subtipo de projeto para:<br /><br /> -Adicione novas propriedades de MSBuild para ser persistente.<br />-Remova propriedades desnecessárias do MSBuild.<br />-Consultar um valor atual de uma propriedade de MSBuild.<br />-Altere o valor atual de uma propriedade de MSBuild.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID></xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
