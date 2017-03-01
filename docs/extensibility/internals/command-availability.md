---
title: Comando disponibilidade | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: 34
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
ms.openlocfilehash: 08f8266d0cb85c18087f7323c0b5e702f5280349
ms.lasthandoff: 02/22/2017

---
# <a name="command-availability"></a>Disponibilidade de comando
O contexto do Visual Studio determina quais comandos estão disponíveis. O contexto pode mudar dependendo do projeto atual, o editor atual, os VSPackages são carregados e outros aspectos do ambiente de desenvolvimento integrado (IDE).  
  
## <a name="command-contexts"></a>Contextos de comando  
 Os contextos de comando a seguir são as mais comuns.  
  
-   **IDE** comandos fornecidos pelo IDE estão sempre disponíveis.  
  
-   **VSPackage** VSPackages pode definir quando comandos devem ser exibidos ou ocultados.  
  
-   **Projeto** projeto comandos aparecem somente para o projeto selecionado no momento.  
  
-   **Editor de** editor apenas uma pode estar ativo por vez. Comandos do editor ativo estão disponíveis. Um editor trabalha junto com um serviço de linguagem. O serviço de linguagem deve processar os comandos no contexto do editor associado.  
  
-   **Tipo de arquivo** um editor pode carregar mais de um tipo de arquivo. Os comandos disponíveis podem mudar dependendo do tipo de arquivo.  
  
-   **Janela ativa** a última janela do documento ativo define o contexto de interface do usuário para associações de teclas. No entanto, uma janela de ferramenta que tem uma tabela de associação de chave que se parece com o navegador da Web interno também pode definir o contexto de interface do usuário. Para janelas de documento com várias guias, como o editor de HTML, cada guia tem um contexto diferente do comando GUID. Depois que uma janela de ferramentas é registrada, ele estará sempre disponível no **exibição** menu.  
  
-   **Contexto de interface do usuário** contextos de interface do usuário são identificados pelos valores da <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>classe, por exemplo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionBuilding>quando a solução está sendo criada, ou <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Debugging>quando o depurador está ativo.</xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Debugging> </xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionBuilding> </xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> Vários contextos de interface do usuário podem estar ativos ao mesmo tempo.  
  
## <a name="defining-custom-context-guids"></a>Definindo os GUIDs de contexto personalizados  
 Se um contexto de comando apropriado que GUID não estiver definido, você pode definir um o VSPackage e, em seguida, programá-lo para ser ativos ou inativos conforme necessário para controlar a visibilidade dos seus comandos.  
  
1.  Registrar os GUIDs de contexto chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A>  
  
2.  Obter o estado de um contexto de GUID ao chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>  
  
3.  Ativar e desativar o contexto GUIDs chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A>  
  
    > [!CAUTION]
    >  Certifique-se de que o VSPackage não afeta qualquer contexto existente GUIDs porque outros VSPackages pode dependem delas.  
  
## <a name="see-also"></a>Consulte também  
 [Objetos de contexto da seleção](../../extensibility/internals/selection-context-objects.md)   
 [Como os VSPackages adicionar elementos de Interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
