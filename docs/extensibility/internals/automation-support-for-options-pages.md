---
title: "Suporte de automação para páginas de opções | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: 29
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
ms.openlocfilehash: ac6d70927243d5c2281cfa7b460e9172426f7d46
ms.lasthandoff: 02/22/2017

---
# <a name="automation-support-for-options-pages"></a>Suporte de automação para páginas de opções
Os VSPackages pode fornecer personalizado **opções** caixas de diálogo para o **ferramentas** menu (páginas de opções de ferramentas) em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e podem disponibilizá-los para o modelo de automação.  
  
## <a name="tools-options-pages"></a>Páginas de opções de ferramentas  
 Para criar um **opções de ferramentas** página, um VSPackage deve fornecer uma implementação de controle de usuário retornada para o ambiente por meio da implementação do VSPackage o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>método (ou para código gerenciado a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>método).</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>  
  
 É opcional, mas altamente recomendável para permitir acesso a essa nova página por meio do modelo de automação. Você pode fazer isso através das seguintes etapas:  
  
1.  Estender o <xref:EnvDTE._DTE.Properties%2A>objeto por meio da implementação de um objeto derivado de IDispatch.</xref:EnvDTE._DTE.Properties%2A>  
  
2.  Retornam uma implementação do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>método (ou para código gerenciado a <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A>método) para o objeto derivado de IDispatch.</xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
  
3.  Quando um consumidor de automação chama o <xref:EnvDTE._DTE.Properties%2A>método personalizado **opção** página de propriedade, o ambiente usa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>método para obter um personalizado **opções de ferramentas** implementação de automação da página.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> </xref:EnvDTE._DTE.Properties%2A>  
  
4.  O objeto de automação do VSPackage, em seguida, é usado para fornecer a cada <xref:EnvDTE.Property>retornado por <xref:EnvDTE._DTE.Properties%2A>.</xref:EnvDTE._DTE.Properties%2A> </xref:EnvDTE.Property>  
  
 Para um exemplo de implementação de uma página de opções de ferramentas personalizada, consulte [VSSDK exemplos](../../misc/vssdk-samples.md).  
  
## <a name="see-also"></a>Consulte também  
 [Expondo objetos do projeto](../../extensibility/internals/exposing-project-objects.md)
