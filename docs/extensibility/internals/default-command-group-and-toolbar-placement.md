---
title: "Padrão de comando, o grupo e o posicionamento da barra de ferramentas | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
caps.latest.revision: 30
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
ms.openlocfilehash: 1d418eea04791d85dd0e8d08fba23abe8dc7e054
ms.lasthandoff: 02/22/2017

---
# <a name="default-command-group-and-toolbar-placement"></a>Comando padrão, o grupo e o posicionamento da barra de ferramentas
Para uniformidade de produto e estabilidade, a interface do usuário exibe determinados grupos de comando por padrão, e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornece definições para comandos e grupos de comando. Os VSPackages também pode usar os comandos padrão e os grupos de comando.  
  
 Os grupos de comando padrão se enquadram em três categorias: IDE comandos, comandos de produto e comandos do editor.  
  
## <a name="default-ide-commands"></a>Comandos do IDE padrão  
 Barra de ferramentas padrão IDE inclui comandos compartilhados por todos os produtos contidos em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Eles incluem comandos relacionados às operações de projeto genérico, como o **salvar** comando e o **Adicionar Item** comando. Os VSPackages não deve adicionar ou subtrair nessa barra de ferramentas, com uma exceção: se o produto ou VSPackage adiciona uma nova janela da ferramenta, a janela deve ser adicionada à lista de janelas de ferramentas disponíveis no **exibição** menu. Novos produtos ou VSPackages pode adicionar suas próprias ferramentas.  
  
## <a name="default-product-commands"></a>Comandos de produto padrão  
 Cada produto pode fornecer o IDE com sua própria barra de ferramentas padrão que contém informações importantes e comandos usados com frequência. No entanto, é melhor usar menus e barras de ferramentas sempre que possível existentes e complementá-las com outras barras de ferramentas de tarefas específicas, conforme necessário.  
  
 O campo de prioridade de uma barra de ferramentas determina o posicionamento da linha. Zero a prioridade coloca a barra de ferramentas na terceira linha (linha 3), abaixo da barra de menu (linha 1) e o **padrão** barra de ferramentas (linha 2). Portanto, outras barras de ferramentas aparecem na linha (prioridade + 3). Barras de ferramentas subsequentes são colocadas na mesma linha, se houver espaço; Caso contrário, eles serão automaticamente transferidos para a próxima linha.  
  
## <a name="default-editor-commands"></a>Editor de comandos padrão  
 Um VSPackage que fornece um editor personalizado deve fornecer uma barra de ferramentas padrão que contém o mais importante e comandos usados com frequência no editor. A barra de ferramentas do editor deve aparecer quando o editor está ativo e deve ser ocultado quando o editor não está ativo. Essa visibilidade é controlada no `VisibilityConstraints Element` do arquivo. VSCT.  
  
 Barras de ferramentas do Editor devem ser colocadas abaixo de ferramentas do IDE e produto.  
  
## <a name="see-also"></a>Consulte também  
 [Grupos, Menus e comandos definidos pelo IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [Como os VSPackages adicionar elementos de Interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
