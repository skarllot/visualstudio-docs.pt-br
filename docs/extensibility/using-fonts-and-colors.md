---
title: Usando fontes e cores | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: 27
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
ms.openlocfilehash: 54012aa1db8612f17ec698a9a7cd0d46dcf3147f
ms.lasthandoff: 02/22/2017

---
# <a name="using-fonts-and-colors"></a>Usando fontes e cores
O [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fornece suporte ao uso de fontes e cores para exibir texto.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral de cor e fonte](../extensibility/font-and-color-overview.md)  
 Descreve as configurações de fonte e cor do texto no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE). Também apresenta os conceitos de categorias e exibir itens e descreve como o editor de núcleo e VSPackages usam atributos de texto.  
  
 [Obtendo informações de cor de colorização de texto e fonte](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 Fornece diretrizes para implementar a colorização de texto em VSPackages gerenciar **categorias** que **Editor de texto**.  
  
 [Acessando configurações de cor e fonte armazenado](../extensibility/accessing-stored-font-and-color-settings.md)  
 Explica como atual fonte e cor configurações podem ser armazenadas, recuperadas e aplicadas.  
  
 [Implementação de categorias personalizadas e exibir itens](../extensibility/implementing-custom-categories-and-display-items.md)  
 Descreve as etapas básicas que uma janela pode criar e usar seu próprio de **exibir itens** e **categorias** para oferecer suporte à exibição de texto.  
  
 Essa abordagem exige um VSPackage implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>interface e das interfaces relacionadas.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
  
 [Como: acessar o esquema de cores e fontes internas](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 Descreve como definir e registrar uma categoria, usando cores e fontes internas e iniciar o uso do sistema forneceu fontes e cores.  
  
## <a name="reference"></a>Referência  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 Fornece uma instância do `IVsFontAndColorDefaults` ou o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>interface que corresponde a um determinado item listado no **Mostrar configurações para** lista no **fontes e cores** página do **opções** caixa de diálogo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 Permite que um VSPackage suportar o IDE **fontes e cores** página definindo padrão fontes e cores para uma janela ou um componente de interface do usuário.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Fornece um mecanismo pelo qual um VSPackage que fornece suporte de fonte e cor pode especificar um grupo de Item de exibição - uma categoria super que representa a união de duas ou mais categorias.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Permite que um VSPackage recuperar dados de fontes e cores, ou salvá-lo no registro.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Notifica os VSPackages que estão usando fontes e cores informações sobre alterações nas configurações de fonte e cor.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 Fornece ferramentas para trabalhar com os dados de entrada e saídos que são usados pelos métodos das [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **fontes e cores** mecanismo.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Controla o cache de configurações de fonte e cor.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Desenvolvendo um serviço de linguagem herdado](../extensibility/internals/developing-a-legacy-language-service.md)  
 Discute como os VSPackages pode usar os serviços de linguagem para personalizar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor.  
  
 [Cores de sintaxe no editores personalizados](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries como o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor usa serviços de linguagem para implementar a coloração de sintaxe.  
  
 [Estendendo a outras partes do Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Explica como usar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] serviços para criar elementos de interface do usuário que correspondem ao restante da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].
