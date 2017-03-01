---
title: Suporte do Assistente para projetos aninhados | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
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
ms.openlocfilehash: 2e7a381df4ed26379978e18a6c446bc56b582353
ms.lasthandoff: 02/22/2017

---
# <a name="wizard-support-for-nested-projects"></a>Suporte do Assistente para projetos aninhados
O IDE executa dois assistentes que pode implementar o projeto pai para projetos aninhados: o **novo projeto** assistente e o **Adicionar Item** assistente.  
  
 Se um usuário inicia o **novo projeto** assistente selecionando **Adicionar projeto** e clicando em **novo projeto** no menu arquivo ou selecionando **adicionar** e clicando com o botão **novo projeto** no Solution Explorer, o IDE executa o **AddProject** comando e implementação do projeto pai o **AddProject** comando retorna um arquivo de modelo de projeto ou um arquivo do assistente (. vsz) que tem um conjunto de parâmetros de contexto.  
  
 Da mesma forma, a implementação do projeto pai de **AddItem** assistentes retorna um arquivo. vsz que tem um conjunto diferente de parâmetros de contexto.  
  
 Para obter mais informações sobre assistentes, consulte [Assistente (. Arquivo vsz)](../../extensibility/internals/wizard-dot-vsz-file.md), [parâmetros de contexto](../../extensibility/internals/context-parameters.md) e [registro de modelos de projeto e Item](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Projetos de aninhamento](../../extensibility/internals/nesting-projects.md)
