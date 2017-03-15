---
title: Determinando qual Editor abre um arquivo em um projeto | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: 10
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
ms.openlocfilehash: ac16b6f4d8429d328cfd76b8b02cd1620f4a4294
ms.lasthandoff: 02/22/2017

---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>Determinando qual Editor abre um arquivo em um projeto
Quando um usuário abre um arquivo em um projeto, o ambiente passa por um processo de pesquisa, eventualmente abrindo o editor apropriado ou o designer para esse arquivo. O procedimento inicial empregado pelo ambiente é o mesmo para editores padrão e personalizadas. O ambiente usa uma variedade de critérios ao sondar o editor a ser usado para abrir um arquivo e o VSPackage deve coordenar com o ambiente durante esse processo.  
  
 Por exemplo, quando um usuário seleciona o **abrir** comando o **arquivo** menu e escolhe `filename`. rtf (ou qualquer outro arquivo com uma extensão. rtf), o ambiente chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>implementação para cada projeto, eventualmente percorrer todas as instâncias de projeto na solução.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Projetos retornam um conjunto de sinalizadores que identificam as declarações em um documento por prioridade. Usando a prioridade mais alta, o ambiente chama apropriado <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> Para obter mais informações sobre o processo de sondagem, [Adicionar projeto e modelos de Item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 O projeto de arquivos diversos declarações de todos os arquivos que não são reclamados por outros projetos. Dessa forma, editores personalizados podem abrir documentos antes de editores padrão abri-los. Se um arquivo de declarações de um projeto de arquivos diversos, o ambiente chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>método para abrir o arquivo com um editor padrão.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> O ambiente verifica sua lista interna de editores registrados para um que manipula arquivos. rtf. Essa lista está localizada no registro na seguinte chave:  
  
 [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<`version`> \Editors\\{`editor factory guid`>} \Extensions]  
  
 Os identificadores de classe na chave HKEY_CLASSES_ROOT\CLSID para todos os objetos que têm uma subchave DocObject também verifica se o ambiente. Se a extensão de arquivo for encontrada lá, uma versão incorporada do aplicativo, como o Microsoft Word, é criada no local no Visual Studio. Esses objetos de documento devem ser compostos arquivos que implementam o <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>interface ou o objeto deve implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> </xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>  
  
 Se não houver nenhuma fábrica de editor para arquivos. rtf no registro, o ambiente examina o HKEY_CLASSES_ROOT \\chave. rtf e abre o editor especificado não existe. Se a extensão de arquivo não for encontrada em HKEY_CLASSES_ROOT, o ambiente usa o editor de texto de núcleo do Visual Studio para abrir o arquivo se ele for um arquivo de texto.  
  
 Se o editor de texto principal falhar, o que ocorre que se o arquivo não é um arquivo de texto, em seguida, o ambiente usa o editor binário para o arquivo.  
  
 Se o ambiente de encontrar um editor para a extensão. RTF em seu registro, ele carrega o VSPackage que implementa essa fábrica de editor. O ambiente chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>método no novo VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> As chamadas de VSPackage `QueryService` para `SID_SVsRegistorEditor`, usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>método para registrar a fábrica do editor com o ambiente.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>  
  
 O ambiente agora verifica novamente sua lista interna de editores registrados para localizar a fábrica do editor registrado recentemente para arquivos. rtf. O ambiente chama a implementação do <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>método, passando no tipo de exibição e de nome de arquivo para criar.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat></xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage></xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
