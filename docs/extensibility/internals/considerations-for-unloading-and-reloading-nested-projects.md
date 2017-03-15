---
title: "Considerações para descarregar e recarregar projetos de aninhado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
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
ms.openlocfilehash: 9ee8ceab33df210c9a0ca1ac9da7eeab3808f53b
ms.lasthandoff: 02/22/2017

---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Considerações para descarregando e recarregando projetos aninhados
Quando você implementa os tipos de projeto aninhado, você deve executar etapas adicionais quando você descarrega e recarregar os projetos. Para notificar corretamente ouvintes de eventos de solução, você deve aumentar corretamente o `OnBeforeUnloadProject` e `OnAfterLoadProject` eventos.  
  
 Um motivo que você deve criar esses eventos dessa maneira é que você não deseja que o controle do código fonte (SCC) para excluir os itens do servidor e, em seguida, adicioná-los de volta como algo novo se houver um `Get` operação do SCC. Nesse caso, um novo arquivo seria carregado fora do SCC, e você precisa descarregar e recarregar todos os arquivos, caso eles sejam diferentes. Chamadas de SCC `ReloadItem`. A implementação dessa chamada é excluir o projeto e recriá-la novamente com a implementação de `IVsFireSolutionEvents` chamar `OnBeforeUnloadProject` e `OnAfterLoadProject`. Quando você executa essa implementação, o SCC é informado que o projeto foi excluído e adicionado novamente temporariamente. Portanto, o SCC não funciona no projeto como se o projeto foi efetivamente excluído do servidor e adicionado novamente.  
  
## <a name="reloading-projects"></a>Recarregar projetos  
 Para oferecer suporte a recarregar projetos aninhados, você implementa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> Na implementação do `ReloadItem`, feche os projetos aninhados e, em seguida, recriá-los.  
  
 Normalmente quando um projeto é recarregado, o IDE gera o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A>e o `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` eventos.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> No entanto, para projetos aninhados que serão excluídos e recarregados, o projeto pai inicia o processo, não do IDE. Como o projeto pai não gera eventos de solução, e o IDE não tem nenhuma informação sobre a inicialização do processo, os eventos não são gerados.  
  
 Para lidar com esse processo, as chamadas de projeto pai `QueryInterface` no <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents>interface desativar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> `IVsFireSolutionEvents`possui funções que informam ao IDE para gerar o `OnBeforeUnloadProject` evento Descarregar projeto aninhado e, em seguida, gerar o `OnAfterLoadProject` evento para recarregar o mesmo projeto.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Projetos de aninhamento](../../extensibility/internals/nesting-projects.md)
