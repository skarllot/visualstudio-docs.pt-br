---
title: "Contribuir com o modelo de automação | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: 18
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
ms.openlocfilehash: 07efc534cd169672b9ed21893d502013b4e9b00f
ms.lasthandoff: 02/22/2017

---
# <a name="contributing-to-the-automation-model"></a>Contribuir com o modelo de automação
Visual Studio fornece um conjunto de interfaces de automação para personalizar o ambiente. O modelo de automação é o modelo de objeto que permite aos usuários finais criar suplementos do Visual Studio e extensões.  
  
 Além disso, é apropriado para você, como desenvolvedor de VSPackage, contribuir para o modelo de automação. fazendo isso, você habilitar os usuários finais do seu VSPackage criar suplementos e geralmente fornecem uma experiência de usuário consistente modelo ao usarem o VSPackage em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Para tornar o usuário final experiência consistente, você pode seguir um conjunto de diretrizes de como você cria o VSPackage para que o modelo de automação para o VSPackage segue as ideias em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral do modelo de automação](../../extensibility/internals/automation-model-overview.md)  
 Define o modelo de automação como um grupos de objetos que controlam os principais aspectos do ambiente comum. Esse conjunto de objetos é representado em um diagrama do modelo de automação.  
  
 [Oferecendo automação para VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)  
 Discute as duas maneiras principais fornecem automação para o VSPackage.  
  
 [Expondo objetos do projeto](../../extensibility/internals/exposing-project-objects.md)  
 Fornece instruções passo a passo para a criação de objetos específicos de VSPackage.  
  
 [Projeto de modelagem](../../extensibility/internals/project-modeling.md)  
 Explica os objetos de projeto padrão que são necessários para criar automação para o novo tipo de projeto e ilustra o caminho que segue automação de projetos. Este tópico também fornece listagens de declarações e a implementação de classes.  
  
 [Exposição de eventos](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Fornece instruções passo a passo para a criação de eventos para o seu modelo de automação.  
  
 [Suporte de automação para páginas de opções](../../extensibility/internals/automation-support-for-options-pages.md)  
 Descreve como retornar um objeto de automação para dar suporte a propriedades de um VSPackage personalizado **opções** na caixa de diálogo de **ferramenta** menu estendendo o `DTE.Properties` objeto.  
  
 [Fornece automação de código](../../extensibility/internals/providing-automation-for-code.md)  
 Explica que a criação de um modelo de automação para o seu código não é necessário. No entanto, um link será fornecido neste tópico que fornece informações criteriosas em modelos de código.  
  
 [Como: fornecer automação para Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Explica o que fornece a automação é uma boa ideia sempre que você deseja disponibilizar os objetos de automação em uma janela, e o ambiente já não fornecem um objeto de automação prontos. Discute a automação para janelas de ferramenta e janelas de documento.  
  
 [Usando o modelo de automação](../../extensibility/internals/using-the-automation-model.md)  
 Fornece dois exemplos de código que mostram como um consumidor de automação obtém o projeto inicial objetos de automação.  
  
 [Automação de configuração e objetos SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Fornece informações sobre a automação para opções de configuração e automação para itens selecionados.  
  
## <a name="reference"></a>Referência  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 Fornece um exemplo de código que mostra como um VSPackage participa no modelo de objeto de automação de DTE. Lista de parâmetros, valores de retorno e comentários selecionados.  
  
## <a name="related-sections"></a>Seções relacionadas
