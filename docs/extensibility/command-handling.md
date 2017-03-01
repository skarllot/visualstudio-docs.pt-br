---
title: Tratamento de comandos | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: 20
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
ms.openlocfilehash: 5a58c6ee650728f01b00e892ddb788b6cb67e0ad
ms.lasthandoff: 02/22/2017

---
# <a name="command-handling"></a>Tratamento de comandos
O editor pode definir novos comandos. Normalmente, os comandos são exibidos em um menu em uma barra de ferramentas ou em um menu de contexto.  
  
 Para obter mais informações sobre como definir os menus e comandos, consulte [comandos, Menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Um serviço de linguagem pode controlar quais menus de contexto são mostrados no editor, interceptando o <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>enumeração.</xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Como alternativa, você pode controlar o menu de contexto em uma base por marcador. Para obter mais informações, consulte [comandos importantes para filtros de serviço de linguagem](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>Adicionar comandos ao Menu de contexto do Editor  
 Para adicionar um comando no menu de contexto, você deve primeiro definir um conjunto de comandos de menu que pertencem a um grupo específico. O exemplo a seguir é retirado do arquivo. VSCT gerado como parte do passo a passo [passo a passo: adicionando recursos a um Editor personalizado](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Menu guid = "guidCustomEditorCmdSet" id = "IDMX_RTF" prioridade = "0x0000" type = "Contexto" >  
  
 \<Guid do pai = "guidCustomEditorCmdSet" id = "0" / >  
  
 \<Cadeias de caracteres >  
  
 \<ButtonText > Menu de contexto CustomEditor\</ButtonText >  
  
 \<CommandName > CustomEditorContextMenu\</CommandName >  
  
 \</ Cadeias de caracteres >  
  
 \</ Menu >  
  
 \</ Menus >  
  
 O texto acima adiciona um comando de menu de contexto com o texto **o Menu de contexto CustomEditor**. O GUID do Menu é que o conjunto de comando que é criado com este editor e o tipo é "Contexto".  
  
 Você também pode usar comandos predefinidos que não precisam ser definidos no arquivo. VSCT. Por exemplo, se você examinar o arquivo EditorPane.cs gerado pelo modelo do pacote do Visual Studio, verá que um conjunto de comandos predefinidos, como <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID>definido por <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, são tratados em manipuladores de comandos, como o método onSelectAll.</xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> </xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID>  
  
## <a name="see-also"></a>Consulte também  
 [Barras de ferramentas, Menus e comandos](../extensibility/internals/commands-menus-and-toolbars.md)
