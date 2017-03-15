---
title: Menus de contexto | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
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
ms.openlocfilehash: 8209671452b32e7bccdd7e52fb6b2e61f2191feb
ms.lasthandoff: 02/22/2017

---
# <a name="context-menus"></a>Menus de contexto
Menus de contexto são exibidos quando um usuário clica com o botão direito em uma região ativa da área do cliente e limpar quando o botão direito do mouse é liberado.  
  
## <a name="editor-context-menus"></a>Menus de Contexto do Editor  
 Interceptando `ECMD_SHOWCONTEXTMENU`, seu serviço de linguagem pode controlar os menus de contexto que serão exibido no editor. Para exibir seu próprio menu de contexto, lidar com esse comando quando ele é passado para o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Se você não tratar esse comando, o IDE exibe um menu de contexto padrão fornecido para o editor. Você também pode controlar o conteúdo do menu de contexto em uma base por marcador. Para obter mais informações sobre isso, consulte [usando marcadores de texto com a API herdada](../extensibility/using-text-markers-with-the-legacy-api.md) e [comandos do serviço de linguagem herdado interceptando](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolvendo um serviço de linguagem herdado](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Estendendo Menus e comandos](../extensibility/extending-menus-and-commands.md)
