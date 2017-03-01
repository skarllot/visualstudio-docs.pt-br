---
title: 'Como: hospedar um Editor em outro Editor | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 14
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
ms.openlocfilehash: 5987f653d5db1dcf6757d752cf71ca158086b3ff
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-host-an-editor-in-another-editor"></a>Como: hospedar um Editor em outro Editor
No Visual Studio, você pode hospedar um editor dentro de outro, especificando a janela de hospedagem como uma janela pai. Para fazer isso, defina os parâmetros <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>e <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>no quadro de janela filho.</xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> </xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Para configurar o quadro de janela para hospedar um editor  
  
1.  Designe um editor como um editor hospedado, criando um painel de janela filho.  
  
     Esse painel é onde entra texto do editor.  
  
2.  Criar um editor de hospedagem usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>  
  
3.  Definir o <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>e <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>Propriedades na implementação do quadro de janela do editor hospedado passando essas propriedades como parâmetros para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>método, respectivamente.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> </xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> </xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>  
  
     Se você precisar recuperar esses parâmetros, passar essas propriedades para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>  
  
4.  Chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>método para o editor independente.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>  
  
     O editor aparece no painel hospedado do editor de conteúdo.  
  
## <a name="robust-programming"></a>Programação robusta  
 O **Application Designer** no Visual Studio Team Edition for Architects é um exemplo de um quadro de janela de editor hospedagem outro editor. O **Application Designer** hospeda outros designers no painel direito. Um painel designer (ou **propriedades** página) para cada um dos designers independentes é adicionado ao quadro da janela recipiente.
