---
title: Usar marcadores de texto com a API herdada | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
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
ms.openlocfilehash: 26be8a5496493f14b004cea16155f89f45d7d25c
ms.lasthandoff: 02/22/2017

---
# <a name="using-text-markers-with-the-legacy-api"></a>Usar marcadores de texto com a API herdada
Um marcador de texto é um flutuante intervalo de texto em um buffer que pode afetar a exibição e o comportamento de uma região de texto. Marcadores incluem pontos de interrupção, indicadores, os sublinhados ondulados e regiões de somente leitura. Marcadores de texto são basicamente diferentes das cores da sintaxe. Coloração de sintaxe é uma maneira rápida para comunicar-se a sintaxe da linguagem que está associada uma região de texto. Coloração de sintaxe geralmente é solicitada ao Windows redesenha a tela quando a velocidade é importante. Coloração de sintaxe altera somente a cor do texto. Marcadores de texto podem alterar outras propriedades de texto. Marcadores de texto podem "float" e aplicar um comportamento especial e cores.  
  
 Por causa da sobrecarga de desempenho associada com marcadores de texto, não crie muitos marcadores para seus buffers de texto. Cada marcador é atualizado toda vez que o usuário edita o conteúdo do buffer.  
  
> [!NOTE]
>  Os usuários podem alterar a cor de um tipo de marcador visível, mas não sua forma e estilo. Para obter mais informações, consulte [fontes e cores, ambiente, caixa de diálogo Opções](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Como: adicionar marcadores de texto padrão](../extensibility/how-to-add-standard-text-markers.md)|Descreve como adicionar um tipo de marcador de texto padrão fornecido pelo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principal para uma exibição de texto.|  
|[Como: implementar marcadores de erro](../extensibility/how-to-implement-error-markers.md)|Descreve como implementar uma instância do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] marcador que é usado para indicar erros usando os sublinhados ondulados vermelhos.|  
|[Como: criar marcadores de texto personalizado](../extensibility/how-to-create-custom-text-markers.md)|Descreve como criar e adicionar um tipo de marcador de texto personalizado a um modo de exibição de texto.|  
|[Como: usar marcadores de texto](../extensibility/how-to-use-text-markers.md)|Explica como adicionar marcadores de texto.|  
|[Dentro do Editor de núcleo](../extensibility/inside-the-core-editor.md)|Descreve os recursos do editor de núcleo e fornece detalhes sobre como personalizar o editor de núcleo.|  
|[Recursos do Editor](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|Descreve os recursos disponíveis no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor básicos.|  
  
## <a name="reference"></a>Referência  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType></xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Fornece um mecanismo uniforme para obter informações sobre o tipo de marcador um texto específico, se predefinidos pelo editor ou registrados por um VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 Fornece acesso a e ajusta a posição de um marcador de texto em um buffer de texto usando coordenadas bidimensionais.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 Fornece métodos para gerenciamento de marcadores de texto.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 Fornece retornos de chamada de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE e outros processos que são usados para ajustar um marcador de texto.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 Estende a funcionalidade que está disponível por meio do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>interface fornecendo retornos de chamada adicionais.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 Estende a funcionalidade que está disponível por meio do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>interface fornecendo retornos de chamada adicionais.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 Permite que um tipo de marcador determinar se outros tipos de marcador compartilham o mesmo conjunto de cores.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 Fornece o contexto para marcadores de texto no editor de núcleo. Para cada tipo de marcador de texto que está no editor de núcleo, o IDE cria uma marca <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>objeto.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 Um manipulador que é fornecido para marcadores cujos glifos oferecer suporte a edição arrastar-e-soltar. Um glifo é um ícone que indica a posição de um marcador.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 Retorna um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>interface de um serviço que fornece um texto marcadores para outros VSPackages.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 Fornece acesso a e ajusta a posição de um marcador de texto em um buffer de texto usando coordenadas unidimensionais. Se for possível, não use essa interface.
