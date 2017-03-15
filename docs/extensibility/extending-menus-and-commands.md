---
title: Estendendo os Menus e comandos | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: 49
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
ms.openlocfilehash: a6f313430fb48266b59efe550d991248f56d0209
ms.lasthandoff: 02/22/2017

---
# <a name="extending-menus-and-commands"></a>Estendendo Menus e comandos
Comandos são a forma de adicionar ações e processos para o Visual Studio. Na maioria dos casos os comandos são exibidos em menus ou barras de ferramentas. O modelo de projeto de VSPackage mostra como implementar um comando muito básico. Para uma implementação um pouco mais, mas ainda básica, consulte [criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Para obter mais informações sobre comandos, menus e barras de ferramentas do Visual Studio, consulte [comandos, Menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Barras de ferramentas, menus e comandos são definidas no arquivo. VSCT que faz parte dos projetos de VSPackage. Você pode encontrar informações sobre o IDE do Visual Studio e o arquivo. VSCT na [como VSPackages adicionar elementos Interface do usuário](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Os tópicos a seguir explicam como adicionar diferentes tipos de comandos, menus e barras de ferramentas.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Adicionar um Menu a barra de menus do Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Explica como adicionar um menu na parte superior a barra de menus do Visual Studio.  
  
 [Atalhos de teclado de associação aos itens de Menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Explica como adicionar um atalho de teclado (como CTRL + 3) para um item de menu.  
  
 [Adicionando um Submenu a um Menu](../extensibility/adding-a-submenu-to-a-menu.md)  
 Explica como adicionar um submenu ao menu superior.  
  
 [Adicionar um mais recentemente usada lista a um Submenu](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 Explica como adicionar uma lista de usados recentemente.  
  
 [Criando grupos reutilizáveis de botões](../extensibility/creating-reusable-groups-of-buttons.md)  
 Descreve como agrupar itens de comando para que elas podem ser incluídas em vários menus.  
  
 [Adicionando ícones a comandos de Menu](../extensibility/adding-icons-to-menu-commands.md)  
 Descreve como adicionar um ícone para um comando em uma barra de ferramentas e um menu.  
  
 [Alterar o texto de um comando de Menu](../extensibility/changing-the-text-of-a-menu-command.md)  
 Descreve o uso do `TextChanges` sinalizador para ativar um item de menu a ser alterado dinamicamente.  
  
 [Alterando a aparência de um comando](../extensibility/changing-the-appearance-of-a-command.md)  
 Descreve como habilitar ou desabilitar um comando dinamicamente.  
  
 [Atualizando a Interface do usuário](../extensibility/updating-the-user-interface.md)  
 Descreve como forçar uma atualização da interface do usuário para refletir alterações recentes.  
  
 [Localizando os comandos de Menu](../extensibility/localizing-menu-commands.md)  
 Explica como localizar comandos de menu.  
  
## <a name="related-sections"></a>Seções relacionadas
