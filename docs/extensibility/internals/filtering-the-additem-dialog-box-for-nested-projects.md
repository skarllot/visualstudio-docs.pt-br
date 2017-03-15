---
title: "A caixa de diálogo AddItem de filtragem para projetos aninhados | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
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
ms.openlocfilehash: c70e13c61386f6dd112740897901501118260e57
ms.lasthandoff: 02/22/2017

---
# <a name="filtering-the-additem-dialog-box-for-nested-projects"></a>A caixa de diálogo AddItem de filtragem para projetos aninhados
Quando você exibe um **AddItem** caixa de diálogo para um projeto aninhado, o projeto pai pode controlar quais itens são exibidos na caixa de diálogo.  
  
 O <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>interface permite filtrar os nós que estarão em um **AddItem** caixa de diálogo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> Quando o projeto filho exibe o **AddItem** caixa de diálogo, o pai pode implementar o `IVsFilterAddProjectItemDlg` interface e filtrar itens que outra forma seriam exibidos no projeto do filho.  
  
 Quando os projetos são agrupados por função em projetos pai específico, você pode implementar `IVsFilterAddProjectItemDlg` quando o usuário seleciona **Adicionar Item de projeto** no menu de atalho em um projeto aninhado. Implementando `IvsFilterAddProjectItemDlg displays` projeto somente itens ou arquivos específico para esse grupo. Itens de projeto para outros grupos são filtradas fora da caixa de diálogo, mesmo se eles estiverem armazenados no mesmo diretório.  
  
 Quando um usuário abre o **AddItem** filho, a implementação do projeto pai da caixa de diálogo de `IVsFilterAddProjectItemDlg` interface é chamada.  
  
 O `IVsFilterAddProjectItemDlg` interface também pode implementar a filtragem por categoria. Para obter mais informações, consulte [a adição de itens para as caixas de diálogo Adicionar Novo Item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) e [registro de modelos de projeto e Item](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2></xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Adicionando itens a adicionar novo Item caixas de diálogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Registrando o projeto e modelos de Item](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Projetos de aninhamento](../../extensibility/internals/nesting-projects.md)
