---
title: Projeto de arquivos diversos | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
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
ms.openlocfilehash: 4b51edb690fe279a3f37cb2d40b72af81d9dcce6
ms.lasthandoff: 02/22/2017

---
# <a name="miscellaneous-files-project"></a>Projeto de arquivos diversos
Quando um usuário abre itens de projeto, o IDE atribui ao projeto de arquivos diversos todos os itens que não são membros de quaisquer projetos em uma solução.  
  
 Projetos desempenham um papel importante na determinação de qual editor é usado quando um usuário abre um item de projeto. Um projeto pode ser criado para abrir determinados arquivos usando um editor específico do projeto ou um editor padrão.  
  
 Um editor específico do projeto normalmente requer que o usuário tivesse conhecimento especial ou usar interfaces especial do projeto. Para obter mais informações, consulte [como: abrir editores específicos do projeto](../../extensibility/how-to-open-project-specific-editors.md).  
  
 Um editor padrão pode abrir qualquer arquivo com uma extensão específica em qualquer projeto. O usuário pode personalizar alguns editores padrão, como o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editor de texto, para projetos mas ainda manter seus caracteres pública. Editores padrão são criadas usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>  
  
 Se nenhum projeto na solução responde que ele possa abrir um item de projeto, o IDE fornece um projeto especial chamado projeto de arquivos diversos que abre qualquer arquivo.  
  
 Esse projeto especial possibilita a abertura de um arquivo fora do contexto de um projeto. Durante o processamento de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A>método, o projeto de arquivos diversos sempre responde com uma prioridade muito baixa.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> Portanto, os arquivos diversos projeto sempre produz a qualquer projeto de prioridade mais alta que possa abrir arquivos.  
  
 O projeto de arquivos diversos requer que o usuário explicitamente criá-lo com o **novo projeto** caixa de diálogo. Além disso, o projeto de arquivos diversos não gerencia permanentemente uma lista de membros do projeto. Ele usa um recurso opcional para registrar uma lista dos arquivos usados mais recentemente para cada usuário.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY></xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [Como: abrir editores específicos do projeto](../../extensibility/how-to-open-project-specific-editors.md)   
 [Como: abrir editores padrão](../../extensibility/how-to-open-standard-editors.md)   
 [Adicionando o projeto e modelos de Item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Adicionando o projeto e modelos de Item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)
