---
title: 'Como: implementar marcadores de erro | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
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
ms.openlocfilehash: 5c52217bdfabdfa0931560194bf12fde74919044
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-implement-error-markers"></a>Como: implementar marcadores de erro
Marcadores de erro (ou sublinhados ondulados vermelhos) são as personalizações do editor de texto para implementar o mais difícil. No entanto, os benefícios que eles oferecem aos usuários do seu VSPackage podem compensam o custo para fornecê-las. Marcadores de erro sutilmente marcam o texto que o analisador de linguagem considerar incorreto com uma linha vermelha ondulada ou ondulada. Este indicador ajuda os programadores exibindo visualmente código incorreto.  
  
 Use marcadores de texto para implementar os sublinhados ondulados vermelhos. Como regra, serviços de linguagem adicionar sublinhados ondulados vermelhos no buffer de texto como uma passagem de plano de fundo, no tempo ocioso ou em um thread em segundo plano.  
  
### <a name="to-implement-the-red-wavy-underline-feature"></a>Para implementar o recurso de sublinhado ondulado vermelho  
  
1.  Selecione o texto sob a qual você deseja colocar o sublinhado vermelho ondulado.  
  
2.  Criar um marcador do tipo `MARKER_CODESENSE_ERROR`. Para obter mais informações, consulte [como: adicionar marcadores de texto padrão](../extensibility/how-to-add-standard-text-markers.md).  
  
3.  Depois disso, passe um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>ponteiro de interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
  
 Esse processo também permite que você crie o texto da dica ou um menu de contexto especial sobre um determinado marcador. Para obter mais informações, consulte [como: adicionar marcadores de texto padrão](../extensibility/how-to-add-standard-text-markers.md).  
  
 Os objetos a seguir são necessários para que os marcadores de erro podem ser exibidos.  
  
-   Um analisador.  
  
-   Um provedor de tarefa (ou seja, uma implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>) que mantém um registro das alterações nas informações de linha para identificar as linhas para ser analisado novamente.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>  
  
-   Eventos de alteração de um filtro de exibição de texto que captura o cursor do modo de exibição usando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>) método.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>  
  
 O analisador, o provedor de tarefa e o filtro fornecem a infra-estrutura necessária para que os marcadores de erro possível. As etapas a seguir fornecem o processo para exibir marcadores de erro.  
  
1.  Em uma exibição que está sendo filtrada, o filtro obtém um ponteiro para o provedor de tarefa associado com dados da exibição.  
  
    > [!NOTE]
    >  Você pode usar o mesmo filtro de comando para dicas de método, conclusão de instrução, marcadores de erro e assim por diante.  
  
2.  Quando o filtro recebe um evento indicando que você moveu para outra linha, é criada uma tarefa para verificar se há erros.  
  
3.  O manipulador de tarefa verifica se a linha está suja. Nesse caso, ele analisa a linha de erros.  
  
4.  Se forem encontrados erros, o provedor de tarefas cria uma instância do item de tarefa. Esta instância cria o marcador de texto que usa o ambiente como um marcador de erro no modo de exibição de texto.  
  
## <a name="see-also"></a>Consulte também  
 [Usar marcadores de texto com a API herdada](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Como: adicionar marcadores de texto padrão](../extensibility/how-to-add-standard-text-markers.md)   
 [Como: criar marcadores de texto personalizado](../extensibility/how-to-create-custom-text-markers.md)   
 [Como: usar marcadores de texto](../extensibility/how-to-use-text-markers.md)
