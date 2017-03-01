---
title: 'Como: implementar o gerenciamento de desfazer | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: 11
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
ms.openlocfilehash: eb25db65a93858270f338570c2497abbed3c8c49
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-implement-undo-management"></a>Como: implementar o gerenciamento de desfazer
A principal interface usada para o gerenciamento de desfazer é <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>, que é implementado pelo ambiente.</xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> Para dar suporte ao gerenciamento de desfazer, implementar unidades desfazer separado (ou seja, <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>, que pode conter várias etapas individuais.</xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>  
  
 Como você implementa o gerenciamento de desfazer varia dependendo se o editor dá suporte a vários modos de exibição ou não. Os procedimentos para cada implementação são detalhados nas seções a seguir.  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>Casos onde um editor compatível com uma única exibição  
 Nesse cenário, o editor não oferece suporte a vários modos de exibição. Há apenas um editor e um documento, e eles oferecem suporte ao desfazer. Use o procedimento a seguir para implementar o gerenciamento de desfazer.  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>Para dar suporte ao gerenciamento de desfazer para um editor de modo de exibição único  
  
1.  Chamar `QueryInterface` sobre o `IServiceProvider` interface no quadro da janela para `IOleUndoManager`, do objeto de exibição de documento para acessar o Gerenciador de desfazer (`IID_IOLEUndoManager`).  
  
2.  Quando uma exibição é colocada em um quadro de janela, ela recebe um ponteiro de site, que pode usar para chamar `QueryInterface` para `IServiceProvider`.  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>Casos em que um editor dá suporte a vários modos de exibição  
 Se você tiver a separação de documento e exibição, há normalmente uma operação desfazer manager associado com o documento em si. Todas as unidades de desfazer são colocadas no Gerenciador de um Desfazer associado ao objeto de dados do documento.  
  
 Em vez da consulta de modo de exibição para o Gerenciador de desfazer, de que há um para cada modo de exibição, os dados do documento objeto chamadas <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>para instanciar o Gerenciador de desfazer, especificando um identificador de classe de CLSID_OLEUndoManager.</xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> O identificador de classe é definido no arquivo OCUNDOID.h.  
  
 Ao usar <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>para criar sua própria instância do Gerenciador de desfazer, use o procedimento a seguir para conectar o Gerenciador de desfazer no ambiente.</xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>Para conectar o Gerenciador de desfazer no ambiente  
  
1.  Chamar `QueryInterface` no objeto retornado de <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2>para `IID_IOleUndoManager`.</xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> Armazenar o ponteiro para <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>.</xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>  
  
2.  Call `QueryInterface` on `IOleUndoManager` for `IID_IOleCommandTarget`. Armazenar o ponteiro para <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>  
  
3.  Retransmissão seu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>e <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>chamadas armazenado `IOleCommandTarget` interface para os seguintes comandos StandardCommandSet97:</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>  
  
    -   cmdidUndo  
  
    -   cmdidMultiLevelUndo  
  
    -   cmdidRedo  
  
    -   cmdidMultiLevelRedo  
  
    -   cmdidMultiLevelUndoList  
  
    -   cmdidMultiLevelRedoList  
  
4.  Call `QueryInterface` on `IOleUndoManager` for `IID_IVsChangeTrackingUndoManager`. Armazenar o ponteiro para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
  
     Use o ponteiro para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>para chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>, o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>e o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A>métodos.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
  
5.  Call `QueryInterface` on `IOleUndoManager` for `IID_IVsLinkCapableUndoManager`.  
  
6.  Chamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A>com seu documento, que também deve implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> Quando o documento é fechado, chame `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`.  
  
7.  Quando o documento é fechado, chame `QueryInterface` em seu Gerenciador de desfazer para `IID_IVsLifetimeControlledObject`.  
  
8.  Chamada <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>  
  
9. Quando forem feitas alterações no documento, chame <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>Manager com um `OleUndoUnit` classe</xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> O <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>método mantém uma referência ao objeto, geralmente que liberá-lo logo após o <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>.</xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>  
  
 O `OleUndoManager` classe representa uma instância da pilha de desfazer. Portanto, há um objeto de Gerenciador de desfazer por entidade de dados sendo rastreado para desfazer ou refazer.  
  
> [!NOTE]
>  Enquanto o objeto do Gerenciador de desfazer é usado pelo editor de texto, é um componente geral que tem suporte específico para o editor de texto. Se você deseja oferecer suporte a vários nível desfazer ou refazer, você pode usar esse objeto para fazer isso.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager></xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject></xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Como: limpar a pilha de desfazer](../extensibility/how-to-clear-the-undo-stack.md)
