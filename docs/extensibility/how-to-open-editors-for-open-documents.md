---
title: 'Como: abrir editores para documentos abertos | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
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
ms.openlocfilehash: 326d82b0abb6e6bfbaf9e0757a7f2bfb6be10748
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-open-editors-for-open-documents"></a>Como: abrir editores para documentos abertos
Antes de um projeto é aberto em uma janela de documento, o projeto primeiro deve determinar se o arquivo já está aberto na janela do documento para outro editor. O arquivo pode ser abra em um editor específico do projeto ou um dos editores padrão registrado com [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="opening-a-project-specific-editor"></a>Abrindo um Editor específico do projeto  
 Use o procedimento a seguir para abrir um editor específicas do projeto para um arquivo que já está aberto.  
  
#### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Para abrir um editor específicas do projeto para um arquivo aberto  
  
1.  Chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>  
  
     Essa chamada retorna ponteiros para a hierarquia do documento, item de hierarquia e quadro de janela, se apropriado.  
  
2.  Se o documento for aberto, o projeto deve verificar se existe apenas um objeto de dados de documento, ou se um objeto de exibição de documento também está presente.  
  
    -   Se existe um objeto de exibição de documento, e essa exibição é para um item de hierarquia ou uma hierarquia diferente, o projeto usa o ponteiro para o quadro de janela do modo de exibição para repavimentar janela existente.  
  
    -   Se existe um objeto de exibição de documento, e esse modo de exibição é para a mesma hierarquia e o item de hierarquia, o projeto pode abrir uma segunda exibição se pode conectar-se ao objeto de dados subjacente do documento. Caso contrário, o projeto deve usar o ponteiro para o quadro de janela do modo de exibição para repavimentar janela existente.  
  
    -   Se o objeto de dados de documento existe, apenas o projeto deve determinar se ele pode usar o objeto de dados de documento para o modo de exibição. Se o objeto de dados de documento for compatível, concluir as etapas discutidas em [abrindo um Editor específico do projeto](../extensibility/how-to-open-project-specific-editors.md).  
  
     Se o objeto de dados de documento não for compatível, um erro deve ser exibido ao usuário que indica que o arquivo está em uso. Esse erro só deve ser exibido na transitórios casos, como quando um arquivo está sendo compilado ao mesmo tempo o usuário está tentando abrir o arquivo usando um editor diferente de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor de texto principal. O editor de texto principal pode compartilhar o objeto de dados de documento com o compilador.  
  
3.  Se o documento não estiver aberto, porque não há nenhum objeto de dados de documento ou o objeto de exibição de documento, conclua as etapas na [abrindo um Editor específico do projeto](../extensibility/how-to-open-project-specific-editors.md).  
  
## <a name="opening-a-standard-editor"></a>Abrindo um Editor padrão  
 Use o procedimento a seguir para abrir um editor padrão para um arquivo que já está aberta.  
  
#### <a name="to-open-a-standard-editor-for-an-open-file"></a>Para abrir um editor padrão para um arquivo aberto  
  
1.  Chamada <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>  
  
     Esse método primeiro verifica se o documento não estiver aberto, chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> Se o documento já estiver aberto, sua janela de editor é resurfaced.  
  
2.  Se o documento não estiver aberto, em seguida, conclua as etapas na [como: abrir editores padrão](../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Consulte também  
 [Abrindo e salvando itens de projeto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Como: abrir editores específicos do projeto](../extensibility/how-to-open-project-specific-editors.md)   
 [Como: abrir editores padrão](../extensibility/how-to-open-standard-editors.md)
