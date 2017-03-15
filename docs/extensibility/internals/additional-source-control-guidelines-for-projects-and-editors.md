---
title: Diretrizes de controle de origem adicionais para projetos e editores | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
caps.latest.revision: 14
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
ms.openlocfilehash: ee74f16c90dbf697732a490f895efb1a52233d80
ms.lasthandoff: 02/22/2017

---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Diretrizes de controle de origem adicionais para projetos e editores
Há uma série de diretrizes que projetos e editores devem seguir para dar suporte ao controle de origem.  
  
## <a name="guidelines"></a>Diretrizes  
 O projeto ou o editor também deve fazer o seguinte para dar suporte ao controle de origem:  
  
|Área|Projeto|Editor|Detalhes|  
|----------|-------------|------------|-------------|  
|Cópias particulares de arquivos|X||O ambiente oferece suporte a cópias particulares de arquivos. Ou seja, cada pessoa inscrita no projeto tem sua própria cópia privada dos arquivos no projeto.|  
|Persistência de Unicode/ANSI|X|X|Se você escrever o código de persistência, manter arquivos no formato ANSI porque a maioria dos programas de controle de origem atualmente não dão suporte a Unicode.|  
|Enumerar arquivos|X||O projeto deve conter uma lista específica de todos os arquivos dentro dele e deve ser capaz de enumerar a lista de arquivos usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>(VSH_PROPID_First_Child/Next_Sibling).</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> O projeto também deve expor os nomes de item por meio de seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A>implementação e suporte à pesquisa de nome (inclusive arquivos especiais) por meio de seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>implementação.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A>|  
|Formato do texto|X|X|Quando possível, os arquivos devem ser em formato de texto para dar suporte a mesclagem de versões diferentes. Arquivos que não estão no formato de texto não podem ser mesclados com outras versões do arquivo mais tarde. O formato de texto preferido é XML.|  
|Base de referência|X||Projetos baseados em referências prontamente têm suporte no controle de origem. No entanto, projetos baseados em diretório também são suportados pelo controle de origem, desde que o projeto pode produzir uma lista de seus arquivos sob demanda, independentemente dos arquivos existirem no disco. Ao abrir um projeto do controle de origem, o arquivo de projeto é interrompido primeiro antes de qualquer um dos arquivos.|  
|Manter objetos e propriedades em ordem previsível|X|X|Manter os arquivos em uma ordem previsível, como ordem alfabética, para facilitar a mesclagem.|  
|Recarregar|X|X|Quando um arquivo é alterado no disco, seu editor deve ser capaz de recarregá-lo. Quando você participa no controle de origem, o ambiente será recarregar os dados para você, chamando seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>implementação.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> O caso de recarregar mais difíceis é quando um check-out ocorre quando você tiver chamado IVsQueryEditQuerySave::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e processamento de informações.</xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> No entanto, seu código de recarregar deve ser capaz de executar nessa situação.<br /><br /> O ambiente recarrega automaticamente arquivos de projeto. No entanto, um projeto deve implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>se tiver aninhado hierarquias para oferecer suporte a recarregar aninhados arquivos de projeto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|  
  
## <a name="see-also"></a>Consulte também  
 [Suporte a controle de origem](../../extensibility/internals/supporting-source-control.md)
