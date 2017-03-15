---
title: Estrutura de VSPackage (VSPackage de controle de origem) | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: 26
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
ms.openlocfilehash: 90bc54156abaf98658f01d6551716c845187c794
ms.lasthandoff: 02/22/2017

---
# <a name="vspackage-structure-source-control-vspackage"></a>Estrutura de VSPackage (VSPackage de controle de origem)
O SDK de pacote de controle de origem fornece diretrizes para criar um VSPackage que permitem que um implementador de controle de origem para integrar sua funcionalidade de controle de origem com o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente. Um VSPackage é um componente COM que normalmente é carregado sob demanda, o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE), de acordo com os serviços que são publicados pelo pacote em suas entradas do registro. Cada VSPackage deve implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> Um VSPackage geralmente consome serviços oferecidos pelo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE e proffers alguns serviços própria.  
  
 Um VSPackage declara seus itens de menu e estabelece um estado do item padrão por meio do arquivo. VSCT. O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE exibe os itens de menu nesse estado até que o VSPackage é carregado. Consequentemente, a implementação do VSPackage do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>método é chamado para habilitar ou desabilitar itens de menu.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>  
  
## <a name="source-control-package-characteristics"></a>Características do pacote de controle de origem  
 Um controle de origem VSPackage está profundamente integrado ao [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 A semântica de VSPackage incluem:  
  
-   Interface a ser implementada em virtude sendo um VSPackage (o `IVsPackage` interface)  
  
-   Implementação de comandos da interface do usuário (arquivo. VSCT e a implementação do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interface)</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>  
  
-   Registro do VSPackage com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 O controle de origem VSPackage deve se comunicar com esses outros [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entidades:  
  
-   Projetos  
  
-   Editores  
  
-   SoluçõesD;  
  
-   Windows  
  
-   A tabela de documento em execução  
  
### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Ambiente de serviços do Visual Studio que podem ser consumidos  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell></xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell></xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution></xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution></xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 Serviço SVsRegisterScciProvider  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave></xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments></xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager></xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### <a name="vsip-interfaces-implemented-and-called"></a>VSIP Interfaces implementadas e chamada  
 Um pacote de controle de origem é um VSPackage e, portanto, ele pode interagir diretamente com outros VSPackages são registrados com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. A fim de fornecer toda a funcionalidade de controle do código-fonte, um controle de fonte VSPackage pode lidar com interfaces fornecidas por projetos ou o shell.  
  
 Cada projeto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>seja reconhecido como um projeto dentro do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> No entanto, essa interface não é especializada suficiente para controle de origem. Projetos que devem estar no controle de origem implementam <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> Essa interface é usada pelo controle de origem VSPackage para consultar um projeto para seu conteúdo e fornecer informações de associação (as informações necessárias para estabelecer uma conexão entre o local do servidor e o local de disco de um projeto sob controle de origem) e glifos.  
  
 O controle de origem VSPackage implementa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, que por sua vez permite que projetos se registrem para controle de origem e recuperar seus glifos status.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
  
 Para obter uma lista completa de interfaces que deve ser considerados um controle da fonte de VSPackage, consulte [serviços relacionados e Interfaces](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).  
  
## <a name="see-also"></a>Consulte também  
 [Elementos de design](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [Interfaces e serviços relacionados](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
