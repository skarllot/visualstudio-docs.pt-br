---
title: "Visão geral de cor e fonte | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: 22
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
ms.openlocfilehash: 212e6290620b4c55a11ac3f7e20b3942b9b80545
ms.lasthandoff: 02/22/2017

---
# <a name="font-and-color-overview"></a>Visão geral de cor e fonte
Este tópico discute as configurações de fonte e cor do texto no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE). Ele também apresenta os conceitos de categorias e exibir itens e descreve como o editor de núcleo e VSPackages usam atributos de texto.  
  
## <a name="the-fonts-and-colors-property-page"></a>A página de propriedades de cores e fontes  
 Você pode gerenciar os atributos do texto exibido no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o ambiente de desenvolvimento integrado (IDE) por meio de **fontes e cores** página de propriedades. Para localizar o **fontes e cores** página de propriedade, no **ferramentas** menu, clique em **opções**. Expanda **ambiente**e, em seguida, clique em **fontes e cores**.  
  
## <a name="categories-and-display-items"></a>Categorias e itens de exibição  
 Fontes e cores são organizadas em **categorias** e **itens de exibição**.  
  
-   A **categoria** é um contêiner lógico ou funcional para um número de **itens de exibição**.  
  
     Uma lista de **categorias** está no **Mostrar configurações de** caixa suspensa do **fontes e cores** página de propriedades.  
  
-   A **exibir o Item** é uma entidade de texto bem definido, como um comentário, uma cadeia de caracteres ou uma estrutura de controle que deve ser colorido quando exibidos.  
  
 Cada **exibir o Item** exclusivamente é definido dentro do **categoria** que o contém. Consequentemente, mais de um **categoria** pode ter um **exibir o Item** com o mesmo nome.  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>Controle de VSPackage fontes e cores  
 O [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] permite que os VSPackages para:  
  
-   Definir a fonte e cor **categorias**.  
  
-   Especifique as fontes e cores usadas para apresentar **itens de exibição**.  
  
-   Interagir com o **fontes e cores** página de propriedades.  
  
-   Agregar vários **categorias** em grupos.  
  
-   Manter as alterações feitas nas configurações padrão.  
  
 Há duas maneiras de interagir com as seleções de fonte e cor dentro do [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)].  
  
-   Uma maneira é conhecida como *coloração de sintaxe*. Ele é usado por um VSPackage que personaliza existente [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor implementar um serviço de linguagem e criar uma fonte de editor.  
  
     Apenas uma **categoria** oferece suporte a esse mecanismo, ou seja, o **Editor de texto**.  
  
-   Uma alternativa mais geral oferece suporte a todos os outros **categorias** e componentes de interface do usuário que não seja o editor de código-fonte ao exibir texto. Para obter mais informações, consulte <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
  
## <a name="core-editor-text-settings"></a>Configurações de texto do Editor de núcleo  
 Configurações de fonte e cor para o editor de núcleo de um objeto de serviço de linguagem são governadas pelo **texto EditorCategory** encontrado no **Mostrar configurações de** caixa suspensa do **fontes e cores** página de propriedades.  
  
 Ao trabalhar com editores, você deve usar a fonte especializada e o mecanismo de controle de cor que fornece o serviço de linguagem para controlar e estender o **Editor de texto** configurações. O mecanismo é conhecido como *coloração de sintaxe* e fornece:  
  
-   Uma técnica simplificada para gerenciar as fontes e cores de itens de exibição.  
  
     Para obter mais informações, consulte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
-   Um mecanismo de colorização bem definido e otimizada.  
  
     Para obter mais informações, consulte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>  
  
-   A capacidade de usar itens de exibição interna do **EditorCategory texto** e estendê-las.  
  
     Para obter mais informações, consulte [como: Use interno pode ser colorido itens](../extensibility/internals/how-to-use-built-in-colorable-items.md) e [itens pode ser colorido personalizados](../extensibility/internals/custom-colorable-items.md).  
  
-   Persistência automática do atual estado de ambas as internas e personalizada exibir itens com o **Editor de texto** categoria.  
  
 Para obter mais informações sobre a sintaxe de cores consulte [coloração de sintaxe em um serviço de linguagem herdado](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces herdadas no Editor](../extensibility/legacy-interfaces-in-the-editor.md)   
 [Sintaxe de cores em um serviço de linguagem herdado](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
