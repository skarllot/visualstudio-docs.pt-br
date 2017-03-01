---
title: "Como: dar suporte a estrutura de tópicos em um serviço de linguagem herdado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
caps.latest.revision: 17
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
ms.openlocfilehash: 209d9cf7893ab96b3d00b02c701d8f7db4262be8
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Como: dar suporte a estrutura de tópicos em um serviço de linguagem herdado
Estrutura de tópicos é usada para expandir ou recolher as regiões diferentes de texto. A forma de estrutura de tópicos é usada pode ser definido diferente por diferentes idiomas. Para obter mais informações, consulte [estrutura de tópicos](../../ide/outlining.md).  
  
 Serviços de linguagem herdada são implementados como parte de um VSPackage, mas a maneira mais recente para implementar recursos de serviço de linguagem é usar extensões MEF. Para obter mais informações sobre a nova maneira de implementar a estrutura de tópicos, consulte [passo a passo: estrutura de tópicos](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  É recomendável que você comece a usar o novo editor de API assim que possível. Isso irá melhorar o desempenho do seu serviço de linguagem e lhe permitem tirar proveito dos novos recursos do editor.  
  
 O exemplo a seguir demonstra como para oferecer suporte a esse comando para o serviço de linguagem.  
  
### <a name="to-support-outlining"></a>Para oferecer suporte a estrutura de tópicos  
  
1.  Implementar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage>em seu objeto de serviço de linguagem.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage>  
  
2.  Chamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>no objeto de sessão de estrutura de tópicos atual para adicionar novas regiões de estrutura de tópicos.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>  
  
## <a name="robust-programming"></a>Programação robusta  
 Quando um usuário seleciona **recolher para definições** sobre o **estrutura de tópicos** menu, o IDE chama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A>no seu serviço de linguagem.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A>  
  
 Quando esse método é chamado, o IDE passa um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>ponteiro (um ponteiro para um buffer de texto) e um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>(um ponteiro para a sessão atual de estrutura de tópicos).</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>  
  
 Você pode chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>método para várias regiões de estrutura de tópicos, especificando essas regiões no `rgOutlnReg` parâmetro.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> O `rgOutlnReg` parâmetro é um <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion>estrutura.</xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> Esse processo permite que você especifique diferentes características da região oculta, como se uma determinada região está expandida ou recolhida.  
  
> [!NOTE]
>  Tenha cuidado ao ocultar caracteres de nova linha. Texto oculto deve estender desde o início da primeira linha para o último caractere da última linha em uma seção, deixando o caractere de nova linha final visíveis.  
  
## <a name="see-also"></a>Consulte também  
 [Como: fornecer suporte a texto oculto em um serviço de linguagem herdado](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [Como: fornecer suporte expandido de estrutura de tópicos em um serviço de linguagem herdado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
