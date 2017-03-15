---
title: "Fornecem a estrutura de tópicos de suporte em um serviço de linguagem | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
caps.latest.revision: 16
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
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: fc502e4430a49284cffe14386249999d82085f1c
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Como: fornecer suporte expandido de estrutura de tópicos em um serviço de linguagem herdado
Há duas opções para estender o suporte de estrutura de tópicos para sua linguagem, além de oferecer suporte a **recolher para definições de** comando. Você pode adicionar regiões controlada pelo editor e adicionar regiões controlado pelo cliente.  
  
## <a name="adding-editor-controlled-outline-regions"></a>Adicionar regiões controlado de Editor  
 Use essa abordagem para criar uma região de estrutura de tópicos e, em seguida, permitir que o editor controlar se a região é expandida, recolhido e assim por diante. Duas opções para fornecer suporte de estrutura de tópicos, essa opção é menos eficiente. Para esta opção, você deve criar uma nova região de estrutura de tópicos em um intervalo especificado de texto usando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> Depois que essa região é criado, seu comportamento é controlado pelo editor. Use o procedimento a seguir para implementar regiões controlada pelo editor.  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>Para implementar uma região controlada pelo editor de estrutura de tópicos  
  
1.  Chamar `QueryService` para<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager></xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     Isso retorna um ponteiro para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>  
  
2.  Chamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, passando um ponteiro para um buffer de texto especificado.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> Isso retorna um ponteiro para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>objeto para o buffer.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>  
  
3.  Ligar <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>para um ponteiro para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> </xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>  
  
4.  Chamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>Adicionar um ou mais novas regiões de estrutura de tópicos em um momento.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>  
  
     Esse método permite que você especifique o intervalo de texto da estrutura de tópicos, se as regiões de estrutura de tópicos existentes são removidos ou preservados e se a região de estrutura de tópicos está expandida ou recolhida por padrão.  
  
## <a name="adding-client-controlled-outline-regions"></a>Adicionar regiões controlado pelo cliente  
 Usam essa abordagem de estrutura de tópicos de implementar controlado pelo cliente (ou inteligente) como a que é usado pelo [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] serviços de linguagem. Um serviço de linguagem que gerencia sua própria estrutura de tópicos monitora o conteúdo do buffer de texto para destruir antigo regiões de estrutura de tópicos quando eles se torna inválido e criar novas regiões de estrutura de tópicos, conforme necessário.  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>Para implementar uma região de estrutura de tópicos controlado pelo cliente  
  
1.  Chamar `QueryService` para <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.</xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> Isso retorna um ponteiro para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>  
  
2.  Chamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, passando um ponteiro para um buffer de texto especificado.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> Isso determina se o texto oculto já existe uma sessão para o buffer.  
  
3.  Se o texto já existe uma sessão, então você não precisa criar um e um ponteiro para existente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>objeto é retornado.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Use esse ponteiro para enumerar e criar regiões de estrutura de tópicos. Caso contrário, chame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>para criar uma sessão de texto oculto para o buffer.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> Um ponteiro para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>objeto é retornado.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>  
  
    > [!NOTE]
    >  Quando você chama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>, você pode especificar um cliente texto oculto (ou seja, um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>objeto).</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> Esse cliente notifica você quando um texto oculto ou região de estrutura de tópicos está expandido ou recolhido pelo usuário.  
  
4.  Chamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>estrutura) parâmetro: Especifique um valor de <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE>no `iType` membro o <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>estrutura para indicar que você está criando uma região de estrutura de tópicos, em vez de uma região oculta.</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> </xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> Especifique se a região é controlado pelo cliente ou editor controlada no `dwBehavior` membro do <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>estrutura.</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> A implementação de estrutura de tópicos inteligente pode conter uma mistura de editor e o cliente controlados regiões de estrutura de tópicos. Especificar o texto da faixa é exibido quando a região de estrutura de tópicos estiver recolhida, como "…", além de `pszBanner` membro do <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>estrutura.</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Texto da faixa do editor padrão para uma região oculta é "...".
