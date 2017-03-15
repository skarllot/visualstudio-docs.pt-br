---
title: 'Como: usar marcadores de texto | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 13
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
ms.openlocfilehash: 03e265193afa5cce4189042bd4807a687ffcf62c
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-use-text-markers"></a>Como: usar marcadores de texto
Marcadores de texto podem ser aplicadas para editar um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>objeto.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="to-apply-text-markers"></a>Para aplicar marcadores de texto  
  
1.  Obter uma instância de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>classe.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>  
  
    > [!NOTE]
    >  O editor de núcleo automaticamente aplica marcadores de texto padrão para qualquer documento que está editando, e não deve ser necessário aplicar marcadores de texto padrão explicitamente.  
  
2.  Obter uma identificação de tipo de marcador do marcador que você está interessado em chamando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A>método com o `GUID` do marcador do texto que você deseja trabalhar com.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A>  
  
    > [!NOTE]
    >  Não use o `GUID` do VSPackage ou do serviço que fornece o marcador de texto.  
  
3.  Use a ID de tipo de marcador obtida chamando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A>método como um parâmetro ao chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>método ou o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A>método para aplicar um marcador de texto para uma determinada região do texto.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A>  
  
#### <a name="to-add-features-to-text-markers"></a>Para adicionar recursos a marcadores de texto  
  
1.  Pode ser desejável para adicionar recursos adicionais a um marcador de texto, como dicas de ferramenta, um menu de contexto especial ou manipulador para circunstâncias especiais. Para fazer isso:  
  
2.  Criar um objeto que implementa o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
  
3.  Se a funcionalidade adicional for desejada, implemente o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>e o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>interfaces no mesmo objeto que implementa o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
  
4.  Passar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>interface que você criar para a chamada para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>método ou o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A>método usado para aplicar o marcador de texto para uma determinada região do texto.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
  
5.  Ao adicionar o suporte do menu de contexto a uma região de marcador de texto é necessário criar o menu.  
  
     Para obter mais informações sobre como criar um contexto menu, consulte [Menus de contexto](../extensibility/context-menus.md).  
  
6.  O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente chama os métodos das interfaces fornecidas, como o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A>método, ou o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A>método conforme necessário.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A>  
  
## <a name="see-also"></a>Consulte também  
 [Usar marcadores de texto com a API herdada](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Como: adicionar marcadores de texto padrão](../extensibility/how-to-add-standard-text-markers.md)   
 [Como: criar marcadores de texto personalizado](../extensibility/how-to-create-custom-text-markers.md)   
 [Como: implementar marcadores de erro](../extensibility/how-to-implement-error-markers.md)
