---
title: Acessando as camadas de texto usando a API herdada | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
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
ms.openlocfilehash: c1c9166116f92d87f4d5d4f0278d100339f5bf1f
ms.lasthandoff: 02/22/2017

---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>Acessando as camadas de texto usando a API herdada
Normalmente, uma camada de texto encapsula algum aspecto do layout de texto. Por exemplo, uma camada de "uma função no tempo" oculta texto antes e depois de uma função que contém o cursor (ponto de inserção de texto).  
  
 Uma camada de texto reside entre um buffer e um modo de exibição e modifica o modo que de exibição vê o conteúdo do buffer.  
  
## <a name="text-layer-information"></a>Informações da camada de texto  
 A lista a seguir descreve como as camadas de texto funcionam em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   O texto em uma camada de texto pode ser marcado com marcadores e coloração de sintaxe.  
  
-   Atualmente, você não pode implementar suas próprias camadas.  
  
-   Uma camada expõe <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, que é derivado de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> O buffer de texto em si também é implementado como uma camada, que permite uma exibição lidar polimorficamente com camadas subjacentes.  
  
-   Qualquer número de camadas pode estar entre a exibição e o buffer. Cada camada lida apenas com a camada abaixo dela, e o modo de exibição lida principalmente com a camada mais alto. (A exibição tem algumas informações sobre o buffer).  
  
-   Uma camada pode afetar apenas as camadas que estão abaixo dele. Ele não pode afetar as camadas acima dela, além da origem de eventos padrão.  
  
-   No editor de texto oculto, texto sintético e quebra automática de linha são implementados como camadas. Você pode implementar o texto oculto e sintético sem interagir diretamente com as camadas. Para obter mais informações, consulte [de estrutura de tópicos em um serviço de linguagem herdado](../extensibility/internals/outlining-in-a-legacy-language-service.md) e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>  
  
-   Cada camada de texto tem seu próprio sistema de coordenadas local que é exposto por meio de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> A camada de quebra automática de linha, por exemplo, pode conter duas linhas enquanto o buffer de texto subjacente pode conter apenas uma linha.  
  
-   O modo de exibição se comunica em camadas por meio de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> Use essa interface para reconciliar as coordenadas de exibição com coordenadas de buffer.  
  
-   Qualquer camada como camada de texto sintéticos que se origina o texto deve fornecer uma implementação local do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>  
  
-   Além dos <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, uma camada de texto deve implementar <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>e disparar os eventos no <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> </xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>  
  
## <a name="see-also"></a>Consulte também  
 [Cores de sintaxe no editores personalizados](../extensibility/syntax-coloring-in-custom-editors.md)   
 [Usar marcadores de texto com a API herdada](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Personalizando Menus e controles de Editor usando a API herdada](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)
