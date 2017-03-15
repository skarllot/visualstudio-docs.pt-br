---
title: Janelas de documento | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: 17
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
ms.openlocfilehash: b31b062a4e96016ac0b68d8da42979ddeccb500b
ms.lasthandoff: 02/22/2017

---
# <a name="document-windows"></a>Janelas de documento
No Visual Studio, uma *janela documento* é uma janela de quadro filho que está associada uma janela de interface de documentos múltiplos (MDI). Janelas de documento são geralmente usadas para a exibição e a modificação do código-fonte ou texto, mas também podem hospedar outros tipos funcionais. Janelas de documento:  
  
-   Podem ser organizados em grupos de guia horizontal ou vertical separada no pai MDI para que vários arquivos podem ser exibidos ao mesmo tempo.  
  
-   Pode ser encaixado em qualquer ordem no pai MDI.  
  
-   Pode ser flutuante livremente.  
  
-   São vinculados na ordem de tabulação para outras janelas MDI.  
  
 Os comandos para agrupamento, encaixe e flutuante podem ser encontradas no menu de atalho para uma guia da janela de documento.  
  
 Para obter mais informações sobre o comportamento de janelas no Visual Studio, consulte [Personalizar layouts de janela](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
## <a name="document-window-implementation"></a>Implementação de janela de documento  
 Janelas de documento são criadas com a implementação de um editor. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>interface cria janelas de documentos como parte de um editor de instanciar.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Para obter mais informações, consulte [Interfaces herdado no Editor de](../../extensibility/legacy-interfaces-in-the-editor.md).  
  
> [!NOTE]
>  Para fornecer compatibilidade e encaminhar os pontos em uma janela de navegação, implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> O editor de texto usa marcadores de texto para identificar os pontos de navegação no documento.  
  
## <a name="the-running-document-table"></a>A tabela de documento em execução  
 O IDE usa a tabela de documento (RDT) em execução para acompanhar o status de cada janela de documento. O RDT é o mecanismo pelo qual documento windows é notificado sobre eventos, como quando uma solução é fechada ou quando um arquivo foi editado. Para obter mais informações, consulte [executando tabela Document](../../extensibility/internals/running-document-table.md).  
  
## <a name="see-also"></a>Consulte também  
 [Atraso de carregamento de documentos](../../extensibility/internals/delayed-document-loading.md)
