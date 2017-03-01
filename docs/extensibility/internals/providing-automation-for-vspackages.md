---
title: "Oferecendo automação para VSPackages | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
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
ms.openlocfilehash: ca3700d1e26ccd4be1054463e9426b364ba17301
ms.lasthandoff: 02/22/2017

---
# <a name="providing-automation-for-vspackages"></a>Oferecendo automação para VSPackages
Há duas maneiras de fornecer automação para seu VSPackages: Implementando objetos específicos de VSPackage e implementando objetos de automação padrão. Geralmente, eles são usados juntos para estender o modelo de automação do ambiente.  
  
## <a name="vspackage-specific-objects"></a>Objetos específicos de VSPackage  
 Certos locais dentro do modelo de automação exigem que você fornecer objetos de automação que são exclusivos para o VSPackage. Por exemplo, novos projetos exigem objetos distintos que fornece apenas o VSPackage. Os nomes desses objetos são inseridos no registro e obtidos por meio de chamadas para o ambiente `DTE` objeto.  
  
 Objetos específicos de VSPackage também podem ser obtidos quando um consumidor de automação usa o objeto fornecido através da propriedade do objeto de um objeto padrão. Por exemplo, o padrão `Window` objeto possui uma `Object` propriedade, comumente conhecida como o `Windows.Object` propriedade. Quando os consumidores chamam o `Window.Object` em uma janela implementada o VSPackage, novamente você passar um objeto de automação específico de seu próprio projeto.  
  
#### <a name="projects"></a>Projetos  
 Os VSPackages pode estender o modelo de automação para novos tipos de projeto por meio de seus próprios objetos específicos de VSPackage. A principal finalidade de fornecer novos objetos de automação para o VSPackage é diferenciar seu projeto exclusivo objetos de um <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject>ou um <xref:VSLangProj80.VSProject2>objeto.</xref:VSLangProj80.VSProject2> </xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> Essa diferenciação é útil quando você deseja fornecer uma maneira para destacar ou iterar o tipo de projeto, além de outros tipos de projeto, eles devem aparecer lado a lado em uma solução. Para obter mais informações, consulte [expondo objetos do projeto](../../extensibility/internals/exposing-project-objects.md).  
  
#### <a name="events"></a>Eventos  
 A arquitetura de evento do ambiente oferece outro lugar para anexar seus próprios objetos específicos de VSPackage. Por exemplo, ao criar seus próprios objetos de evento exclusivos, você pode estender o modelo de evento do ambiente para projetos. Você talvez queira fornecer seus próprios eventos quando um novo item é adicionado ao tipo de projeto. Para obter mais informações, consulte [eventos expondo](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).  
  
#### <a name="window-objects"></a>Objetos de janela  
 Windows pode devolver um objeto de automação de VSPackage específico para o ambiente quando chamado. Implementar um objeto que é derivado de <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, <xref:EnvDTE.IExtensibleObject>ou `IDispatch` que volta passa propriedades, estendendo o objeto de janela no qual ele está localizado.</xref:EnvDTE.IExtensibleObject> </xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> Por exemplo, você pode usar essa abordagem fornecem automação para um controle colocado em um quadro de janela. A semântica deste objeto e outros objetos que podem estender é sua para design. Para obter mais informações, consulte [como: fornecer automação para Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).  
  
#### <a name="options-pages-on-the-tools-menu"></a>Páginas de opções no menu Ferramentas  
 Você pode criar páginas para estender as ferramentas, o modelo de automação de opções por meio da implementação de páginas e adicionar informações ao registro para criar suas próprias opções. As páginas, em seguida, podem ser chamadas por meio do modelo de objeto do ambiente como quaisquer outras páginas de opções. Se o design do recurso que você está adicionando ao ambiente por meio de VSPackages requer páginas de opções, você deve adicionar o suporte de automação. Para obter mais informações, consulte [suporte de automação para páginas de opções](../../extensibility/internals/automation-support-for-options-pages.md).  
  
## <a name="standard-automation-objects"></a>Objetos de automação padrão  
 Para estender a automação para projetos, você também implementar objetos de automação padrão (derivado de `IDispatch`) que espera ao lado de outros objetos do projeto e implementar propriedades e métodos padrão. Exemplos de objetos padrão os objetos do projeto são inseridos na hierarquia de solução como `Projects`, `Project`, `ProjectItem`, e `ProjectItems`. Cada novo tipo de projeto deve implementar esses objetos (e possivelmente outros aqueles dependendo da semântica do projeto).  
  
 De certa forma, esses objetos fornecem oposta aproveitar os objetos de projeto VSPackage específicos. Os objetos de automação padrão permitem que seu projeto para ser usado de forma generalizada como qualquer outro projeto os mesmos objetos de suporte. Portanto, um suplemento que é escrito em geral `Project` e `ProjectItem` objetos podem funcionar em relação a projetos de qualquer tipo. Para obter mais informações, consulte [projeto de modelagem](../../extensibility/internals/project-modeling.md).
