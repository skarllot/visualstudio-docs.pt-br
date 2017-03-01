---
title: Diretrizes de posicionamento de comando | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
caps.latest.revision: 28
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
ms.openlocfilehash: ca84800a199e9db420379697051fece598eb9295
ms.lasthandoff: 02/22/2017

---
# <a name="command-placement-guidelines"></a>Diretrizes de posicionamento de comando
Práticas recomendadas para comandos de posicionamento no ambiente de desenvolvimento integrado (IDE) do Visual Studio variam dependendo do tamanho do conjunto de comandos. Comandos são definidos e posicionados de acordo com as informações nos arquivos. VSCT.  
  
## <a name="best-practices-for-all-command-sets"></a>Práticas recomendadas para todos os conjuntos de comandos  
 Para cada conjunto de comandos, siga estas diretrizes:  
  
-   Prepare um gráfico da estrutura de comando com antecedência. Identifique os comandos, caixas de combinação, grupos de comando e menus de atalho que serão usados em mais de um local.  
  
-   Os comandos que aparecem no mesmo grupo devem estar relacionados.  
  
-   Grupos que contêm apenas um comando são aceitáveis.  
  
-   Pacotes não devem adicionar muitos comandos aos menus existentes do Visual Studio. Em vez disso, eles devem criar menus ou submenus para hospedar novos comandos.  
  
-   Quando você coloca um comando em um menu existente, o nome do comando para que seu objetivo é criptografado e não será ser confundido com comandos existentes.  
  
## <a name="best-practices-for-small-command-sets"></a>Práticas recomendadas para conjuntos de comandos pequeno  
 Se você estiver desenvolvendo um VSPackage que tenha apenas alguns comandos, também siga estas diretrizes:  
  
-   Quando possível, use o [elemento pai](../../extensibility/parent-element.md) de um comando, caixa de combinação, grupo ou menu filho para colocá-lo no grupo apropriado.  
  
-   Atribua grupos aos menus exibidos pelo VSPackage.  
  
-   O pai de um comando ou um menu filho deve ser um [elemento do grupo](../../extensibility/group-element.md). Atribuir comandos e menus filho a grupos e, em seguida, atribuir os grupos de menus do pai.  
  
-   Você pode colocar um comando em grupos adicionais, adicionando um [CommandPlacements elemento](../../extensibility/commandplacements-element.md) seção após a definição do comando e, em seguida, adicionando ao `CommandPlacements Element` um [CommandPlacement elemento](../../extensibility/commandplacement-element.md) para cada grupo adicional.  
  
## <a name="best-practices-for-large-command-sets"></a>Práticas recomendadas para conjuntos de comandos grande  
 O VSPackage terá muitos comandos que aparecerão em vários contextos, também siga estas diretrizes:  
  
-   Verifique os menus, grupos e comandos de gerenciamento automático do domínio pai. Ou seja, não atribua um `Parent Element` na definição do item.  
  
-   Use `CommandPlacement Element` entradas de `CommandPlacements Element` seção colocar menus, grupos e comandos em seus menus pai e grupos.  
  
-   No `CommandPlacements` seção, as entradas que preenchem um determinado menu ou grupo deve estar adjacente uns aos outros. Isso auxilia na legibilidade e torna o `Priority` mais fácil de determinar as classificações.  
  
## <a name="see-also"></a>Consulte também  
 [Como os VSPackages adicionar elementos de Interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
