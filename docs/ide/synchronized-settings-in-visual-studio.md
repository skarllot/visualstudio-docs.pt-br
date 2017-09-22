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
author: gewarren
ms.author: gewarren
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
ms.translationtype: HT
ms.sourcegitcommit: 0387b9a656f97d9354f95f121cad8422e93a69bc
ms.openlocfilehash: e48edfa02f059444539e0a3d8514366f94a1a1f1
ms.contentlocale: pt-br
ms.lasthandoff: 08/18/2017

---
# <a name="synchronize-your-settings-in-visual-studio"></a>Sincronizar as configurações no Visual Studio

Ao entrar no Visual Studio em vários computadores usando a mesma conta de personalização, por padrão, as configurações são sincronizadas em todos os computadores.

## <a name="synchronized-settings"></a>Configurações sincronizadas

Por padrão, as seguintes configurações são definidas.

- As configurações de desenvolvimento (você precisa selecionar um conjunto de configurações durante a primeira execução do Visual Studio, mas você pode alterar a seleção a qualquer momento. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md)).

- As seguintes opções nas páginas **Ferramentas &#124; Opções**:

    - **Tema** e configurações de uso de maiúsculas da barra de menus, na página de opções **Ambiente**, **Geral**

    - Todas as configurações da página de opções **Ambiente**, **Fontes e Cores**

    - Todos os atalhos de teclado, na página de opções **Ambiente**, **Teclado**

    - Todas as configurações da página de opções **Ambiente, Guias e Janelas**

    - Todas as configurações da página de opções **Ambiente**, **Inicialização**

    - Todas as configurações das páginas de opções **Editor de Texto**

    - Todas as configurações nas páginas **Designer XAML**

- Alias de comando definidos pelo usuário. Para obter mais informações sobre como definir aliases de comando, consulte [Aliases de comando do Visual Studio](../ide/reference/visual-studio-command-aliases.md).

- Layouts de janela definidos pelo usuário na página **Janela &#124; Gerenciar Layouts de Janela**

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Desligar configurações sincronizadas em um computador específico

As configurações sincronizadas para o Visual Studio são ativadas por padrão. É possível desligar as configurações sincronizadas em um computador acessando a página **Ferramentas &#124; Opções &#124; Ambiente &#124; Configurações Sincronizadas** e desmarcando a caixa de seleção.  Por exemplo, se você decidir não sincronizar as configurações do Visual Studio no Computador A, todas as alterações de configuração feitas no Computador A não serão exibidas no Computador B ou C. Os Computadores B e C continuarão sendo sincronizados entre si, mas não com o Computador A.

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Sincronizar configurações em edições e produtos da família Visual Studio

As configurações podem ser sincronizadas em qualquer edição do Visual Studio, incluindo Community Edition. As configurações também são sincronizadas em todos os produtos da família Visual Studio. No entanto, cada um desses produtos da família pode ter suas próprias configurações que não são compartilhadas com o Visual Studio. Por exemplo, configurações específicas a um produto no Computador A serão compartilhadas com outro no Computador B, mas não com o Visual Studio no Computador A ou B.

## <a name="side-by-side-synchronized-settings"></a>Configurações sincronizadas lado a lado

No Visual Studio 15.3 e posterior, nós interrompemos o compartilhamento de determinadas configurações, tais como o layout da janela de ferramentas, entre diferentes instalações lado a lado do Visual Studio 2017 alterando o local do arquivo `CurrentSettings.vssettings` em `%userprofile%\Documents\Visual Studio 2017\Settings` para uma pasta específica da instalação semelhante a `%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx\Settings`.

**OBSERVAÇÃO:** para usar as novas configurações específicas da instalação, você deve completar uma nova instalação. Quando você faz upgrade de uma instalação do Visual Studio 2017 existente para a versão mais atualizada, ela usará o local compartilhado existente. Se, no momento, você tiver instalações lado a lado do Visual Studio 2017, decidir atualizar e desejar usar o novo local do arquivo de configurações específicas de instalação, consulte as seguintes etapas:

1. Após a atualização, use o assistente de configurações de Importação\Exportação para exportar todas as nossas configurações existentes para um local fora da pasta `%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx`.
2. Abra o **Prompt de Comando do Desenvolvedor para VS 2017** da instalação do Visual Studio atualizada e execute `devenv /resetuserdata` por meio dele.
3. Inicie o Visual Studio e importe as configurações salvas do arquivo de configurações exportado.

## <a name="see-also"></a>Consulte também

[Personalizando o IDE](../ide/personalizing-the-visual-studio-ide.md)

