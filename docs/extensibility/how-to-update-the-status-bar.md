---
title: 'Como: atualizar a barra de Status | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
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
ms.openlocfilehash: 8448a2df42deae086f04d27518d6c7a2e3998edb
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-update-the-status-bar"></a>Como: atualizar a barra de Status
O **barra de Status** uma barra de controle que está localizada na parte inferior de muitas janelas de aplicativo que contém uma ou mais linhas de texto de status ou indicadores.  
  
### <a name="to-update-the-status-bar"></a>Para atualizar a barra de Status  
  
1.  Implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>em cada objeto de exibição individual (DocView) que fornece o editor, como um modo de exibição de formulário e um modo de exibição de código.</xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>  
  
2.  Quando o IDE chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>, atualize as informações de **barra de Status** chamando os métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> </xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>  
  
    > [!NOTE]
    >  O IDE chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>somente quando a janela de documento for ativada inicialmente.</xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> Para o restante do tempo que a janela do documento está ativa, você deve atualizar o **barra de Status** informações como o estado de suas alterações do editor.  
  
## <a name="robust-programming"></a>Programação robusta  
 A **barra de Status** contém quatro campos separados:  
  
-   Texto de status  
  
-   Barra de progresso  
  
-   Ícone animado  
  
-   Informações do Editor  
  
 Para obter mais informações, consulte [barras de Status](/visual-cpp/mfc/status-bars).  
  
 O IDE chama automaticamente o <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>método de sua <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>implementação quando a janela de documento é ativada.</xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> </xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>  
  
 O implementador de VSPackage é responsável por atualizar o texto de status na barra de status. O IDE redefine essa cadeia de caracteres como "Pronto" se o campo de texto de status é definido como texto vazio ("") no tempo ocioso.  
  
## <a name="see-also"></a>Consulte também  
 [Barras de status](/visual-cpp/mfc/status-bars)
