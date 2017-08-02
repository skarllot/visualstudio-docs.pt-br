---
title: Acessando o Buffer de texto usando a API herdada | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
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
ms.openlocfilehash: 9487bd37d786a40981345609ad5e69a55f1e91a5
ms.lasthandoff: 02/22/2017

---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>Acessando o Buffer de texto usando a API herdada
O texto é responsável por gerenciar fluxos de texto e persistência de arquivo. Embora o buffer pode ler ou gravar outros formatos, toda a comunicação comum com o buffer é executada usando Unicode. Nas APIs herdadas, o buffer de texto pode usar um - ou um sistema de coordenadas bidimensional para identificar os locais de caracteres no buffer.  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>Dimensão de um e dois sistemas de coordenadas  
 Uma posição de coordenadas unidimensional é baseada na posição do caractere do primeiro caractere no buffer, como 147. Você usa o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>interface para acessar um local unidimensional no buffer.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> Um sistema de coordenadas bidimensional é com base nos pares de linha e de índice. Por exemplo, um caractere em buffer em 43, 5 seria na linha 43, cinco caracteres à direita do primeiro caractere na linha. Acessar um local bidimensional no buffer usando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> Tanto o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>e o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>as interfaces são implementadas pelo objeto de buffer de texto (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>) e pode ser acessado entre si usando `QueryInterface`.</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> O diagrama a seguir mostra essas e outras interfaces principais <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>  
  
 ![Objeto de Buffer de texto](~/extensibility/media/vstextbuffer.gif "vsTextBuffer")  
Objeto de buffer de texto  
  
 Embora o sistema de coordenadas funciona no buffer de texto, ele é otimizado para usar coordenadas bidimensionais. Um sistema de coordenadas unidimensional pode criar sobrecarga de desempenho. Portanto, use o sistema de coordenadas bidimensional sempre que possível.  
  
 O segunda responsabilidade do buffer de texto é a persistência de arquivo. Para fazer isso, o objeto de buffer de texto implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>e atua como o componente de objeto de dados de documentos para itens de projeto e outros componentes do ambiente envolvidos na persistência.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> Para obter mais informações, consulte [abrindo e salvando itens de projeto](../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Alterando as configurações de exibição usando a API herdada](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Explica como alterar as configurações de exibição usando a API herdada.  
  
 [Usando o Gerenciador de texto para monitorar as configurações globais](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Explica como usar o Gerenciador de texto para monitorar as configurações globais...  
  
## <a name="see-also"></a>Consulte também  
 [Dentro do Editor de núcleo](../extensibility/inside-the-core-editor.md)
