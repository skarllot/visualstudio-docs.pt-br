---
title: Exibindo arquivos usando o abrir com o comando | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
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
ms.openlocfilehash: a266d33679068b4a5d0513216520bbba44a43b33
ms.lasthandoff: 02/22/2017

---
# <a name="displaying-files-by-using-the-open-with-command"></a>Exibindo arquivos usando o abrir com o comando
Um projeto pode solicitar que o IDE para exibir o **abrir com** caixa de diálogo. Essa solicitação solicita ao usuário para abrir um arquivo que tenha uma seleção de editores padrão. As etapas a seguir descrevem esse processo.  
  
1.  As chamadas de projeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, especificando um valor de OSE_UseOpenWithDialog para o `OSEOpenDocEditor` parâmetro.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>  
  
2.  Com base na extensão de nome de arquivo do documento, o IDE determina quais editores listados no podem registro abrem o documento especificado e exibe essas informações no **abrir com** caixa de diálogo.  
  
    > [!NOTE]
    >  Projetos que têm um editor intrínseco que deve ser incluído no **abrir com** caixa de diálogo deve registrar uma fábrica de editor para cada esse editor. Editores intrínsecos só funcionam junto com um determinado tipo de projeto, que é aplicado na implementação do <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> O IDE tem uma fábrica de editor interno para o editor de texto principal e o editor binário. O IDE também cria uma instância de uma fábrica de editor em nome de cada associação de arquivo registrada do Windows. Um exemplo desse tipo de arquivo é o Microsoft Word.  
  
3.  Assim que o usuário seleciona um item do **abrir com** caixa de diálogo, em seguida, o IDE abre o documento chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Para obter mais informações, consulte [como: abrir editores padrão](../../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Consulte também  
 [Abrindo e salvando itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Exibindo arquivos usando o comando Abrir arquivo](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [Como: abrir editores padrão](../../extensibility/how-to-open-standard-editors.md)
