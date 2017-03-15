---
title: Prioridade do projeto | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
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
ms.openlocfilehash: 670aa77d5976bbb0188d1d15bce3600e1c055ac9
ms.lasthandoff: 02/22/2017

---
# <a name="project-priority"></a>Prioridade do projeto
Um item de projeto geralmente é um membro de apenas um projeto na solução. Portanto, o IDE pode determinar facilmente qual projeto é usado para abrir o item. No entanto, se um item for um membro de mais de um projeto, o IDE usa um esquema de prioridade para determinar o melhor projeto para abrir o item.  
  
 A lista a seguir mostra o esquema de prioridades do projeto:  
  
-   O IDE chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A>método para cada projeto na solução para determinar se o documento é um membro desse projeto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A>  
  
-   Se o documento for um membro do projeto, o projeto responde com uma prioridade que o project atribui acordo com o manuseio de documento. Por exemplo, um projeto de linguagem responde com uma prioridade alta para seus arquivos de origem de linguagem, mas responde com uma prioridade mais baixa para um tipo de arquivo não reconhecido que não é usado como parte de seu processo de compilação.  
  
-   Projetos que oferecem designers ou editores personalizados, específicos do projeto para um documento também recebem uma prioridade alta.  
  
-   O <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>enumeração fornece o documento de valores de prioridade.</xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>  
  
-   O projeto que especifica a prioridade mais alta recebe o contexto para abrir o documento. Se dois projetos retornam valores de prioridade igual, o projeto ativo é preferencial. Se nenhum projeto na solução responde que ele pode abrir o documento, o IDE coloca o documento no projeto de arquivos diversos. Para obter mais informações, consulte [diversos arquivos de projeto](../../extensibility/internals/miscellaneous-files-project.md).  
  
## <a name="see-also"></a>Consulte também  
 [Projeto de arquivos diversos](../../extensibility/internals/miscellaneous-files-project.md)   
 [Como: abrir editores para documentos abertos](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [Adicionando o projeto e modelos de Item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)
