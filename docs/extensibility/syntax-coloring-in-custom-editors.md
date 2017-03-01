---
title: Cores de sintaxe no editores personalizados | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
caps.latest.revision: 12
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
ms.openlocfilehash: 598e24d7ed1472e85af0b2cc794a18fa7cdb36b9
ms.lasthandoff: 02/22/2017

---
# <a name="syntax-coloring-in-custom-editors"></a>Cores de sintaxe no editores personalizados
Editores visuais do SDK de ambiente do Studio, incluindo o editor de núcleo, usam os serviços de linguagem para identificar itens específicos de sintáticos e exibi-los com cores especificadas para exibir um determinado documento.  
  
## <a name="colorization-requirements"></a>Requisitos de colorização  
 Todos os editores de implementação colorizador de um serviço de linguagem devem:  
  
1.  Usar um objeto que implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>para gerenciar o texto a ser colorido e um objeto que implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>para fornecer uma exibição de documento do texto.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>  
  
2.  Obter uma interface para um serviço de idioma específico, consultando o provedor de serviços do VSPackage usando o GUID de identificação do serviço de idiomas.  
  
3.  Chame o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>método do objeto implementando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> Este método associa o serviço de linguagem com o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>implementação VSPackage usa para gerenciar o texto a ser colorido.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>  
  
## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Uso do Editor núcleo de colorizador de um serviço de linguagem  
 Quando um serviço de linguagem com um colorizador é obtido por uma instância do editor de núcleo, a análise e renderização de texto por colorizador de um serviço de linguagem ocorre automaticamente sem a necessidade de intervenção adicional de sua parte.  
  
 O IDE transparente:  
  
-   Chama o colorizador conforme necessário para analisar e analisar texto conforme ele é adicionado ou modificado na implementação de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>  
  
-   Garante que a exibição fornecida pela exibição do documento fornecida pelo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>implementação é atualizada e redesenhada usando as informações retornadas pelo colorizador.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>  
  
## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Uso do Editor não essenciais de colorizador de um serviço de linguagem  
 Instâncias do editor não-core também podem usar o serviço de colorização de sintaxe de um serviço de linguagem, mas eles explicitamente devem recuperar e aplicar colorizador do serviço e redesenhar seus entre exibições de documento.  
  
 Para fazer isso, um editor não essenciais:  
  
1.  Obter objeto de colorizador de um serviço de linguagem (que implementa `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>).</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> O VSPackage faz isso chamando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>método na interface do serviço de linguagem.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>  
  
2.  Chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>método para solicitar que um determinado intervalo de texto ser colorido.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>  
  
     O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>método retorna uma matriz de valores, um para cada letra no texto abrangem sendo colorido.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Ele também identifica o intervalo de texto como um tipo específico de item pode ser colorido, como um comentário, a palavra-chave ou o tipo de dados.  
  
3.  Use as informações de colorização retornadas por <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>para redesenhar e exibir seu texto.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>  
  
> [!NOTE]
>  Além de usar colorizador de um serviço de linguagem, um VSPackage pode optar por usar o mecanismo de coloração de texto para fins gerais do SDK do ambiente Visual Studio. Para obter mais informações sobre esse mecanismo, consulte [usando fontes e cores](../extensibility/using-fonts-and-colors.md).  
  
## <a name="see-also"></a>Consulte também  
 [Sintaxe de cores em um serviço de linguagem herdado](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementando a coloração de sintaxe](../extensibility/internals/implementing-syntax-coloring.md)   
 [Como: usar itens pode ser coloridos internos](../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Itens pode ser coloridos personalizados](../extensibility/internals/custom-colorable-items.md)
