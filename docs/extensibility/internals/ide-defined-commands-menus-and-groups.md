---
title: Grupos, Menus e comandos definidos pelo IDE | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
caps.latest.revision: 27
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
ms.openlocfilehash: 83a3e713e4a5e9c9a90c864cf83f27e6601dfe97
ms.lasthandoff: 02/22/2017

---
# <a name="ide-defined-commands-menus-and-groups"></a>Grupos, Menus e comandos definidos pelo IDE
Muitos menus, comandos e grupos de comando já estão definidos para uso pelo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Esses comandos também estão disponíveis para uso quando você estende [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="finding-environment-defined-commands"></a>Localizando definida pelo ambiente de comandos  
 Os comandos de ambiente são definidos em um conjunto de quatro arquivos. VSCT:  
  
-   SharedCmdDef.vsct  
  
-   SharedCmdPlace.vsct  
  
-   ShellCmdDef.vsct  
  
-   ShellCmdPlace.vsct  
  
 Esses arquivos estão localizados em * \<caminho de instalação do SDK do Visual Studio >*\visualstudiointegration\common\inc.\\. Esses arquivos fornecem as definições e os GUIDs dos menus e grupos que você pode usar no comando tabela arquivo de configuração (VSCT) o VSPackage como contêineres para seus próprios menus, grupos e comandos.  
  
## <a name="in-this-section"></a>Nesta seção  
 [GUIDs e IDs de Menus do Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Fornece os valores GUID e ID de menus na barra de menu do Visual Studio e os grupos que elas contêm.  
  
 [GUIDs e IDs de barras de ferramentas do Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Fornece os valores GUID e ID de barras de ferramentas no IDE do Visual Studio e os grupos que elas contêm.  
  
 [GUIDs e IDs de comandos do Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Fornece os valores GUID e ID de comandos definidos pelo IDE do Visual Studio.  
  
## <a name="see-also"></a>Consulte também  
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Comandos definidos pelo IDE para estender sistemas de projeto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [Como os VSPackages adicionar elementos de Interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
