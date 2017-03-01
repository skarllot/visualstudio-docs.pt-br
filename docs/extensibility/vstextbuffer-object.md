---
title: Objeto VSTextBuffer | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: 9
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
ms.openlocfilehash: 728f4b2153f89a15ca34753667df44371511e6b6
ms.lasthandoff: 02/22/2017

---
# <a name="vstextbuffer-object"></a>Objeto VSTextBuffer
O objeto de buffer de texto representa um fluxo de texto em Unicode, que é geralmente associado um arquivo. Um <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>objeto pode ser usado fora do contexto do editor principal, como no caso de um assistente.</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>  
  
 A tabela a seguir mostra as interfaces de `VSTextBuffer`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IOleCommandTarget](http://msdn.microsoft.com/library/windows/desktop/ms683797)|Interface OLE padrão. Usado principalmente para tratamento no buffer de desfazer/refazer.|  
|[IPersistFile](http://msdn.microsoft.com/library/windows/desktop/ms687223)|Interface OLE padrão.|  
|[IPersistStream](http://msdn.microsoft.com/library/windows/desktop/ms690091)|Interface OLE padrão.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permite a criação de ações de compostos (ou seja, ações que são agrupadas em uma unidade única de desfazer/refazer).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Permite a persistência de dados de documentos gerenciados pelo buffer de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Fornece serviços básicos; usado por muitos clientes.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Usado para pesquisar um buffer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Fornece leitura e gravação a recursos usando coordenadas bidimensionais. Herda de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Fornece leitura e gravação a recursos usando coordenadas unidimensionais. Herda de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Rápido e fornece acesso sequencial orientada por fluxo ao texto no buffer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData></xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Fornece acesso a uma coleção genérica de propriedades. A propriedade mais importante é o nome ou o moniker do buffer. Você pode armazenar seus próprios dados aleatórios no buffer com essa interface criando um GUID e usá-lo como uma chave.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer></xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Oferece suporte a pontos de conexão para eventos.|  
  
## <a name="remarks"></a>Comentários  
 O `VSTextBuffer` costuma ser encontrado por um `QueryInterface` chamar `IVsTextBuffer`. Para obter mais informações, consulte [Buffer de texto](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView></xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Edição de figuras](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)
