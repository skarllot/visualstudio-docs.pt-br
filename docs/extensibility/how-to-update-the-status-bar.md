---
title: 'Como: atualizar a barra de Status | Microsoft Docs'
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 15b207618487fd49516849c591ef80c56b618ce0
ms.contentlocale: pt-br
ms.lasthandoff: 04/05/2017

---
# <a name="how-to-update-the-status-bar"></a>Como: atualizar a barra de Status
O **barra de Status** uma barra de controle que está localizada na parte inferior de muitas janelas de aplicativo que contém uma ou mais linhas de texto de status ou indicadores.  
  
### <a name="to-update-the-status-bar"></a>Para atualizar a barra de Status  
  
1.  Implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>em cada objeto de exibição individual (DocView) que fornece seu editor, como um modo de exibição de formulário e um modo de exibição de código.</xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>  
  
2.  Quando o IDE chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>, atualize as informações de **barra de Status** chamando os métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> </xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>  
  
    > [!NOTE]
    >  As chamadas IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>somente quando a janela de documento for ativada inicialmente.</xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> Para o restante do tempo que a janela do documento está ativa, você deve atualizar o **barra de Status** informações como o estado de suas alterações do editor.  
  
## <a name="robust-programming"></a>Programação robusta  
 Um **barra de Status** contém quatro campos separados:  
  
-   Texto de status  
  
-   Barra de progresso  
  
-   Ícone animado  
  
-   Informações de editor  
  
 Para obter mais informações, consulte [barras de Status](/cpp/mfc/status-bars).  
  
 O IDE chama automaticamente o <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>método de sua <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>implementação quando a janela do documento é ativada.</xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> </xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>  
  
 O implementador de VSPackage é responsável por atualizar o texto de status na barra de status. O IDE redefine essa cadeia de caracteres para "Pronta" se o campo de texto de status é definido como texto vazio ("") no tempo ocioso.  
  
## <a name="see-also"></a>Consulte também  
 [Barras de status](/cpp/mfc/status-bars)
