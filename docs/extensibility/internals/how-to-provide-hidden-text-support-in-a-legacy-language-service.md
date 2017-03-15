---
title: "Como: fornecer suporte a texto oculto em um serviço de linguagem herdado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
caps.latest.revision: 21
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
ms.openlocfilehash: a607f1a29dd1d929d6be598c353b7dce631d840a
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Como: fornecer suporte a texto oculto em um serviço de linguagem herdado
Você pode criar regiões de texto oculto além das regiões de estrutura de tópicos. Texto oculto regiões podem ser controlado pelo cliente ou controlada pelo editor e são usados para ocultar uma região de texto completamente. O editor exibe uma região oculta como linhas horizontais. Um exemplo disso é o modo de exibição somente Script no editor de HTML.  
  
## <a name="procedure"></a>Procedimento  
  
#### <a name="to-implement-a-hidden-text-region"></a>Para implementar uma região de texto oculto  
  
1.  Chamar `QueryService` para <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.</xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     Isso retorna um ponteiro para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>  
  
2.  Chamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, passando um ponteiro para um buffer de texto especificado.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> Isso determina se o texto oculto já existe uma sessão para o buffer.  
  
3.  Se já existir, você não precisa criar um e um ponteiro para existente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>objeto é retornado.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Use esse ponteiro para enumerar e criar regiões de texto oculto. Caso contrário, chame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>para criar uma sessão de texto oculto para o buffer.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>  
  
     Um ponteiro para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>objeto é retornado.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>  
  
    > [!NOTE]
    >  Quando você chama `CreateHiddenTextSession`, você pode especificar um cliente texto oculto (ou seja, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>).</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> O cliente do texto oculto notifica você quando texto oculto ou estrutura de tópicos está expandida ou recolhida pelo usuário.  
  
4.  Chamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>Adicionar um ou mais novo delinear regiões ao mesmo tempo, especifique as seguintes informações no `reHidReg` (<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>) parâmetro:</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>  
  
    1.  Especifique um valor de `hrtConcealed` no `iType` membro o <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>estrutura para indicar que você está criando uma região oculta, em vez de uma região de estrutura de tópicos.</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>  
  
        > [!NOTE]
        >  Quando escondidos regiões estão ocultas, o editor exibe automaticamente linhas ao redor das regiões ocultas para indicar sua presença.  
  
    2.  Especifique se a região é controlado pelo cliente ou editor controlada no `dwBehavior` membros o <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>estrutura.</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Sua implementação de estrutura de tópicos inteligente pode conter uma mistura de contorno de editor e o cliente controlados e regiões de texto oculto.
