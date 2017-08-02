---
title: "Como: adicionar marcadores de texto padrão | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: 10
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
ms.openlocfilehash: eed2b832e4432e663c74680c83777a727bb1583f
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-add-standard-text-markers"></a>Como: adicionar marcadores de texto padrão
Use o procedimento a seguir para criar um tipo de marcador de texto padrão fornecido com o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor básicos.  
  
### <a name="to-create-a-text-marker"></a>Para criar um marcador de texto  
  
1.  Dependendo se você estiver usando uma ou duas - sistema de coordenadas tridimensional, chame o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>método ou o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A>método para criar um novo marcador de texto.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>  
  
     Na chamada de método, especifique um tipo de marcador, um intervalo de texto para criar o marcador e um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Esse método retorna um ponteiro ao marcador de texto criado recentemente. Tipos de marcador são tirados de <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE>enumeração.</xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> Especifique um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>interface se você deseja ser informado sobre eventos de marcador.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
  
    > [!NOTE]
    >  Crie marcadores de texto no thread da interface do usuário principal somente. O editor de núcleo se baseia no conteúdo do buffer de texto para criar marcadores de texto e o buffer de texto não é thread-safe.  
  
## <a name="adding-a-custom-command"></a>Adicionar um comando personalizado  
 Implementando o `IVsTextMarkerClient` interface e fornecendo um ponteiro para ele de um marcador aprimora o comportamento do marcador de várias maneiras. Em primeiro lugar, isso permite que você forneça dicas para o marcador e executar comandos. Isso também permite que você para receber notificações de eventos para marcadores individuais e criar um menu de contexto sobre o marcador. Use o procedimento a seguir para adicionar um comando personalizado no menu de contexto do marcador.  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>Para adicionar um comando personalizado ao menu de contexto  
  
1.  Antes que seja exibido no menu de contexto, o ambiente chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A>método e passa a você um ponteiro para o marcador de texto afetado e o número do item de comando no menu de contexto.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A>  
  
     Por exemplo, os comandos de ponto de interrupção específico no menu de contexto incluem **remover ponto de interrupção** por meio de **novo ponto de interrupção**, conforme exibido na tela a seguir.  
  
     ![Menu de contexto do marcador](~/docs/extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2.  Devolver um texto identificando o nome do comando personalizado. Por exemplo, **remover ponto de interrupção** pode ser um comando personalizado se o ambiente não já forneceu-lo. Você também passa novamente se o comando é suportado, disponível e habilitado, e/ou uma alternância-off. O ambiente usa essas informações para exibir o comando personalizado no menu de contexto da forma correta.  
  
3.  Para executar o comando, o ambiente chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A>método, transmitindo um ponteiro para o marcador de texto e o número do comando selecionado no menu de contexto.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A>  
  
     Use essas informações desta chamada para executar quaisquer ações do marcador de texto de comando personalizado dita.  
  
## <a name="see-also"></a>Consulte também  
 [Usar marcadores de texto com a API herdada](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Como: implementar marcadores de erro](../extensibility/how-to-implement-error-markers.md)   
 [Como: criar marcadores de texto personalizado](../extensibility/how-to-create-custom-text-markers.md)   
 [Como: usar marcadores de texto](../extensibility/how-to-use-text-markers.md)
