---
title: "Gerenciamento de proprietário de bloqueio de documentos | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: 21
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
ms.openlocfilehash: a78ee74a210f544ad4f9d97a9d2457bdf9d70988
ms.lasthandoff: 02/22/2017

---
# <a name="document-lock-holder-management"></a>Gerenciamento de proprietário de bloqueio de documento
A tabela de documento em execução (RDT) mantém uma contagem de documentos abertos e todos eles têm os bloqueios editar. Você pode colocar um bloqueio de edição em um documento de RDT quando é editado por meio de programação em segundo plano sem que o usuário ver um documento aberto em uma janela de documento. Essa funcionalidade é frequentemente usada por designers que modificar vários arquivos através de uma interface gráfica do usuário.  
  
## <a name="document-lock-holder-scenarios"></a>Cenários de proprietário de bloqueio de documento  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>Arquivo de "a" uma dependência no arquivo tem "b"  
 Considere uma situação em que você implementar um editor padrão "A" tipo de arquivo "a" e cada arquivo do tipo "a" tem uma referência a (ou dependência) de um arquivo do tipo "b". Existe um editor padrão "B" para arquivos do tipo "b". Quando o editor "A" abre o arquivo "r" recupera a referência para o arquivo correspondente "b". O arquivo "b" não é exibido, mas "A" editor pode modificá-lo. Editor de "A" obtém uma referência aos dados de documento do arquivo "b" do <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>método e também mantém um bloqueio de edição no arquivo "b".</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> Depois que o editor "A" é feito modificando o arquivo "b", você pode diminuir o bloqueio de edição contagem no arquivo "b" chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> Você pode pular essa etapa se você tivesse chamado o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>método com o parâmetro `dwRDTLockType` definida como <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> </xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>O arquivo "b" é aberto por um Editor diferente  
 Se o arquivo "b" já está aberto pelo editor "B" quando "A" editor tenta abri-lo, há dois cenários separados para lidar com:  
  
-   Se o arquivo "b" está aberto em um editor compatível, você deve ter um"editor" registrar um bloqueio de edição de documento no arquivo "b" usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> Depois que o editor de "A" é feito modificando arquivo "b", cancele o registro do documento editar bloqueio usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A>  
  
-   Se o arquivo "b" está aberto em um modo incompatível, você também pode deixar a tentativa abertura de arquivo "b" por "A" falhar, ou você pode deixar a exibição associada ao editor "A" parcialmente abre e exibe uma mensagem de erro apropriada do editor. A mensagem de erro deve instruir o usuário fechar o arquivo "b" no editor incompatível e abra novamente o arquivo usando o "a" editor "A". Você também pode implementar o [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] método <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A>para avisar o usuário fechar o arquivo "b" que é aberto no editor incompatível.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> Se o usuário fechar o arquivo "b", a abertura de arquivo "a" no editor "A" continua normalmente.  
  
## <a name="additional-document-edit-lock-considerations"></a>Considerações de bloqueio de editar documentos adicionais  
 Você receberá um comportamento diferente se o editor "A" é o único editor que tem um documento editar bloqueio no arquivo "b" do que o editor "B" também contém um documento editar bloqueio no arquivo "b". Em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], **Class Designer** é um exemplo de um designer visual que não possui um bloqueio de editar o arquivo de código associado. Ou seja, se o usuário abriu um diagrama de classe no modo de design e o arquivo de código associado abertos simultaneamente, e se o usuário modifica o arquivo de código, mas não salvar as alterações, as alterações também são perdidas ao arquivo de diagrama (. CD) da classe. Se o **Class Designer** tem o documento apenas editar bloqueio no arquivo de código, o usuário não é solicitado a salvar as alterações ao fechar o arquivo de código. O IDE pede ao usuário para salvar as alterações somente depois que o usuário fecha o **Class Designer**. As alterações salvas são refletidas em ambos os arquivos. Se o **Class Designer** e o editor de arquivo de código mantido bloqueios de edição do documento no arquivo de código, em seguida, o usuário é solicitado a salvar ao fechar o arquivo de código ou o formulário. Nesse ponto, as alterações salvas são refletidas no formulário e o arquivo de código. Para obter mais informações sobre diagramas de classe, consulte [trabalhando com diagramas de classe (Designer de classe)](../ide/working-with-class-diagrams-class-designer.md).  
  
 Observe que se você precisa colocar um bloqueio de edição em um documento para um editor não, você deve implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>  
  
 Muitas vezes um interface do usuário designer que modifica os arquivos de código por meio de programação faz alterações em mais de um arquivo. Nesses casos o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A>método manipula o salvamento de um ou mais documentos por meio do **você deseja salvar as alterações para os seguintes itens?** caixa de diálogo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A>  
  
## <a name="see-also"></a>Consulte também  
 [Tabela de documento em execução](../extensibility/internals/running-document-table.md)   
 [A tabela de documento em execução e persistência](../extensibility/internals/persistence-and-the-running-document-table.md)
