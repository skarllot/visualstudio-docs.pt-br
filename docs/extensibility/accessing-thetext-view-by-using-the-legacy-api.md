---
title: "Acessando theText exibição usando a API herdada | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: 15
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
ms.openlocfilehash: 00425866e9460185a81b9769f4b41e3ada154bcd
ms.lasthandoff: 02/22/2017

---
# <a name="accessing-thetext-view-by-using-the-legacy-api"></a>Acessando theText exibição usando a API herdada
Uma exibição de texto é uma apresentação do texto que é armazenado em um buffer de texto. Você pode acessar a exibição de texto usando a API herdada, conforme mostrado na seção a seguir.  
  
## <a name="text-view-object"></a>Objeto de exibição de texto  
 Cada exibição é associada com o próprio buffer de texto e o modo de exibição é uma janela nos dados no buffer. O diagrama a seguir mostra as interfaces principais do objeto de exibição de texto, que é representado pelo <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>.</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>  
  
 ![Objeto de exibição de texto do Visual Studio](~/docs/extensibility/media/vstextview.gif "vstextview")  
Objeto de exibição de texto  
  
 O modo de exibição é uma maneira de apresentar o texto no buffer. Ele inclui recursos como quebra automática de linha e a estrutura de tópicos, para que o que você vê no modo de exibição não é uma representação exata do texto no buffer.  
  
 Um modo de exibição permite que outros serviços ou processos para interceptar os comandos de entrada e agir sobre eles antes que o modo de exibição age sobre eles. O mais comum para isso é um serviço de linguagem. Um serviço de linguagem talvez seja necessário, por exemplo, para interceptar o comando para a tecla ENTER fornecer personalizado recuo dicas de ferramenta ou comportamento.  
  
## <a name="adding-functionality-to-the-text-view"></a>Adicionando funcionalidade à exibição de texto  
 Você pode personalizar o comportamento de exibição de texto ao manipular os pressionamentos de teclas específicos. Para interceptar os pressionamentos de teclas, você deve implementar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>em seu objeto e forneça um destino de comando (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) para monitorar e interceptar comandos.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>  
  
 A exibição de texto usa arquitetura sequencial para filtros de comando. Novos filtros de comando (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objetos) são adicionados à sequência ao chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>método.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>  
  
 Notificação de eventos para o modo de texto é fornecida usando o `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents` interface. Implemente essa interface em seu objeto de cliente para receber a notificação de alterações para a exibição de texto. Expor essa interface para o modo de exibição de texto usando o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>interface na exibição do texto para receber notificação de alterações do modo de exibição.</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>  
  
## <a name="see-also"></a>Consulte também  
 [Alterando as configurações de exibição usando a API herdada](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [Usando o Gerenciador de texto para monitorar as configurações globais](../extensibility/using-the-text-manager-to-monitor-global-settings.md)
