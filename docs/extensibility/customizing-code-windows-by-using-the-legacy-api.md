---
title: "Personalizando o Windows de código usando a API herdada | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 19
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
ms.openlocfilehash: 620125814b150bf05e46b39099e09593e0ea8e5a
ms.lasthandoff: 02/22/2017

---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>Personalizando o Windows de código usando a API herdada
Uma janela de código é um objeto de janela de documento que oferece suporte a um ou mais modos de exibição de texto. Os recursos exatos de uma janela de código dependem do serviço de idioma associado. No modo de interface de documentos múltiplos (MDI), a janela de código é o quadro de filho MDI.  
  
 Janelas de código são controladas pelos serviços de linguagem, e cada serviço de linguagem pode fornecer seu próprio Gerenciador de janela de código. Isso permite que o serviço de linguagem adicionar seus próprio adornos a janela de código, como rabiscos, colorização e muito mais. Para obter mais informações sobre como criar uma janela principal, consulte [instanciar o principal Editor usando a API herdada](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Uma janela de código é um <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>objeto que tem um modo de exibição de texto e qualquer ornamentos situados no objeto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Quando você criar a janela de código durante a instanciação do núcleo do editor, o serviço de linguagem pode anexar um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>para a janela de código, como é mostrado na ilustração a seguir.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>  
  
 ![Gráfico de CodeWindow](../extensibility/media/vscodewindow.gif "vscodewindow")  
Janela de código  
  
 O serviço de linguagem implementa o Gerenciador de janelas de código e é responsável por gerenciar ornamentos, como uma barra de menu suspenso. O janela de código chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>método durante a inicialização da janela de código.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> Quando essa chamada é feita, o serviço de linguagem pode adicionar uma barra de menu suspenso ou uma barra de botões (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>) para a janela de código.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>  
  
## <a name="in-this-section"></a>Nesta seção  
 `Customizing Code Windows by Using the Legacy API`  
 Explica como personalizar o windows de código usando a API herdada.  
  
 [Como: hospedar um Editor em outro Editor](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Explica como hospedar um segundo editor dentro de uma janela do editor.  
  
 [Como: disparar eventos quando o Editor perde o foco](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Explica como anexar um modo de exibição de documento para um objeto de dados do documento.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow></xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer></xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView></xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Criando o Editor principal usando a API herdada](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Acessando theText exibição usando a API herdada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
