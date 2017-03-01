---
title: 'Como: implementar o localizar e substituir o mecanismo | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
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
ms.openlocfilehash: 96650e2c3c3be30a7da1ec52dea0ba5d7ef7598b
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Como: implementar o localizar e substituir o mecanismo
Visual Studio fornece duas maneiras de localizar/substituir a implementação. Uma maneira é passar uma imagem de texto para o shell e deixá-lo a lidar com a pesquisa, realce e substituindo texto. Isso permite aos usuários especificar vários intervalos de texto. Como alternativa, o VSPackage pode controlar essa funcionalidade em si. Em ambos os casos, você deve notificar o shell sobre o destino atual e as metas para todos os documentos abertos.  
  
### <a name="to-implement-findreplace"></a>Para implementar localizar/substituir  
  
1.  Implementar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>interface em um dos objetos retornados pelo quadro propriedades <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>ou <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>.</xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> </xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> Se você estiver criando um editor personalizado, você deve implementar essa interface como parte da classe editor personalizado.  
  
2.  Use o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A>método para especificar as opções que suporta seu editor e indicar se ele implementa a pesquisa de texto imagem.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A>  
  
     Se o editor dá suporte a imagem de texto Pesquisar, implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>  
  
     Caso contrário, implementar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>  
  
3.  Se você implementar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>métodos, você pode simplificar suas tarefas de pesquisa chamando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper></xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget></xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID></xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
