---
title: "Como: abrir editores específicos do projeto | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
caps.latest.revision: 13
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
ms.openlocfilehash: 3414888c213567389f504a1c173b7dd154e81de0
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-open-project-specific-editors"></a>Como: abrir editores específicos do projeto
Se um arquivo de item está sendo aberto por um projeto é intrinsecamente associado ao editor específico para o projeto, o projeto deve abrir o arquivo usando um editor específico do projeto. O arquivo não pode ser delegado para o mecanismo do IDE para a seleção de um editor. Por exemplo, em vez de usar um editor de bitmap padrão, você pode usar essa opção de editor específicas do projeto para especificar um editor específico de bitmap que reconhece as informações no arquivo que é exclusivo ao seu projeto.  
  
 O IDE chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>método quando ele determina se um arquivo deve ser aberto por um projeto específico.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> Para obter mais informações, consulte [exibindo arquivos usando o comando Abrir do arquivo](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Use as diretrizes a seguir para implementar o `OpenItem` método para que o projeto abrir um arquivo usando um editor específico do projeto.  
  
### <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>Para implementar o método OpenItem com um editor específico do projeto  
  
1.  Chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>método (RDT_EditLock) para determinar se o arquivo (objeto de dados de documento) já está aberto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>  
  
    > [!NOTE]
    >  Para obter mais informações sobre dados de documentos e objetos de exibição de documento, consulte [dados de documentos e visualização de documentos em editores personalizados](../extensibility/document-data-and-document-view-in-custom-editors.md).  
  
2.  Se o arquivo já estiver aberto, repavimentar o arquivo chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>método e especificando um valor de IDO_ActivateIfOpen para o `grfIDO` parâmetro.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>  
  
     Se o arquivo está aberto e o documento é de propriedade de um projeto que não seja o projeto de chamada, um aviso será exibido para o usuário que o editor está sendo aberto é de outro projeto. A janela de arquivo, em seguida, é exibida.  
  
3.  Se o buffer de texto (objeto de dados de documento) já está aberto e você deseja anexar outro modo de exibição a ele, você é responsável por conectar esse modo de exibição. A abordagem recomendada para instanciar um modo de exibição (objeto de exibição de documento) do projeto, é o seguinte:  
  
    1.  Chamar `QueryService` sobre o <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry>para obter um ponteiro para o <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2>interface.</xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> </xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry>  
  
    2.  Chame o <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>método para criar uma instância da classe de exibição do documento</xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>  
  
4.  Chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>método, especificando o objeto de exibição do documento.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>  
  
     Esse método sites o objeto de exibição de documento em uma janela de documento.  
  
5.  Executar as chamadas apropriadas como o <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A>ou o <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A>métodos.</xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A>  
  
     Neste ponto, o modo de exibição deve ser totalmente inicializado e está pronto para ser aberto.  
  
6.  Chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>método para exibir e abrir o modo de exibição.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>  
  
## <a name="see-also"></a>Consulte também  
 [Abrindo e salvando itens de projeto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Como: abrir editores padrão](../extensibility/how-to-open-standard-editors.md)   
 [Como: abrir editores para documentos abertos](../extensibility/how-to-open-editors-for-open-documents.md)
