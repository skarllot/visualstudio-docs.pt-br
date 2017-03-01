---
title: Eventos de Buffer de texto na API herdada | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
caps.latest.revision: 16
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
ms.openlocfilehash: 39ac6a711278950d09ed16b157fc89980144e3d0
ms.lasthandoff: 02/22/2017

---
# <a name="text-buffer-events-in-the-legacy-api"></a>Eventos de Buffer de texto na API herdada
O objeto de buffer de texto emite vários eventos diferentes que permitem que você responda às situações diferentes.  
  
 Quando você estiver usando a API herdada, você deve implementar as seguintes interfaces para receber notificação de alterações para o buffer de texto. Expõe as interfaces para o buffer de texto usando o `IConnectionPointContainer` modificações na interface no buffer de texto para receber notificação da linha do buffer. Para obter mais informações, consulte [como: registrar eventos de Buffer de texto com a API herdada](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). No caso de `IVsTextStreamEvents` ou `IVsTextLinesEvents` interfaces, as alterações são retornadas em qualquer uma ou duas dimensões coordenadas, respectivamente.  
  
## <a name="text-buffer-interfaces"></a>Interfaces de Buffer de texto  
 A seguir estão as interfaces implementadas pelo objeto de buffer de texto.  
  
|Interface|Descrição|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permite a criação de ações compostas (ou seja, ações que são agrupadas em uma unidade única de desfazer/refazer).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Permite a persistência de dados de documentos gerenciados pelo buffer de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Fornece serviços básicos; usado por muitos clientes.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Fornece leitura e gravação a recursos usando coordenadas bidimensionais. Herda de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Rápido e fornece acesso sequencial orientada por fluxo ao texto no buffer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Fornece leitura e gravação a recursos usando coordenadas unidimensionais. Herda de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData></xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Fornece acesso a uma coleção genérica de propriedades. A propriedade mais importante é o nome ou o moniker do buffer. Você pode armazenar seus próprios dados aleatórios no buffer com essa interface criando um GUID e usá-lo como uma chave.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer></xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Oferece suporte a pontos de conexão para eventos.|  
  
## <a name="text-buffer-event-interfaces"></a>Interfaces de evento de Buffer de texto  
 A seguir estão as interfaces para notificação de eventos de buffer de texto.  
  
|Interface|Descrição|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Notifica os clientes quando um novo serviço de linguagem está associado um buffer de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Notifica os clientes quando um buffer de texto é inicializado e quando são feitas alterações aos dados no buffer de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Notifica os clientes de alterações para o buffer de texto subjacente em coordenadas unidimensionais.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Notifica os clientes de alterações para o buffer de texto subjacente em coordenadas bidimensionais.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Notifica os clientes de alterações de dados de usuário.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Notifica os clientes do gesto última confirmação para disparar o evento e fornece o intervalo de texto alterado. O `IVsPreliminaryTextChangeCommitEvents` interface não é acionada em resposta a desfazer ou refazer comandos. Eventos acionados apenas para buffers que tenham um Gerenciador de desfazer. `IVsPreliminaryTextChangeCommitEvents`é acionado antes de outros eventos, como uma lista muito, para certificar-se de que os outros eventos não alteram o texto antes que as alterações sejam confirmadas. O VSPackage deve monitorar o o `IVsPreliminaryTextChangeCommitEvents` interface ou `IVsFinalTextChangeCommitEvents` interface, mas não ambos.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Notifica os clientes do gesto última confirmação para disparar o evento e fornece o intervalo de texto alterado. O `IVsFinalTextChangeCommitEvents` interface não é acionada em resposta a desfazer ou refazer comandos. Eventos acionados apenas para buffers que tenham um Gerenciador de desfazer. `IVsFinalTextChangeCommitEvents`destina para uso somente por serviços de linguagem ou outros objetos que têm controle total sobre a edição. O VSPackage deve monitorar o o `IVsPreliminaryTextChangeCommitEvents` interface ou `IVsFinalTextChangeCommitEvents` interface, mas não ambos.|  
  
## <a name="see-also"></a>Consulte também  
 [Acessando o Buffer de texto usando a API herdada](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [Como: registrar eventos de Buffer de texto com a API herdada](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)
