---
title: "Sintaxe de cores em um serviço de linguagem herdado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
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
ms.openlocfilehash: 0f9e79b7886328680e1ce4dd2054f2baecabdea4
ms.lasthandoff: 02/22/2017

---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Sintaxe de cores em um serviço de linguagem herdado
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]usa um serviço de codificação por cores para identificar elementos da linguagem e exibi-los com as cores especificadas em um editor.  
  
## <a name="colorizer-model"></a>Modelo de colorizador  
 A linguagem serviço implementa a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>interface, que é usada por editores.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> Essa implementação é um objeto separado do serviço de linguagem, conforme mostrado na ilustração a seguir.  
  
 ![Gráfico do colorizador SVC](~/docs/extensibility/internals/media/figlgsvccolorizer.gif "FigLgSvcColorizer")  
Modelo de colorizador simples  
  
> [!NOTE]
>  O serviço de cores de sintaxe é separada da geral [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mecanismo para colorir o texto. Para obter mais informações sobre o geral [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] mecanismo suporte colorir, consulte [usando fontes e cores](../../extensibility/using-fonts-and-colors.md).  
  
 Além de colorizador, o serviço de linguagem pode fornecer itens pode ser coloridos personalizados que são usados pelo editor de anúncios que fornece itens pode ser coloridos personalizados. Você pode fazer isso Implementando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>interface no mesmo objeto que implementa o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> Retorna o número de itens pode ser coloridos personalizados quando o editor chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>método e ela retorna um item pode ser colorido personalizado individual quando chama o editor de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>método.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>  
  
 O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>método retorna um objeto que implementa o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> Se o serviço de linguagem compatível com valores de cor de 24 bits ou alto, implemente o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>interface no mesmo objeto, como o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>  
  
## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Como um VSPackage usa um colorizador de serviço de linguagem  
  
1.  O VSPackage deverá obter o serviço de idioma apropriado, que requer que o serviço de linguagem VSPackage para fazer o seguinte:  
  
    1.  Usar um objeto que implementa o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>interface para obter o texto a ser colorido.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>  
  
         Texto geralmente é exibido usando um objeto que implementa o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>  
  
    2.  Obtenha o serviço de linguagem consultando o provedor de serviço do VSPackage para o GUID do serviço de linguagem. Serviços de linguagem são identificados no registro pela extensão de arquivo.  
  
    3.  Associar o serviço de linguagem com o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>chamando seu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>método.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>  
  
2.  O VSPackage agora pode obter e usar o objeto colorizador da seguinte maneira:  
  
    > [!NOTE]
    >  Não é necessário obter uma linguagem de objetos de colorizador do serviço explicitamente VSPackages que use o editor de núcleo. Assim que uma instância do editor de núcleo obtém um serviço de idioma apropriado, ele executa todas as tarefas de colorização mostradas aqui.  
  
    1.  Obter o objeto de colorizador do serviço de linguagem, que implementa o `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer`, e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>interfaces, chamando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>método no serviço de linguagem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>objeto.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>  
  
    2.  Chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>método para obter as informações de colorizador para um determinado intervalo de texto.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>  
  
         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>Retorna uma matriz de valores, um para cada caractere na extensão de texto sendo colorido.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Os valores são índices em uma lista de itens pode ser colorido que é a lista de item pode ser colorido padrão mantida pelo editor de núcleo ou uma lista de item personalizado que pode ser colorido mantido pelo serviço de linguagem propriamente dito.  
  
    3.  Use as informações de colorização retornadas pelo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>método para exibir o texto selecionado.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>  
  
> [!NOTE]
>  Além de usar um colorizador de serviço de linguagem, um VSPackage também pode usar o uso geral [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] colorir o mecanismo de texto. Para obter mais informações sobre esse mecanismo, consulte [usando fontes e cores](../../extensibility/using-fonts-and-colors.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Implementando a coloração de sintaxe](../../extensibility/internals/implementing-syntax-coloring.md)  
 Discute como um editor acessa um serviço de linguagem coloração de sintaxe e que o serviço de linguagem deve implementar para oferecer suporte a sintaxe de cores.  
  
 [Como: usar itens pode ser coloridos internos](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 Demonstra como usar itens pode ser coloridos internos do serviço de linguagem.  
  
 [Itens pode ser coloridos personalizados](../../extensibility/internals/custom-colorable-items.md)  
 Discute como implementar itens pode ser coloridos personalizados.  
  
## <a name="see-also"></a>Consulte também  
 [Usando fontes e cores](../../extensibility/using-fonts-and-colors.md)
