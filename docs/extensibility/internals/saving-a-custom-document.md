---
title: Salvando um documento personalizado | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
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
ms.openlocfilehash: a9ca3c67797b3ba47a0361ba4cdcff688070eb53
ms.lasthandoff: 02/22/2017

---
# <a name="saving-a-custom-document"></a>Salvando um documento personalizado
Os identificadores de ambiente a **salvar**, **Salvar como**, e **Salvar tudo** comandos. Quando um usuário clica **salvar**, **Salvar como**, **ou salvar tudo** sobre o **arquivo** menu ou fecha a solução, resultando em um Salvar tudo, o seguinte processo ocorre.  
  
 ![Salvar do Editor de cliente](~/extensibility/internals/media/private.gif "Private")  
Salvar, salvar como e salvar tudo manipulação de comando para um editor personalizado  
  
 Esse processo é detalhado nas etapas a seguir:  
  
1.  Para o **salvar** e **Salvar como** comandos, o ambiente usa o <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>de serviço para determinar a janela do documento ativo e, portanto, os itens devem ser salvos.</xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> Depois que a janela de documento ativa é conhecida, o ambiente localiza o ponteiro de hierarquia e o identificador de item (itemID) para o documento na tabela de documento em execução. Para obter mais informações, consulte [executando tabela Document](../../extensibility/internals/running-document-table.md).  
  
     Para o comando Salvar tudo, o ambiente usa as informações na tabela de documento em execução para compilar a lista de todos os itens para salvar.  
  
2.  Quando a solução recebe um <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>chamada, ele percorre o conjunto de itens selecionados (ou seja, as várias seleções expostas pelo <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>service).</xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>  
  
3.  Em cada item da seleção, a solução usa o ponteiro de hierarquia para chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A>método para determinar se o comando de menu Salvar deve ser habilitado.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> Se um ou mais itens estiverem incorretos, o comando Save está habilitado. Se a hierarquia usa um editor padrão, em seguida, os delegados de hierarquia consultando sujos status para o editor chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>  
  
4.  Em cada item selecionado está sujo, a solução usa o ponteiro de hierarquia para chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>método nas hierarquias apropriados.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>  
  
     No caso de um editor personalizado, a comunicação entre o objeto de dados de documentos e o projeto é particular. Assim, as preocupações de persistência especiais são manipuladas entre esses dois objetos.  
  
    > [!NOTE]
    >  Se você implementar sua própria persistência, certifique-se de chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>método para economizar tempo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> Esse método verifica para ter certeza de que é seguro salvar o arquivo (por exemplo, o arquivo não é somente leitura).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Abrindo e salvando itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md)
