---
title: "Implementar manipulação de comando para projetos de aninhado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
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
ms.openlocfilehash: b648ef0381701350f46f4695f214c6ee8c9f32e7
ms.lasthandoff: 02/22/2017

---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementar manipulação de comando para projetos aninhados
O IDE pode passar os comandos que são passados para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>e o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interfaces para projetos aninhados ou projetos pai podem filtrar ou substituir os comandos.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>  
  
> [!NOTE]
>  Somente os comandos que normalmente é tratados pelo projeto pai podem ser filtrados. Comandos como **criar** e **implantar** que são manipuladas pelo IDE não pode ser filtrado.  
  
 As etapas a seguir descrevem o processo de implementação de manipulação de comandos.  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="to-implement-command-handling"></a>Para implementar o tratamento de comando  
  
1.  Quando o usuário seleciona um projeto aninhado ou um nó em um projeto aninhado:  
  
    1.  O IDE chama o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>método.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>  
  
     – ou —  
  
    1.  Se o comando tiver sido originado em uma janela de hierarquia, como um comando de menu de atalho no Solution Explorer, o IDE chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>método pai do projeto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>  
  
2.  O projeto pai pode examinar os parâmetros a serem passados para `QueryStatus`, como `pguidCmdGroup` e `prgCmds`, para determinar se o projeto pai deve filtrar os comandos. Se o projeto pai é implementado para comandos de filtragem, ele deve definir:  
  
    ```  
    prgCmds[0].cmdf = OLECMDF_SUPPORTED;  
    // make sure it is disabled  
    prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;  
    ```  
  
     Em seguida, o projeto pai deve retornar `S_OK`.  
  
     Se o projeto pai não filtrar o comando, ele deve simplesmente retornar `S_OK`. Nesse caso, o IDE roteia automaticamente o comando para o projeto filho.  
  
     O projeto pai não tem que rotear o comando para o projeto filho. O IDE executa essa tarefa.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Barras de ferramentas, Menus e comandos](../../extensibility/internals/commands-menus-and-toolbars.md)   
 [Projetos de aninhamento](../../extensibility/internals/nesting-projects.md)
