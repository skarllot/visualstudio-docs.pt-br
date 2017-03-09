---
title: "Sincronizar as configurações no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/23/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 4166ed8bfa0234e1cc453bd045974b412f87ae42
ms.openlocfilehash: a1a310aa6bf0e3d0042f35f5c49612f33b89fb61
ms.lasthandoff: 02/22/2017

---
# <a name="synchronize-your-settings-in-visual-studio"></a>Sincronizar as configurações no Visual Studio
Ao entrar no Visual Studio em vários computadores usando a mesma conta de personalização, por padrão, as configurações são sincronizadas em todos os computadores.

## <a name="synchronized-settings"></a>Configurações sincronizadas  
 Por padrão, as seguintes configurações são definidas.  

-   As configurações de desenvolvimento (você precisa selecionar um conjunto de configurações durante a primeira execução do Visual Studio, mas você pode alterar a seleção a qualquer momento. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).)  

-   As seguintes opções nas páginas **Ferramentas &#124; Opções**:  

    -   **Tema** e configurações de uso de maiúsculas da barra de menus, na página de opções **Ambiente**, **Geral**  

    -   Todas as configurações da página de opções **Ambiente**, **Fontes e Cores**  

    -   Todos os atalhos de teclado, na página de opções **Ambiente**, **Teclado**  

    -   Todas as configurações da página de opções **Ambiente, Guias e Janelas**  

    -   Todas as configurações da página de opções **Ambiente**, **Inicialização**  

    -   Todas as configurações das páginas de opções **Editor de Texto**  

-   Todas as configurações das páginas de opções Designer XAML  

-   Alias de comando definidos pelo usuário. Para obter mais informações sobre como definir aliases de comando, consulte [Aliases de comando do Visual Studio](../ide/reference/visual-studio-command-aliases.md).  

-   Layouts de janela definidos pelo usuário na página **Janela &#124; Gerenciar Layouts de Janela**  

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Desligar configurações sincronizadas em um computador específico  
 As configurações sincronizadas para o Visual Studio são ativadas por padrão. É possível desligar as configurações sincronizadas em um computador acessando a página **Ferramentas &#124; Opções &#124; Ambiente &#124; Configurações Sincronizadas** e desmarcando a caixa de seleção.  Por exemplo, se você decidir não sincronizar as configurações do Visual Studio no Computador A, todas as alterações de configuração feitas no Computador A não serão exibidas no Computador B ou C. Os Computadores B e C continuarão sendo sincronizados entre si, mas não com o Computador A.  

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Sincronizar configurações em edições e produtos da família Visual Studio  
 As configurações podem ser sincronizadas em qualquer edição do Visual Studio, incluindo Community Edition. As configurações também são sincronizadas em todos os produtos da família Visual Studio. No entanto, cada um desses produtos da família pode ter suas próprias configurações que não são compartilhadas com o Visual Studio. Por exemplo, configurações específicas a um produto no Computador A serão compartilhadas com outro no Computador B, mas não com o Visual Studio no Computador A ou B.  

## <a name="see-also"></a>Consulte também  
 [Personalizando o IDE](../ide/personalizing-the-visual-studio-ide.md)

