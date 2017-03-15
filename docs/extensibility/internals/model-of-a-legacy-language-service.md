---
title: "Modelo de um serviço de linguagem herdado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
caps.latest.revision: 20
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
ms.openlocfilehash: 154d7ea22878c1834b97b98b88220816581139d0
ms.lasthandoff: 02/22/2017

---
# <a name="model-of-a-legacy-language-service"></a>Modelo de um serviço de linguagem herdado
Um serviço de linguagem define os elementos e recursos para um idioma específico e é usado para fornecer o editor com informações específicas para esse idioma. Por exemplo, o editor precisa saber os elementos e as palavras-chave da linguagem para oferecer suporte a coloração de sintaxe.  
  
 O serviço de linguagem trabalha junto com o buffer de texto gerenciado pelo editor e o modo de exibição que contém o editor. O Microsoft IntelliSense **informações rápidas** opção é um exemplo de um recurso fornecido por um serviço de linguagem.  
  
## <a name="a-minimal-language-service"></a>Um serviço de linguagem mínima  
 O serviço de linguagem mais básico contém os dois objetos a seguir:  
  
-   O *serviço de linguagem* implementa o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Um serviço de linguagem tem informações sobre a linguagem, incluindo seu nome, extensões de nome de arquivo, o Gerenciador de janela de código e colorizador.  
  
-   O *colorizador* implementa o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>  
  
 O desenho conceitual a seguir mostra um modelo de um serviço de linguagem básicos.  
  
 ![Gráfico de modelo de serviço de linguagem](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Modelo de serviço de linguagem básicos  
  
 Os hosts de janela de documento o *exibição do documento* do editor, neste caso o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editor básicos. O modo de exibição de documento e o buffer de texto são de propriedade pelo editor. Esses objetos funcionam com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] através de uma janela de documento especializadas chamado um *janela código*. A janela de código está contida em uma <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>objeto que é criado e controlado pelo IDE.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>  
  
 Quando um arquivo com uma determinada extensão é carregado, o editor localiza o serviço de idioma associado com a extensão e passa para ele a janela de código chamando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>método.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> O serviço de linguagem retorna um *Gerenciador de janela de código*, que implementa o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>  
  
 A tabela a seguir fornece uma visão geral dos objetos no modelo.  
  
|Componente|Objeto|Função|  
|---------------|------------|--------------|  
|Buffer de texto|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer></xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>|Um fluxo de texto Unicode de leitura/gravação. É possível usar outras codificações de texto.|  
|Janela de código|<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow></xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>|Uma janela de documento que contém um ou mais modos de exibição de texto. Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] está no modo de interface de documentos múltiplos (MDI), a janela de código é um filho MDI.|  
|Exibição de texto|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView></xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>|Uma janela que permite ao usuário navegar e exibir o texto usando o teclado e mouse. Uma exibição de texto aparece para o usuário como um editor. Você pode usar modos de exibição de texto em janelas do editor comum, a janela de saída e a janela imediata. Além disso, você pode configurar um ou mais modos de exibição de texto dentro de uma janela de código.|  
|Gerenciador de texto|Gerenciado pelo <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>serviço, do qual você obtém um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>ponteiro</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> </xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>|Um componente que mantém informações comuns compartilhadas por todos os componentes descritos anteriormente.|  
|Serviço de linguagem|Implementação dependente; implementa<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo></xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>|Um objeto que fornece o editor com informações específicas de idioma como realce de sintaxe, conclusão de instrução e correspondência de chaves.|  
  
## <a name="see-also"></a>Consulte também  
 [Dados de documentos e visualização de documentos em editores personalizados](../../extensibility/document-data-and-document-view-in-custom-editors.md)
