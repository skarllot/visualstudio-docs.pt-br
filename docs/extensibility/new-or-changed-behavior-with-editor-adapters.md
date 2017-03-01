---
title: Comportamento novo ou alterado com adaptadores de Editor | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapter behavior
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
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
ms.openlocfilehash: a9c38a14ec99503d96ce3a10746dcda3a5574e73
ms.lasthandoff: 02/22/2017

---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>Comportamento novo ou alterado com adaptadores de Editor
Se você estiver atualizando o código escrito em relação a versões anteriores do editor de núcleo do Visual Studio e você planeja usar o editor adaptadores (ou correções) em vez de usar a nova API, você deve estar ciente das seguintes diferenças no comportamento dos adaptadores de editor em relação ao editor de núcleo anterior.  
  
## <a name="features"></a>Recursos  
  
#### <a name="using-setsite"></a>Usando SetSite()  
 Você deve chamar <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A>quando você criar buffers de texto, modos de exibição de texto e janelas de código antes de executar outras operações neles.</xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> No entanto, isso não é necessário se você usar a <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>criá-los, porque os métodos de Create () do serviço se chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A> </xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>  
  
#### <a name="hosting-ivscodewindow-and-ivstextview-in-your-own-content"></a>Hospedando IVsCodeWindow e IVsTextView em seu próprio conteúdo  
 Você pode hospedar ambos <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>em seu próprio conteúdo usando o modo de Win32 ou WPF.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> No entanto, você deve ter em mente que existem algumas diferenças nos dois modos.  
  
##### <a name="using-win32-and-wpf-versions-of-ivscodewindow"></a>Usando versões do IVsCodeWindow Win32 e WPF  
 A janela de código do editor é derivada de <xref:Microsoft.VisualStudio.Shell.WindowPane>, que implementa o Win32 anteriores <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>interface, bem como o novo WPF <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> </xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> </xref:Microsoft.VisualStudio.Shell.WindowPane> Você pode usar o <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A>método para criar um ambiente de hospedagem baseados em HWND, ou o <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A>método para criar um ambiente de hospedagem do WPF.</xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> </xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> O editor subjacente sempre usa o WPF, mas você pode criar o tipo de painel de janela que atenda aos seus requisitos de hospedagem se você estiver inserindo este painel de janela diretamente no seu próprio conteúdo.  
  
##### <a name="using-win32-and-wpf-versions-of-ivstextview"></a>Usando versões do IVsTextView Win32 e WPF  
 Você pode definir um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>para modo do Win32 ou WPF.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>  
  
 Quando uma fábrica de editor cria uma exibição de texto, por padrão, ele está hospedado dentro de um HWND, e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A>retorna um HWND.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> Você não deve usar esse modo para inserir o editor dentro de um controle WPF.  
  
 Para definir uma exibição de texto para o modo do WPF, você deve chamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A>e passar <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3>como uma inicialização sinalizadores no `InitView` parâmetro.</xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> Você pode obter a <xref:System.Windows.FrameworkElement>chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A> </xref:System.Windows.FrameworkElement>  
  
 Modo do WPF é diferente do modo de Win32 de duas maneiras. Primeiro, a exibição de texto pode ser hospedada em um contexto do WPF. Você pode acessar o painel do WPF, direcionando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane>chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Segundo, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A>ainda retorna um HWND, mas esse HWND pode ser usado somente para verificar sua posição e definir o foco no proprietário.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> Você não deve usar esse HWND para responder a uma mensagem WM_PAINT, porque ele não afeta como o editor pinta a janela. Esse HWND está presente apenas para facilitar a transição para o novo editor de código por meio dos adaptadores. É altamente recomendável que você não deve usar `VIF_NO_HWND_SUPPORT` se o componente exigir um HWND funcione, devido a limitações no HWND retornado de `GetWindowHandle` enquanto nesse modo.  
  
#### <a name="passing-arrays-as-parameters-in-native-code"></a>Passando matrizes como parâmetros no código nativo  
 Há muitos métodos herdado editor API com parâmetros que incluem uma matriz e sua contagem. Os exemplos são:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 Se você estiver chamando esses métodos em código nativo, você deve passar apenas um elemento por vez. Se você passar em mais de um elemento, a chamada será rejeitada, devido a problemas com a implementação de interoperabilidade primário.  
  
 O problema é mais complexo com métodos como <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A> Sempre que esse método é chamado, ele limpa a lista anterior dos tipos de marcador ignorados, portanto, não é possível simplesmente chamar esse método três vezes com três tipos diferentes de marcador. A única solução é chamar esse método apenas em código gerenciado.  
  
#### <a name="threading"></a>Threading  
 Você sempre deve chamar o adaptador de buffer do thread da interface do usuário. O adaptador de buffer é um objeto gerenciado, o que significa que a chamada para ele no código gerenciado ignorarão COM marshaling e sua chamada não serão automaticamente controlada no thread da interface do usuário.  Se você estiver chamando o adaptador de buffer de um thread em segundo plano, você deve usar <xref:System.Windows.Threading.Dispatcher.Invoke%2A>ou um método semelhante.</xref:System.Windows.Threading.Dispatcher.Invoke%2A>  
  
#### <a name="lockbuffer-methods"></a>Métodos de LockBuffer  
 Todos os métodos de LockBuffer() são preteridos. Os exemplos são:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### <a name="commit-events"></a>Confirmação de eventos  
 Confirmar eventos não são suportados. Chamar um método que avisa para esses eventos faz com que o método retorne um código de falha.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### <a name="texteditorevents"></a>TextEditorEvents  
 O <xref:EnvDTE.TextEditorEvents>não são acionados em Commit ().</xref:EnvDTE.TextEditorEvents> Em vez disso, eles acionado cada alteração de texto.  
  
#### <a name="text-markers"></a>Marcadores de texto  
 Você deve chamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A>em <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>objetos quando você removê-los.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> Nas versões anteriores, é necessário somente para os marcadores de versão.  
  
#### <a name="line-numbers"></a>Os números de linha  
 Para uma variedade de métodos em <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>, números de linha correspondem aos números de linha de buffer subjacente, os números de linha não esse fator na estrutura de tópicos e quebra, como no Visual Studio 2008.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>  
  
 Os métodos afetados incluem o seguinte (a lista não é exaustiva):  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.CenterLines%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.CenterLines%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetCaretPos%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineAndColumn%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineAndColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetNearestPosition%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetNearestPosition%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetPointOfLineColumn%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetPointOfLineColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetTextStream%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetTextStream%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWordExtent%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWordExtent%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.ReplaceTextOnLine%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.ReplaceTextOnLine%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetCaretPos%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetSelection%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetSelection%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetTopLine%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetTopLine%2A>  
  
#### <a name="outlining"></a>Estrutura de tópicos  
 Clientes <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>irão</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> ver apenas as regiões de estrutura de tópicos que foram adicionadas usando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>ou <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> Eles não verão regiões ad hoc, porque eles não são adicionados por meio dos adaptadores do editor. Da mesma forma, esses clientes não verá adicionados por linguagens (incluindo c# e C++) que estão usando o novo editor de código, em vez de adaptadores de editor de regiões de estrutura de tópicos.  
  
#### <a name="line-heights"></a>Altura da linha  
 No editor de novas linhas de texto podem ter alturas diferentes, dependendo do tamanho da fonte e transformações de linha possíveis que podem mover a linha em relação a outras linhas. A altura da linha retornada por métodos como <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A>é a altura de uma linha com o tamanho da fonte padrão sem transformações de linha aplicadas.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> Essa altura talvez ou pode não refletir a altura real de uma linha no modo de exibição.  
  
#### <a name="eventing-and-undo"></a>Eventos e desfazer  
 No editor de novo, a exibição continua a executar operações como renderização e gerando eventos continuamente, mesmo quando um cluster de desfazer está aberto. Esse comportamento é diferente das exibições herdadas que não realizar essas operações até após o fechamento do cluster desfazer.  
  
#### <a name="intellisense"></a>IntelliSense  
  
-   O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A>método irá falhar se você passar em uma classe que não implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2>ou <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> Win32 personalizado pop-ups desenhados pelo proprietário não são mais suportados.  
  
#### <a name="smarttags"></a>Marcas inteligentes  
 Não há suporte de adaptador para marcas inteligentes criadas, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData>, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow>, e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2>interfaces.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData>  
  
#### <a name="dte"></a>DTE  
 <xref:EnvDTE80.IncrementalSearch>não foi implementado.</xref:EnvDTE80.IncrementalSearch>  
  
## <a name="unimplemented-methods"></a>Métodos não implementados  
 Alguns métodos não foram implementados no adaptador da camada de texto, adaptador de buffer de texto e adaptador de exibição de texto.  
  
|Interface|Não implementado|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)`não foi implementado.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget></xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView></xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost></xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A>é implementado nos adaptadores mas ignorados pela estrutura de tópicos IU.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx></xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A>é implementado nos adaptadores mas ignorados pela estrutura de tópicos IU.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A>|
