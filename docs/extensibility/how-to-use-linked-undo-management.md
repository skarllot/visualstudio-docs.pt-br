---
title: 'Como: usar o gerenciamento de desfazer vinculado | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 10
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
ms.openlocfilehash: 06fb6a1d3aebcf5c3e87675f131156cf11367ada
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-use-linked-undo-management"></a>Como: usar o gerenciamento de desfazer vinculado
Desfazer vinculado permite que o usuário simultaneamente desfazer as mesmas edições em vários arquivos. Por exemplo, as alterações simultâneas de texto em vários arquivos de programa, como um arquivo de cabeçalho e um arquivo do Visual C++, é uma transação de desfazer vinculado. Capacidade de desfazer vinculado é incorporada a implementação do ambiente do Gerenciador de desfazer, e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager>permite manipular esse recurso.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> Desfazer vinculado é implementado por uma unidade para desfazer pai que pode vincular pilhas de desfazer separado para ser tratado como uma unidade única de desfazer. O procedimento para usar desfazer vinculado é detalhado na seção a seguir.  
  
### <a name="to-use-linked-undo"></a>Usar Desfazer vinculado  
  
1.  Chamar `QueryService` na `SVsLinkedUndoManager` para obter um ponteiro para `IVsLinkedUndoTransactionManager`.  
  
2.  Criar unidade desfazer vinculado pai inicial chamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A> Isso define o ponto de partida para um conjunto de pilhas de desfazer sejam agrupados em pilhas de desfazer vinculado. No `OpenLinkedUndo` método, você também precisará especificar se deseja que o desfazer vinculado estrita ou não restrita. Desfazer vinculado não strict comportamento significa que alguns documentos com irmãos desfazer vinculado podem fechar e ainda deixar o outro vinculado desfazer irmãos em suas pilhas. Comportamento de desfazer vinculado Strict Especifica que todas as pilhas de irmão de desfazer vinculado precisam ser desfeita juntos ou não. Adicionar subsequentes vinculadas pilhas de desfazer chamando [IOleUndoManager::Add](http://msdn.microsoft.com/library/windows/desktop/ms680135) método.  
  
3.  Chamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A>para reverter todas as unidades de desfazer vinculado como um.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A>  
  
    > [!NOTE]
    >  Para implementar o gerenciamento de desfazer vinculado em um editor, adicione o gerenciamento de desfazer. Para obter mais informações sobre como implementar o gerenciamento de desfazer vinculado, consulte [como: implementar o gerenciamento de desfazer](../extensibility/how-to-implement-undo-management.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms682151)   
 [IOleUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms678476)   
 [Como: implementar o gerenciamento de desfazer](../extensibility/how-to-implement-undo-management.md)
