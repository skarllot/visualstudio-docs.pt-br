---
title: Comandos definidos pelo IDE para estender sistemas de projeto | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
caps.latest.revision: 19
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
ms.openlocfilehash: 8ef8f9d3bd75057708f7e1d380da83a38d7efb4b
ms.lasthandoff: 02/22/2017

---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Comandos definidos pelo IDE para estender sistemas de projeto
Quando você deseja estender sistemas de projeto, você pode usar os comandos e comando grupos fornecidos pelo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 As seções a seguir listam os itens de comando que são especialmente úteis para estender sistemas de projeto.  
  
## <a name="command-menus"></a>Menus de comando  
 A tabela a seguir mostra os menus de comando que são úteis locais para colocar os comandos de alto nível que invocar um extensor de projeto.  
  
|Menu de comando|Descrição|  
|------------------|-----------------|  
|IDM_VS_MENU_PROJECT|O **projeto** menu de nível superior.|  
|IDM_VS_TOOL_PROJWIN|O **Solution Explorer** barra de ferramentas.|  
  
## <a name="shortcut-menus"></a>Menus de atalho  
 A tabela a seguir mostra os menus de atalho que se aplicam quando um único nó é selecionado no **Solution Explorer**, ou quando há várias seleções homogêneos no **Solution Explorer**, que é quando todos os nós selecionados são do mesmo tipo.  
  
|Menu de atalho|Descrição|  
|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Aplica-se quando o nó do projeto está selecionado.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Aplica-se quando um arquivo é selecionado.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Aplica-se quando uma pasta está selecionada.|  
|IDM_VS_CTXT_WEBREFFOLDER|Aplica-se quando a pasta de referência da Web está selecionada.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Aplica-se quando o nó raiz de referências chamado "Referências" está selecionado.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Aplica-se quando nós de referência são selecionados; Eles incluem assembly, COM e apenas referências do projeto. Não inclui referências da Web.|  
  
 A tabela a seguir mostra os menus de atalho que se aplicam quando a seleção no **Solution Explorer** abrange várias hierarquias  
  
|Menu de atalho|Descrição|  
|-------------------|-----------------|  
|IDM_VS_CTXT_XPROJ_SLNPROJ|Aplica-se quando a seleção atual contém o nó da solução e nós do projeto raiz.|  
|IDM_VS_CTXT_XPROJ_SLNITEM|Aplica-se quando a seleção atual contém os itens de projeto e o nó de solução.|  
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Aplica-se quando a seleção atual consiste em vários projetos nós raiz apenas.|  
|IDM_VS_CTXT_XPROJ_PROJITEM|Aplica-se quando a seleção atual contém uma mistura de nós de raiz do projeto e itens de projeto. Além disso, a seleção pode conter no nó da solução.|  
|IDM_VS_CTXT_XPROJ_MULTIITEM|Aplica-se quando a seleção atual contém itens de projeto de vários projetos na solução ou itens de tipos diferentes são selecionados no mesmo projeto.|  
  
## <a name="command-groups"></a>Grupos de comando  
 A tabela a seguir mostra os grupos de comando que você pode usar ao estender projetos e que você pode acessar por meio do <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>o menu de atalho.</xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>  
  
|Grupo de comando|Descrição|  
|-------------------|-----------------|  
|IDG_VS_CTXT_PROJECT_BUILD|Comandos para criar, recriar e implantar o projeto.|  
|IDG_VS_CTXT_COMPILELINK|Comandos para compilar e vincular o projeto.|  
|IDG_VS_CTXT_PROJECT_CONFIG|Comandos que defina a configuração do projeto e ordem de compilação.|  
|IDG_VS_CTXT_PROJECT_ADD|Comandos que adicionar itens ao projeto.|  
|IDG_VS_CTXT_PROJECT_START|Comandos que definem o projeto de inicialização associado a tecla F5.|  
|IDG_VS_CTXT_PROJECT_SAVE|Comandos para salvar itens de projeto.|  
|IDG_VS_CTXT_PROJECT_DEBUG|Comandos de depuração.|  
|IDG_VS_CTXT_PROJECT_SCC|Comandos de controle de origem.|  
|IDG_VS_CTXT_PROJECT_TRANSFER|Comandos para recortar, copiar e colar operações.|  
|IDG_VS_CTXT_PROJECT_PROPERTIES|Que fornecem acesso a comandos de **propriedades do projeto** caixa de diálogo.|  
  
## <a name="see-also"></a>Consulte também  
 [Como os VSPackages adicionar elementos de Interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [MenuCommands Vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [Criando grupos reutilizáveis de botões](../../extensibility/creating-reusable-groups-of-buttons.md)
