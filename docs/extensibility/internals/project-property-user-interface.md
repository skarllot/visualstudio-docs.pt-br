---
title: "Interface de usuário de propriedades do projeto | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
caps.latest.revision: 16
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: b344731061053abb208225a0480408ebbe682050
ms.lasthandoff: 02/22/2017

---
# <a name="project-property-user-interface"></a>Interface de usuário de propriedades do projeto
Um subtipo de projeto pode utilizar os itens no projeto **páginas de propriedade** caixa de diálogo como eles são fornecidos pelo projeto base, ocultar ou fazer controles somente leitura e páginas inteiras como fornecidos ou adicionar páginas de subtipo específico de projeto para o **páginas de propriedade** caixa de diálogo.  
  
## <a name="extending-the-project-property-dialog-box"></a>Estendendo a caixa de diálogo de propriedades do projeto  
 Um subtipo de projeto implementa extensores de automação e procurar objetos de configuração do projeto. Esses extensores implementam o <xref:EnvDTE.IFilterProperties>interface fazer determinadas propriedades ocultos ou somente leitura.</xref:EnvDTE.IFilterProperties> O **páginas de propriedade** caixa de diálogo do projeto base, implementado pelo projeto base, respeita a filtragem é realizada pelos extensores de automação.  
  
 O processo de estender uma **propriedades de projeto** caixa de diálogo é apresentada abaixo:  
  
-   O projeto base recupera os Extensores do subtipo do projeto Implementando o <xref:EnvDTE80.IInternalExtenderProvider>interface.</xref:EnvDTE80.IInternalExtenderProvider> A procura, automação de projeto e projeto procurar objetos de configuração do projeto base todos os implementam essa interface.  
  
-   A implementação de <xref:EnvDTE80.IInternalExtenderProvider>para delegar o objeto de navegação do projeto e o objeto de automação do projeto para o <xref:EnvDTE80.IInternalExtenderProvider>implementação do agregador de subtipo de projeto (ou seja, eles `QueryInterface` para <xref:EnvDTE80.IInternalExtenderProvider>no <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>objeto de projeto).</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> </xref:EnvDTE80.IInternalExtenderProvider> </xref:EnvDTE80.IInternalExtenderProvider> </xref:EnvDTE80.IInternalExtenderProvider>  
  
-   O objeto de procura de configuração de projeto base também implementa <xref:EnvDTE80.IInternalExtenderProvider>para conectar diretamente no extensor de automação do objeto de configuração do projeto subtipo.</xref:EnvDTE80.IInternalExtenderProvider> Sua implementação delega para o <xref:EnvDTE80.IInternalExtenderProvider>interface implementada pelo agregador de subtipo do projeto.</xref:EnvDTE80.IInternalExtenderProvider>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implementado pelo objeto de procura de configuração de projeto, retorna o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>objeto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, também implementado pelo objeto de procura de configuração de projeto, retorna o <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>objeto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>  
  
-   Um subtipo de projeto pode determinar as CATIDs apropriados para os diversos objetos extensíveis do projeto base em tempo de execução, recuperando o seguinte <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>valores:</xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
 Para determinar as CATIDs do escopo do projeto, o subtipo de projeto recupera as propriedades acima para <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>do `VSITEMID``typedef`.</xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT> Um subtipo de projeto também pode querer controlar quais **páginas de propriedade** páginas da caixa de diálogo são exibidas para o projeto, configuração dependente e independentes de configuração. Alguns subtipos de projeto podem ser necessário remover as páginas internas e adicionar a páginas específicas do subtipo de projeto. Para permitir isso, o cliente gerenciado projeto chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>método para as seguintes propriedades:</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>  
  
-   `VSHPROPID_PropertyPagesCLSIDList`– uma lista delimitada por ponto e vírgula de CLSIDs de páginas de propriedades de configuração independente.  
  
-   `VSHPROPID_CfgPropertyPagesCLSIDList —`uma lista delimitada por ponto e vírgula de CLSIDs de páginas de propriedades de configuração dependente.  
  
 Porque o projeto subtipo agregados a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>do objeto, ele pode substituir a definição dessas propriedades para controlar quais **páginas de propriedade** são exibidas caixas de diálogo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> O subtipo de projeto pode recuperar essas propriedades do projeto base interno e, em seguida, adicionar ou remover CLSIDs conforme necessário.  
  
 Novas páginas de propriedade adicionadas por um subtipo de projeto são entregues a um objeto de procura de configuração de projeto da implementação do projeto base. Esse objeto de procura de configuração de projeto dá suporte a extensores de automação. Para obter mais informações sobre AutomationExtenders, consulte [implementando e extensores de automação usando](http://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). As páginas de propriedades implementadas pela chamada de subtipo do projeto <xref:EnvDTE.Project.Extender%2A>para recuperar seu próprio objeto de procura de configuração subtipo de projeto que estende o objeto de procura de configuração do projeto base.</xref:EnvDTE.Project.Extender%2A>  
  
## <a name="see-also"></a>Consulte também  
 <xref:EnvDTE.IFilterProperties></xref:EnvDTE.IFilterProperties>   
 [Caixa de diálogo páginas de propriedades](http://msdn.microsoft.com/en-us/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)
