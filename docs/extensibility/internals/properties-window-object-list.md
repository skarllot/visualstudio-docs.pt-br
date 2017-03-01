---
title: Lista de objetos de janela de propriedades | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
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
ms.openlocfilehash: 5344f4b1fb8743620691e6a6c75316cd9aa486db
ms.lasthandoff: 02/22/2017

---
# <a name="properties-window-object-list"></a>Lista de objetos de janela de propriedades
Na lista de **propriedades** janela é uma lista suspensa que permite que você altere a seleção para outros objetos disponíveis dentro de uma ou mais janelas selecionadas. Selecionar um objeto diferente de dentro desta lista dispara uma chamada para <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>para informar o ambiente de que um novo objeto foi selecionado.</xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> As informações exibidas de **propriedades** janela for alterada para mostrar as propriedades associadas ao objeto selecionado recentemente.  
  
## <a name="the-object-list"></a>A lista de objetos  
 A lista de objeto consiste em dois campos: o nome do objeto (exibidas em negrito) e o tipo de objeto.  
  
 O nome do objeto exibido à esquerda do tipo de objeto em negrito é recuperado do próprio objeto usando o `Name` propriedade fornecida pelo <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>interface.</xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, o único método em <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, retorna <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>para coclass da interface.</xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> </xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo></xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A> O **propriedades** janela usa <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>para obter o nome de coclass, que é exibido como o nome do objeto na lista suspensa.</xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>  
  
 Se o objeto não tem um `Name` um nome de propriedade não é exibida na área de nome da lista de objetos. Você pode adicionar uma propriedade de nome para o objeto se desejar que o nome exibido na lista de objetos.  
  
 Se o objeto COM não implementa <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, o **propriedades** janela exibe o nome da interface no lugar do nome do objeto no lado esquerdo da lista.</xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo propriedades](../../extensibility/internals/extending-properties.md)
