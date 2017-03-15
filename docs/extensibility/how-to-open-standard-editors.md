---
title: "Como: abrir editores padrão | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
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
ms.openlocfilehash: 17894f9e8f0eee9c88203587da554509ce856fac
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-open-standard-editors"></a>Como: abrir editores padrão
Quando você abre um editor padrão, deixar o IDE determinar um editor padrão para um tipo de arquivo designado, em vez de especificar um editor específicas do projeto para o arquivo.  
  
 Conclua o procedimento a seguir para implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> Isso abrirá um arquivo de projeto em um editor padrão.  
  
### <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>Para implementar o método OpenItem com um editor padrão  
  
1.  Chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>(`RDT_EditLock`) para determinar se o arquivo de objeto de dados de documento já está aberto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>  
  
2.  Se o arquivo já estiver aberto, repavimentar o arquivo chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>método, especificando um valor de `IDO_ActivateIfOpen` para o `grfIDO` parâmetro.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>  
  
     Se o arquivo está aberto e o documento é de propriedade de um projeto diferente do projeto de chamada, o projeto recebe um aviso de que o editor está sendo aberto é de outro projeto. A janela de arquivo, em seguida, é exibida.  
  
3.  Se o documento não está aberto ou não na tabela de documento em execução, chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>método (`OSE_ChooseBestStdEditor`) para abrir um editor padrão para o arquivo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>  
  
     Quando você chama o método, o IDE executa as seguintes tarefas:  
  
    1.  O IDE examina os editores / {guidEditorType} subchave extensões no registro para determinar o editor pode abrir o arquivo e tem a prioridade mais alta para fazer isso.  
  
    2.  Depois que o IDE determina qual editor pode abrir o arquivo, o IDE chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Implementação do editor deste método retorna informações necessárias para o IDE chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>e site do documento recém-aberta.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>  
  
    3.  Por fim, o IDE carrega o documento usando a interface de persistência usuais, como <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>  
  
    4.  Se o IDE anteriormente determinou que a hierarquia ou um item de hierarquia está disponível, o IDE chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A>método no projeto para obter um contexto de nível de projeto <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>ponteiro passar novamente com o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>chamada de método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> </xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A>  
  
4.  Retornar um <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>ponteiro para o IDE quando o IDE chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A>em seu projeto se você quiser permitir que o contexto de get de editor do seu projeto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>  
  
     Executar esta etapa permite que os serviços adicionais de oferta de projeto para o editor.  
  
     Se a exibição de documento ou um objeto de exibição de documento com êxito foi colocado em um quadro de janela, o objeto é inicializado com seus dados chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider></xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Abrindo e salvando itens de projeto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Como: abrir editores específicos do projeto](../extensibility/how-to-open-project-specific-editors.md)   
 [Como: abrir editores para documentos abertos](../extensibility/how-to-open-editors-for-open-documents.md)   
 [Exibindo arquivos usando o comando Abrir arquivo](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
