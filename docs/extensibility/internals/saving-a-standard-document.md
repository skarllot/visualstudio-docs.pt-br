---
title: "Salvar um documento padrão | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
caps.latest.revision: 8
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
ms.openlocfilehash: a11da1bf8ff2b0637de967be56cec07190006baf
ms.lasthandoff: 02/22/2017

---
# <a name="saving-a-standard-document"></a>Salvar um documento padrão
O ambiente manipula a salvar, salvar como e salvar todos os comandos. Quando um usuário seleciona **salvar**, **Salvar como**, ou **Salvar tudo** do **arquivo** menu ou fecha a solução, resultando em uma **Salvar tudo**, o seguinte processo ocorre.  
  
 ![Editor padrão](../../extensibility/internals/media/public.gif "Public")  
Salvar, salvar como e salvar tudo manipulação de comando para um editor padrão  
  
 Esse processo é detalhado nas etapas a seguir:  
  
1.  Quando o **salvar** e **Salvar como** comandos são selecionados, o ambiente usa o <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>de serviço para determinar a janela do documento ativo e, portanto, os itens devem ser salvos.</xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> Depois que a janela de documento ativa é conhecida, o ambiente localiza o ponteiro de hierarquia e o identificador de item (itemID) para o documento na tabela de documento em execução. Para obter mais informações, consulte [executando tabela Document](../../extensibility/internals/running-document-table.md).  
  
     Quando o **Salvar tudo** comando estiver marcado, o ambiente usa as informações na tabela de documento em execução para compilar a lista de todos os itens para salvar.  
  
2.  Quando a solução recebe um <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>chamada, ele percorre o conjunto de itens selecionados (ou seja, as várias seleções expostas pelo <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>service).</xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>  
  
3.  Em cada item da seleção, a solução usa o ponteiro de hierarquia para chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A>método para determinar se o **salvar** menu comando deve ser habilitado.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> Se um ou mais itens estiverem incorreto, o **salvar** comando está habilitado. Se a hierarquia usa um editor padrão, em seguida, os delegados de hierarquia consultando sujos status para o editor chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>  
  
4.  Em cada item selecionado está sujo, a solução usa o ponteiro de hierarquia para chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>método nas hierarquias apropriados.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>  
  
     É comum para a hierarquia usando um editor padrão para editar o documento. Nesse caso, os dados do documento de objeto para esse editor deve oferecer suporte a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> Ao receber o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>chamada de método, o projeto deve informar o editor que o documento está sendo salva chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A>método no objeto de dados de documento.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> O editor pode permitir que o ambiente manipular o **Salvar como** caixa de diálogo, chamando `Query Service` para o <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>interface.</xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> Isso retorna um ponteiro para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> O editor deve chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>método, transmitindo um ponteiro para o editor <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>implementação por meio do `pPersistFile` parâmetro.</xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> O ambiente, em seguida, executa a operação de salvamento e fornece o **Salvar como** caixa de diálogo do editor. O ambiente, em seguida, chama de volta para o editor com <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.</xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>  
  
5.  Se o usuário está tentando salvar um documento sem título (ou seja, um documento que não foram salvo anteriormente), um comando Salvar como, na verdade, é executado.  
  
6.  Para o comando Salvar como, o ambiente exibe a caixa de diálogo Salvar como, solicitando ao usuário um nome de arquivo.  
  
     Se o nome do arquivo foi alterado, a hierarquia é responsável por atualizar o quadro do documento informações armazenadas em cache chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>(VSFPROPID_MkDocument).</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>  
  
 Se o **Salvar como** comando move o local do documento e a hierarquia é dependem da localização do documento, a hierarquia é responsável por entregando a propriedade da janela do documento aberto para outra hierarquia. Por exemplo, isso ocorre se o projeto controla se o arquivo é um arquivo (arquivo diverso) interno ou externo em relação ao projeto. Use o procedimento a seguir para alterar a propriedade de um arquivo para o projeto de arquivos diversos.  
  
## <a name="changing-file-ownership"></a>Alterando a propriedade de arquivo  
  
#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Para alterar a propriedade de arquivo para o projeto de arquivos diversos  
  
1.  Consultar o serviço para o <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager>interface.</xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager>  
  
     Um ponteiro para <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2>é retornado.</xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2>  
  
2.  Chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A>(`pszMkDocumentNew`, `punkWindowFrame`) para transferir o documento para a nova hierarquia.</xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> A hierarquia de executar o comando Salvar como chama esse método.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Abrindo e salvando itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md)
