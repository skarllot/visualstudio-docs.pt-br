---
title: "Detalhes de configuração de controle de origem | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
caps.latest.revision: 11
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
ms.openlocfilehash: 4d23f2c99897a65cf842caee3cd4badd6d7809a3
ms.lasthandoff: 02/22/2017

---
# <a name="source-control-configuration-details"></a>Detalhes de configuração de controle de origem
Para implementar o controle de origem, você precisa configurar corretamente o sistema do projeto ou o editor para fazer o seguinte:  
  
-   Solicitar permissão para fazer a transição de estado alterado  
  
-   Solicitar permissão para salvar um arquivo  
  
-   Solicitar permissão para adicionar, remover ou renomear arquivos do projeto  
  
## <a name="request-permission-to-transition-to-changed-state"></a>Solicitar permissão para fazer a transição de estado alterado  
 Um editor ou projeto deve solicitar permissão para fazer a transição para o estado de alteração (sujo) chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> Cada editor que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>deve chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>e receber aprovação para alterar o documento do ambiente antes de retornar `True` para `M:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty(System.Int32@)`.</xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> Um projeto é essencialmente um editor para um arquivo de projeto e tem como resultado, a responsabilidade mesmo para implementar o rastreamento de estado alterado para o arquivo de projeto como um editor de texto para seus arquivos. O ambiente manipula o estado alterado da solução, mas você deverá manipular o estado alterado de qualquer objeto na solução referencia, mas não armazena, como um arquivo de projeto ou seus itens. Em geral, se o projeto ou o editor é responsável por gerenciar a persistência de um item, é responsável por implementar o rastreamento de estado alterado.  
  
 Em resposta ao `IVsQueryEditQuerySave2::QueryEditFiles` chamar, o ambiente pode fazer o seguinte:  
  
-   Rejeitar a chamada para alterar, caso em que o editor ou o projeto deve permanecer no estado inalterado (limpo).  
  
-   Indica que os dados do documento devem ser recarregados. Para um projeto, o ambiente será recarregar os dados para o projeto. Um editor deverá recarregar os dados do disco por meio de seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>implementação.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> Em ambos os casos, o contexto do projeto ou o editor pode alterar quando os dados são recarregados.  
  
 É uma tarefa complexa e difícil fazer ajustes apropriados `IVsQueryEditQuerySave2::QueryEditFiles` chamadas em uma base de código existente. Como resultado, essas chamadas devem ser integradas durante a criação do projeto ou no editor.  
  
## <a name="request-permission-to-save-a-file"></a>Solicitar permissão para salvar um arquivo  
 Antes de um projeto ou editor salva um arquivo, ele deve chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> Para arquivos de projeto, essas chamadas são automaticamente preenchidas pela solução, que sabe quando salvar um arquivo de projeto. Editores são responsáveis por fazer essas chamadas, a menos que a implementação do editor de `IVsPersistDocData2` usa a função auxiliar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> Se seu editor implementar `IVsPersistDocData2` dessa maneira, a chamada para `IVsQueryEditQuerySave2::QuerySaveFile` ou `IVsQueryEditQuerySave2::QuerySaveFiles` é feita para você.  
  
> [!NOTE]
>  Sempre fazer essas chamadas preventivamente — ou seja, quando o editor for capaz de receber um cancelamento.  
  
## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Solicitar permissão para adicionar, remover ou renomear arquivos do projeto  
 Antes de um projeto pode adicionar, renomear ou remover um arquivo ou diretório, deve chamar o `IVsTrackProjectDocuments2::OnQuery*` método para solicitar permissão do ambiente. Se a permissão é concedida, o projeto deve concluir a operação e chamar o `IVsTrackProjectDocuments2::OnAfter*` método para notificar o ambiente de que a operação for concluída. O projeto deve chamar os métodos do <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>interface para todos os arquivos (por exemplo, arquivos especiais) e não apenas os arquivos pai.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> Chamadas de arquivo são obrigatórias, mas as chamadas de diretório são opcionais. Se o projeto tiver informações de diretório, ele deve chamar apropriado <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>métodos, mas se ele não tiver essas informações, o ambiente irá inferir informações de diretório.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
  
 O projeto não deve chamar os métodos de `IVsTrackProjectDocuments2` projeto abrir ou fechar. Ouvintes de que deseja que essas informações durante a inicialização podem aguardar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>eventos e percorrer a solução para localizar as informações necessárias.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> No fechamento, essas informações não são necessárias. `IVsTrackProjectDocuments2`é fornecido de <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>.</xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 Para cada adicionar, renomear e a ação de remover, há um `OnQuery*` método e um `OnAfter*` método. Chamar o `OnQuery*` método pedir permissão para adicionar, renomear ou remover o arquivo ou diretório. Chamar o `OnAfter*` método depois que o arquivo ou diretório foi adicionado, renomeado ou removido e o estado do projeto reflete o novo estado.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments></xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>   
 [Suporte a controle de origem](../../extensibility/internals/supporting-source-control.md)
