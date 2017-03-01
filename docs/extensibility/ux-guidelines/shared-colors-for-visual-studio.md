---
title: Compartilhado cores para o Visual Studio | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
caps.latest.revision: 5
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
ms.openlocfilehash: 2400fa8b096b1f8abc927eb986911200dcb62e7f
ms.lasthandoff: 02/22/2017

---
# <a name="shared-colors-for-visual-studio"></a>Cores compartilhadas para o Visual Studio
Quando você está projetando a interface do usuário que usa elementos comuns de shell do Visual Studio, ou você gostaria que o elemento de interface para ser consistente com recursos semelhantes, use nomes de token existentes nos arquivos de definição de pacote para escolher e atribuir cores. Isso garante que a interface do usuário permaneça consistente com o ambiente do Visual Studio geral e que atualiza automaticamente quando os temas são adicionados ou atualizados.  
  
 Este artigo descreve os elementos de interface do usuário comuns e os nomes de token que eles usam, que você pode fazer referência ao criar a interface do usuário semelhante. Para obter informações específicas sobre como acessar esses tokens de cor, consulte [o serviço de VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  
  
 Certifique-se de usar nomes de token corretamente:  
  
-   **Use nomes de token com base em função, não na própria cor.** As cores compartilhadas comuns associados a elementos de interface específicos e destinam-se somente a ser usado para os recursos iguais ou semelhantes. Por exemplo, não reutilize a cor de uma caixa de combinação pressionado para uma animação de progresso de rotação simplesmente porque você deseja que a cor. As funções da caixa de combinação e a animação são diferentes, e se a cor associados com as alterações de caixa de combinação, ele pode não estar mais uma cor apropriado para o elemento de animação. O uso consistente de cor ajuda a orientar seus usuários e evitar confusão.  
  
-   **Use cores de plano de fundo e texto da combinação correta.** Cores de plano de fundo que se destinam a ser usado com texto terá uma cor de texto associado. Não use cores de texto que não seja o que é especificado para esse plano de fundo. Se não houver uma cor de texto associado, não use essa cor de plano de fundo para qualquer superfície no qual você pretende exibir texto. Outras combinações de cores de plano de fundo e texto podem resultar em uma interface ilegível.  
  
-   **Use cores de controle que são apropriadas para seu local.** Em alguns estados, alguns controles do Visual Studio não têm cores de fundo e borda separada. Em vez disso, selecione as cores de superfícies por trás delas. Certifique-se de que você sempre use nomes de token que são apropriados para o local onde você está colocando o controle.  
  
> [!IMPORTANT]
>  Não use tokens encontrados nas categorias de "Página inicial" ou "Cider".  
  
## <a name="command-structures"></a>Estruturas de comando  
  
###  <a name="a-namebkmkcommandmenusa-menus"></a><a name="BKMK_CommandMenus"></a>Menus  
 Menus podem ocorrer em vários locais dentro do Visual Studio: barra de menu principal, incorporada no documento ou a ferramenta windows ou no botão direito do mouse em vários locais em todo o IDE. Implementações de menus associados com outros elementos de interface do usuário são discutidas na seção do respectivo elemento. Você deve sempre usar a implementação de menu padrão fornecida pelo ambiente do Visual Studio. No entanto, em alguns casos raros talvez você não tenha acesso aos menus padrão do Visual Studio. Nessas situações, use os seguintes nomes de token para garantir que a interface do usuário é consistente com outros menus no Visual Studio.  
  
 ![Corte de funcionários em menus](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303&000;_MenuRedline")  
  
 Use...  
 -   sempre que você precisa criar um menu personalizado.  
  
-   Quando você tem um novo componente de interface do usuário que você deseja corresponder os menus do Visual Studio.  
  
 Não use...  
 a cor de plano de fundo sozinha. Sempre use a combinação de plano de fundo/primeiro plano conforme especificado.  
  
#### <a name="menu-title"></a>Título de menu  
 Títulos de menus consistem em um plano de fundo, uma borda e o texto do título, bem como um glifo opcional, normalmente quando o menu é encontrado em uma barra de comandos.  
  
 ![Aplicar linhas vermelhas no título de menu](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303&001;_MenuTitleRedline")  
  
 Use...  
 sempre que você está criando um título de menu personalizado.  
  
 Não use...  
 -   tudo o que você não deseja sempre coincidir com o título de menu.  
  
-   em qualquer combinação de plano de fundo/primeiro plano diferente do especificado.  
  
 **Padrão**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Padrão de título de menu](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303&002;_MenuTitleDefault")  
  
 **Título de menu**  
  
 Informações preliminares  
  
 Nenhum  
  
 Primeiro plano (texto)  
  
 `Environment.CommandBarTextActive`  
  
 ![Título de menu padrão de glifo](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303&003;_MenuTitleWithGlyphDefault")  
  
 **Título de menu com o glifo**  
  
 Primeiro plano (glifos)  
  
 `Environment.CommandBarMenuGlyph`  
  
 Borda  
  
 Nenhum  
  
 **Passe o mouse**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Título de menu no foco](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303&004;_MenuTitleHover")  
  
 **Título de menu**  
  
 Informações preliminares  
  
 `Environment.CommandBarMouseOverBackgroundBegin`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (texto)  
  
 `Environment.CommandBarTextHover`  
  
 ![Título de menu com o glifo em foco](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303&005;_MenuTitleWithGlyphHover")  
  
 **Título de menu com o glifo**  
  
 Primeiro plano (glifos)  
  
 `Environment.CommandBarMenuMouseOverGlyph`  
  
 Borda  
  
 `Environment.CommandBarBorder`  
  
 **Pressionado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Título de menu pressionado](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303&006;_MenuTitlePressed")  
  
 **Título de menu**  
  
 Informações preliminares  
  
 `Environment.CommandBarMenuBackgroundGradientBegin`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (texto)  
  
 `Environment.CommandBarTextActive`  
  
 ![Título de menu com o glifo pressionado](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303&007;_MenuTitleWithGlyphPressed")  
  
 **Título de menu com o glifo**  
  
 Primeiro plano (glifos)  
  
 `Environment.CommandBarMenuMouseDownGlyph`  
  
 Borda  
  
 `Environment.CommandBarMenuBorder`  
  
 Somente à esquerda, superior e direita.  
  
 **Desabilitado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Título de menu com o glifo desabilitado](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303&008;_MenuTitleWithGlyphDisabled")  
  
 **Título de menu com o glifo**  
  
 Informações preliminares  
  
 Nenhum  
  
 Primeiro plano (texto)  
  
 `Environment.CommandBarTextInactive`  
  
 Primeiro plano (glifos)  
  
 `Environment.CommandBarTextInactive`  
  
 Borda  
  
 Nenhum  
  
#### <a name="menu"></a>Menu  
 Um item de menu individual consiste o texto do menu e um ícone opcional, a caixa de seleção ou o glifo do submenu. A alteração de cor do plano de fundo e texto em foco. Esse token de cor é um par de plano de fundo/primeiro plano.  
  
 ![Corte de funcionários em itens de menu](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303&009;_MenuItemRedline")  
  
 Use...  
 para qualquer lista suspensa que é acionada em uma barra de menus ou barra de comandos.  
  
 Não use...  
 -   para qualquer lista suspensa que ocorre em outro contexto.  
  
-   em qualquer combinação de plano de fundo/primeiro plano diferente do especificado.  
  
 **Padrão**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Padrão de menu](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303&010;_MenuDefault")  
  
 **Menu**  
  
 Informações preliminares  
  
 `Environment.CommandBarMenuBackgroundGradientBegin`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (texto)  
  
 `Environment.CommandBarTextActive`  
  
 Primeiro plano (glifo de Submenu)  
  
 `Environment.CommandBarMenuSubmenuGlyph`  
  
 Borda  
  
 `Environment.CommandBarMenuBorder`  
  
 Plano de fundo de canal de ícone  
  
 `Environment.CommandBarMenuIconBackground`  
  
 Separador  
  
 `Environment.CommandBarMenuSeparator`  
  
 Sombra  
  
 `Environment.DropShadowBackground`  
  
 ![Menu check](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303&011;_MenuChecked")  
  
 **Verificado**  
  
 Marca de seleção  
  
 `Environment.CommandBarCheckBox`  
  
 Plano de fundo de marca de seleção  
  
 `Environment.CommandBarSelectedIcon`  
  
 ![Menu selecionado](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303&012;_MenuSelected")  
  
 **Selecionado**  
  
 Plano de fundo do ícone  
  
 `Environment.CommandBarSelected`  
  
 Borda de ícone  
  
 `Environment.CommandBarSelectedBorder`  
  
 **Passe o mouse**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Foco do menu](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303&013;_MenuHover")  
  
 **Item de menu**  
  
 Informações preliminares  
  
 `Environment.CommandBarMenuItemMouseOver`  
  
 Primeiro plano (texto)  
  
 `Environment.CommandBarMenuItemMouseOver`  
  
 Primeiro plano (glifo de Submenu)  
  
 `Environment.CommandBarMenuMouseOverSubmenuGlyph`  
  
 ![Sobreposição de menu check](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303&014;_MenuHoverChecked")  
  
 **Verificado**  
  
 Marca de seleção  
  
 `Environment.CommandBarCheckBoxMouseOver`  
  
 Plano de fundo de marca de seleção  
  
 `Environment.CommandBarHoverOverSelectedIcon`  
  
 ![Sobreposição de menu selecionada](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303&015;_MenuHoverSelected")  
  
 **Selecionado**  
  
 Plano de fundo do ícone  
  
 `Environment.CommandBarHoverOverSelected`  
  
 Borda de ícone  
  
 `Environment.CommandBarHoverOverSelectedIconBorder`  
  
 **Desabilitado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Menu desabilitado](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303&016;_MenuDisabled")  
  
 Item de menu  
  
 Primeiro plano (texto)  
  
 `Environment.CommandBarTextInactive`  
  
 Primeiro plano (glifo de Submenu)  
  
 `Environment.CommandBarMenuSubmenuGlyph`  
  
 ![Menu desabilitado check](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303&017;_MenuDisabledChecked")  
  
 Selecionado  
  
 Marca de seleção  
  
 `Environment.CommandBarCheckBoxDisabled`  
  
 Plano de fundo de marca de seleção  
  
 `Environment.CommandBarSelectedIconDisabled`  
  
### <a name="command-bar"></a>Barra de comandos  
 A barra de comandos pode aparecer em vários locais no Visual Studio IDE, mais notavelmente prateleira de comando e incorporada a ferramenta ou janelas de documento.  
  
 Em geral, use sempre a implementação da barra de comando padrão fornecida pelo ambiente do Visual Studio. Usando o mecanismo padrão garante que todos os detalhes visuais aparecerá corretamente e que elementos interativos, irão se comportar consistente com outros controles de barra de comando do Visual Studio. No entanto, se for necessário para você criar sua própria barra de comandos, certifique-se de que estilo dele corretamente usando os seguintes nomes de token.  
  
 ![Corte de funcionários da barra de comandos](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303&018;_CommandBarRedline")  
  
 ![Aplicar linhas vermelhas no botão de estouro](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303&019;_OverflowButtonRedline")  
  
 Use...  
 em lugares onde você precisa de um comando inserido barra mas são não é possível usar a implementação padrão de barra de comando Visual Studio.  
  
 Não use...  
 -   para elementos de interface do usuário que não são semelhantes de uma barra de comandos.  
  
-   para componentes de barra de comando diferentes para os quais nomes de token especificados.  
  
#### <a name="command-bar-group"></a>Grupo de barra de comando  
 Um grupo de barra de comando consiste em um conjunto relacionado de controles da barra de comando e pode conter qualquer número de botões, dividir os menus suspensos, botões, caixas de combinação ou menus. Cores para esses controles são governadas por nomes de token separados e são discutidas individualmente em outro lugar neste guia. Uma linha separadora é usada para dividir um grupo de barra de comandos em subgrupos relacionados.  
  
 ![Aplicar linhas vermelhas no grupo da barra de comandos](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303&020;_CommandBarGroupRedline")  
  
 Use...  
 em lugares onde você precisa de um comando inserido barra mas são não é possível usar a implementação padrão de barra de comando Visual Studio.  
  
 Não use...  
 -   para elementos de interface do usuário que não são semelhantes de uma barra de comandos.  
  
-   para componentes de barra de comando diferentes para os quais nomes de token especificados.  
  
 **Padrão** (nenhum outro estado)  
  
 Elemento  
  
 Nome de token: Category.color  
  
 Informações preliminares  
  
 `Environment.CommandBarGradientBegin`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Borda  
  
 `Environment.CommandBarToolBarBorder`  
  
 Arraste a alça  
  
 `Environment.CommandBarDragHandle`  
  
 Separador  
  
 `Environment.CommandBarToolBarSeparator`  
  
 `Environment.CommandBarToolBarSeparatorHighlight`  
  
#### <a name="command-icons"></a>Ícones de comando  
 ![Aplicar linhas vermelhas no ícone do comando](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303&021;_CommandIconRedline1")  
  
 ![Aplicar linhas vermelhas no ícone do comando](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303&022;_CommandIconRedline2")  
  
 Use...  
 para os botões que serão colocados em uma barra de comandos.  
  
 Não use...  
 -   para controles que têm seus próprios nomes de token.  
  
-   em qualquer combinação de plano de fundo/primeiro plano diferente do especificado.  
  
 **Padrão**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Comando padrão do ícone](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303&023;_CommandIconDefault")  
  
 **Padrão**  
  
 Informações preliminares  
  
 N/d (herda do plano de fundo da barra de comando)  
  
 Primeiro plano (texto)  
  
 `Environment.CommandBarTextActive`  
  
 Borda  
  
 N/A  
  
 ![Comando padrão do ícone selecionado](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303&024;_CommandIconDefaultSelected")  
  
 **Selecionado**  
  
 Informações preliminares  
  
 `Environment.CommandBarSelected`  
  
 Primeiro plano (texto)  
  
 `Environment.CommandBarTextSelected`  
  
 Borda  
  
 `Environment.CommandBarSelectedBorder`  
  
 **Passe o mouse e teclado focado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Sobreposição de ícone do comando](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303&025;_CommandIconHover")  
  
 **Padrão focalizar**  
  
 Informações preliminares  
  
 `Environment.CommandBarMouseOverBackgroundBegin`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (texto)  
  
 `Environment.CommandBarTextHover`  
  
 Borda  
  
 `Environment.CommandBarBorder`  
  
 ![Comando sobreposição de ícone selecionada](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303&026;_CommandIconHoverSelected")  
  
 **Selecionado em foco**  
  
 Informações preliminares  
  
 `Environment.CommandBarHoverOverSelected`  
  
 Primeiro plano (texto)  
  
 `Environment.CommandBarTextHoverOverSelected`  
  
 Borda  
  
 `Environment.CommandBarHoverOverSelectedIconBorder`  
  
 **Pressionado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Ícone do comando pressionado](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303&027;_CommandIconPressed")  
  
 **Ícone do comando pressionado**  
  
 Informações preliminares  
  
 `Environment.CommandBarMouseDownBackgroundBegin`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (texto)  
  
 `Environment.CommandBarTextMouseDown`  
  
 Borda  
  
 `Environment.CommandBarBorder`  
  
 **Desabilitado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Ícone do comando desabilitado](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303&028;_CommandIconDisabled")  
  
 **Ícone do comando desabilitado**  
  
 Informações preliminares  
  
 N/d (herda do plano de fundo da barra de comando)  
  
 Primeiro plano (texto)  
  
 `Environment.CommandBarTextInactive`  
  
 Borda  
  
 N/A  
  
####  <a name="a-namebkmkcommandcomboboxa-combo-box"></a><a name="BKMK_CommandComboBox"></a>Caixa de combinação  
  
> [!IMPORTANT]
>  Caixas de combinação são semelhantes às listas suspensas, mas incluam uma região editável de texto. Se a lista suspensa não incluir uma região editável de texto, use os tokens de cor encontrados em [suspensa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).  
  
 ![Corte de funcionários da caixa de combinação](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303&029;_ComboBoxRedline")  
  
 Use...  
 -   ao criar caixas de combinação personalizada.  
  
-   ao criar um controle de barra de comandos é semelhante a uma caixa de combinação.  
  
 Não use...  
 -   para qualquer coisa não ser sempre coincidir com o comando UI da barra.  
  
-   Quando você tem acesso a uma caixa de combinação com estilo.  
  
 **Padrão**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Campo de entrada de caixa de combinação](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303&030;_ComboBoxInputField")  
  
 **Campo de entrada**  
  
 Informações preliminares  
  
 `Environment.ComboBoxBackground`  
  
 Primeiro plano (texto)  
  
 `Environment.ComboBoxText`  
  
 Borda  
  
 `Environment.ComboBoxBorder`  
  
 Separador  
  
 Nenhum separador  
  
 ![Botão de lista suspensa da caixa de combinação](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303&031;_ComboBoxDropdownButton")  
  
 **Botão suspenso**  
  
 Informações preliminares  
  
 N/d (herdado)  
  
 Primeiro plano (glifos)  
  
 `Environment.ComboBoxGlyph`  
  
 ![Combinação caixa/lista suspensa](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303&032;_ComboBoxDropdownList")  
  
 **Lista suspensa**  
  
 Informações preliminares  
  
 `Environment.ComboBoxPopupBackgroundBegin`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (texto)  
  
 `Environment.ComboBoxItemText`  
  
 Borda  
  
 `Environment.ComboBoxPopupBorder`  
  
 **Passe o mouse**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Campo de entrada de caixa de combinação em foco](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303&033;_ComboBoxInputFieldHover")  
  
 **Campo de entrada**  
  
 Informações preliminares  
  
 `Environment.ComboBoxMouseOverBackgroundBegin`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (texto)  
  
 `Environment.ComboBoxMouseOverText`  
  
 Borda  
  
 `Environment.ComboBoxMouseOverBorder`  
  
 Separador  
  
 `Environment.ComboBoxMouseOverSeparator`  
  
 ![Combinação caixa/botão suspenso ao focalizar](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303&034;_ComboBoxDropdownButtonHover")  
  
 **Botão suspenso**  
  
 Informações preliminares  
  
 `Environment.ComboBoxButtonMouseOverBackground`  
  
 Primeiro plano (glifos)  
  
 `Environment.ComboBoxMouseOverGlyph`  
  
 ![Combinação caixa/lista suspensa focalizar](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303&035;_ComboBoxDropdownListHover")  
  
 **Lista suspensa**  
  
 Plano de fundo (item de Menu)  
  
 `Environment.ComboBoxItemMouseOverBackground`  
  
 Primeiro plano (texto)  
  
 `Environment.ComboBoxItemMouseOverText`  
  
 Borda (item de Menu)  
  
 `Environment.ComboBoxItemMouseOverBorder`  
  
 **Com foco**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Color.category  
  
 ![Campo de entrada caixa de combinação com foco](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303&036;_ComboBoxInputFieldFocused")  
  
 **Campo de entrada**  
  
 Informações preliminares  
  
 `Environment.ComboBoxFocusedBackground`  
  
 Primeiro plano (texto)  
  
 `Environment.ComboBoxFocusedText`  
  
 Borda  
  
 `Environment.ComboBoxFocusedBorder`  
  
 Separador  
  
 `Environment.ComboBoxFocusedButtonSeparator`  
  
 ![Combinação caixa/botão suspenso focado](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303&037;_ComboBoxDropdownButtonFocused")  
  
 **Botão suspenso**  
  
 Informações preliminares  
  
 `Environment.ComboBoxFocusedButtonBackground`  
  
 Primeiro plano (glifos)  
  
 `Environment.ComboBoxFocusedGlyph`  
  
 **Pressionado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Color.category  
  
 ![Campo de entrada caixa de combinação pressionado](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303&038;_ComboBoxInputFieldPressed")  
  
 **Campo de entrada**  
  
 Informações preliminares  
  
 `Environment.ComboBoxMouseDownBackground`  
  
 Primeiro plano (texto)  
  
 `Environment.ComboBoxMouseDownText`  
  
 Borda  
  
 `Environment.ComboBoxMouseDownBorder`  
  
 Separador  
  
 `Environment.ComboBoxMouseDownSeparator`  
  
 ![Combinação caixa/suspensa botão pressionado](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303&039;_ComboBoxDropdownButtonPressed")  
  
 **Botão suspenso**  
  
 Informações preliminares  
  
 `Environment.ComboBoxButtonMouseDownBackground`  
  
 Primeiro plano (glifos)  
  
 `Environment.ComboBoxMouseDownGlyph`  
  
 **Desabilitado**  
  
 ![Campo de entrada caixa de combinação desabilitado](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303&041;_ComboBoxInputFieldDisabled")  
  
 **Campo de entrada**  
  
 Informações preliminares  
  
 `Environment.ComboBoxDisabledBackground`  
  
 Primeiro plano (texto)  
  
 `Environment.ComboBoxDisabledText`  
  
 Borda  
  
 `Environment.ComboBoxDisabledBorder`  
  
 Separador  
  
 Nenhum separador  
  
 ![Combinação caixa/botão suspenso desabilitado](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303&040;_ComboBoxDropdownButtonDisabled")  
  
 **Botão suspenso**  
  
 Informações preliminares  
  
 Nenhum  
  
 Primeiro plano (glifos)  
  
 `Environment.ComboBoxDisabledGlyph`  
  
####  <a name="a-namebkmkcommanddropdowna-drop-down"></a><a name="BKMK_CommandDropDown"></a>Lista suspensa  
  
> [!IMPORTANT]
>  Listas suspensas são semelhantes às caixas de combinação, mas não têm regiões editáveis de texto. Se a lista suspensa inclui uma região editável de texto, use os tokens de cor encontrados em [caixa de combinação](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).  
  
 ![Aplicar linhas vermelhas no menu suspenso](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303&042;_DropdownRedline")  
  
 Use...  
 ao criar controles de lista suspensa personalizada.  
  
 Não use...  
 -   para qualquer coisa que não seja semelhante a uma lista suspensa.  
  
-   para caixas de combinação ou botões de divisão.  
  
 **Padrão**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Campo de lista suspensa de seleção](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303&043;_DropdownSelectionField")  
  
 **Campo de seleção**  
  
 Informações preliminares  
  
 `Environment.DropDownBackground`  
  
 Primeiro plano (texto)  
  
 `DropDownText`  
  
 Borda  
  
 `DropDownBorder`  
  
 Separador  
  
 Nenhum separador  
  
 ![Botão suspenso](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303&044;_DropdownButton")  
  
 **Botão suspenso**  
  
 Informações preliminares  
  
 Nenhum  
  
 Primeiro plano (glifos)  
  
 `Environment.DropDownGlyph`  
  
 ![Lista suspensa](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303&045;_DropdownList")  
  
 **Lista suspensa**  
  
 Informações preliminares  
  
 `Environment.DropDownPopupBackgroundBegin`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (texto)  
  
 `Environment.ComboBoxItemText`  
  
 Borda  
  
 `Environment.DropDownPopupBorder`  
  
 Sombra  
  
 `Environment.DropShadowBackground`  
  
 **Passe o mouse**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Campo de lista suspensa de seleção em foco](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303&046;_DropdownSelectionFieldHover")  
  
 **Campo de seleção**  
  
 Informações preliminares  
  
 `Environment.DropDownMouseOverBackgroundBegin`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (texto)  
  
 `Environment.DropDownMouseOverText`  
  
 Borda  
  
 `Environment.DropDownMouseOverBorder`  
  
 Separador  
  
 `Environment.DropDownButtonMouseOverSeparator`  
  
 ![Botão suspenso ao focalizar](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303&047;_DropdownButtonHover")  
  
 **Botão suspenso**  
  
 Informações preliminares  
  
 `Environment.DropDownButtonMouseOverBackground`  
  
 Primeiro plano (glifos)  
  
 `Environment.DropDownMouseOverGlyph`  
  
 ![A lista suspensa no foco](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303&048;_DropdownListHover")  
  
 **Lista suspensa**  
  
 Plano de fundo (item de Menu)  
  
 `Environment.ComboBoxItemMouseOverBackground`  
  
 Primeiro plano (texto)  
  
 `Environment.ComboBoxItemMouseOverText`  
  
 Borda (item de Menu)  
  
 `Environment.ComboBoxItemMouseOverBorder`  
  
 **Pressionado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Campo de lista suspensa de seleção pressionado](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303&049;_DropdownSelectionFieldPressed")  
  
 **Campo de seleção**  
  
 Informações preliminares  
  
 `Environment.DropDownMouseDownBackground`  
  
 Primeiro plano (texto)  
  
 `Environment.DropDownMouseDownText`  
  
 Borda  
  
 `Environment.DropDownMouseDownBorder`  
  
 Separador  
  
 `Environment.DropDownButtonMouseDownSeparator`  
  
 ![Botão suspenso pressionado](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303&050;_DropdownButtonPressed")  
  
 **Botão suspenso**  
  
 Informações preliminares  
  
 `Environment.DropDownButtonMouseDownBackground`  
  
 Primeiro plano (glifos)  
  
 `Environment.DropDownMouseDownGlyph`  
  
 **Desabilitado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Campo de lista suspensa de seleção desabilitado](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303&051;_DropdownSelectionFieldDisabled")  
  
 Informações preliminares  
  
 `Environment.DropDownDisabledBackground`  
  
 Primeiro plano (texto)  
  
 `Environment.DropDownDisabledText`  
  
 Borda  
  
 `Environment.DropDownDisabledBorder`  
  
 Separador  
  
 Nenhum separador  
  
 ![Botão suspenso desabilitado](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303&052;_DropdownButtonDisabled")  
  
 Informações preliminares  
  
 N/A  
  
 Primeiro plano (glifos)  
  
 `Environment.DropDownDisabledGlyph`  
  
#### <a name="split-button"></a>Botão de divisão  
 Botões de divisão compartilham muitos nomes de token com outros controles de barra de comando, como botões, menus e texto da barra de comando. Todas as ações necessárias e nomes de token do botão suspenso são repetidos aqui por conveniência. Listas de lista suspensa de botão de divisão são implementações de barra de comandos [Menus](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).  
  
 ![Aplicar linhas vermelhas no botão de divisão](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303&053;_SplitButtonRedline")  
  
 Use...  
 Quando você está criando um botão de divisão personalizado.  
  
 Não use...  
 -   para outros tipos de botões.  
  
-   em qualquer combinação de plano de fundo/primeiro plano diferente do especificado.  
  
 **Padrão**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Botão de divisão](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303&054;_SplitButton")  
  
 **Botão de divisão (padrão)**  
  
 Informações preliminares  
  
 Nenhum  
  
 Primeiro plano (texto)  
  
 `Environment.CommandBarTextActive`  
  
 Primeiro plano (glifos)  
  
 `Environment.CommandBarSplitButtonGlyph`  
  
 Borda  
  
 N/A  
  
 Separador  
  
 N/A  
  
 **Passe o mouse**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Botão de divisão no foco](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303&055;_SplitButtonHover")  
  
 **Botão de divisão (em foco)**  
  
 Informações preliminares  
  
 `Environment.CommandBarMouseOverBackgroundBegin`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (texto)  
  
 `Environment.CommandBarTextHover`  
  
 Primeiro plano (glifos)  
  
 `Environment.CommandBarSplitButtonMouseOverGlyph`  
  
 Borda  
  
 `Environment.CommandBarBorder`  
  
 Separador  
  
 `Environment.CommandBarSplitButtonSeparator`  
  
 **Pressionado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Botão de divisão pressionado](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303&056;_SplitButtonPressed")  
  
 **Botão de divisão (pressionado)**  
  
 Informações preliminares  
  
 `Environment.CommandBarMouseDownBackgroundBegin`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (texto)  
  
 `Environment.CommandBarTextMouseDown`  
  
 Primeiro plano (glifos)  
  
 `Environment.CommandBarSplitButtonMouseDownGlyph`  
  
 Borda  
  
 `Environment.CommandBarBorder`  
  
 Separador  
  
 N/A  
  
 **Desabilitado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Botão de divisão desabilitado](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303&057;_SplitButtonDisabled")  
  
 **Botão de divisão (desabilitado)**  
  
 Informações preliminares  
  
 N/A  
  
 Primeiro plano (texto)  
  
 `Environment.ComboBoxItemTextInactive`  
  
 Primeiro plano (glifos)  
  
 `Environment.CommandBarTextInactive`  
  
 Borda  
  
 N/A  
  
 Separador  
  
 N/A  
  
#### <a name="more-options-and-overflow-buttons"></a>Botões 'Overflow' e 'Mais opções'  
 O botão "Mais opções" é usado quando um grupo de barra de comandos é personalizável, adicionando ou removendo botões da barra de comando relacionado. Botão de "Estouro" é exibida quando uma barra de comandos é truncada devido à falta de espaço horizontal e clique em mostra um menu que contém os botões da barra de comando que não podem ser exibidos. Cores desses dois botões são controladas pelo mesmo conjunto de nomes de token.  
  
 ![Mais opções de corte de funcionários](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303&058;_MoreOptionsRedline")  
  
 Use...  
 para personalizado 'mais opções' ou 'Estouro' botões.  
  
 Não use...  
 para os botões que não têm uma funcionalidade semelhante a um botão de 'estouro de ' ou 'Mais opções'.  
  
 **Padrão**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Mais opções](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303&059;_MoreOptions")  
  
 **Mais opções**  
  
 ![Botão estouro](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303&060;_Overflow")  
  
 **Estouro**  
  
 Informações preliminares  
  
 `Environment.CommandBarOptionsBackground`  
  
 Primeiro plano (glifos)  
  
 `Environment.CommandBarOptionsGlyph`  
  
 **Passe o mouse**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Mais opções de hover](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303&061;_MoreOptionsHover")  
  
 **Mais opções**  
  
 ![Estouro no foco](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303&062;_OverflowOptions")  
  
 **Estouro**  
  
 Informações preliminares  
  
 `Environment.CommandBarOptionsMouseOverBackgroundBegin`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (glifos)  
  
 `Environment.CommandBarOptionsMouseDownGlyph`  
  
 **Pressionado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Mais opções pressionado](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303&063;_MoreOptionsPressed")  
  
 **Mais opções**  
  
 ![Estouro pressionado](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303&064;_OverflowPressed")  
  
 **Estouro**  
  
 Informações preliminares  
  
 `Environment.CommandBarOptionsMouseDownBackgroundBegin`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (glifos)  
  
 `Environment.CommandBarOptionsMouseDownGlyph`  
  
## <a name="document-windows"></a>Janelas de documento  
 Não é necessário para replicar as janelas de documento, pois eles são fornecidos pelo ambiente do Visual Studio. No entanto, você pode decidir que deseja utilizar as cores usadas em janelas de documento para que a interface do usuário aparece sempre consistente com essa parte do ambiente do Visual Studio.  
  
 Ao usar tokens de cor de janela de documento, você deve ter cuidado para usá-los apenas para elementos semelhantes e sempre em pares. Se você não fizer isso, você terá resultados inesperados em sua interface do usuário.  
  
### <a name="document-window-frame"></a>Quadro de janela de documento  
 Janelas de documento podem ser encaixado no IDE ou flutuante como uma janela separada. Quando uma janela de documento é flutuante fora do IDE, ele ainda está corretamente um documento e tem o plano de fundo, borda, texto e cores de guia que são os mesmos que quando ele é parte do IDE. No entanto, o documento fica dentro de um quadro que tem seu próprio plano de fundo, borda e as cores do texto. Quando as janelas de ferramentas estão encaixadas corretamente o documento, eles herdam o comportamento e a cor de suas guias de nomes de token de janela de documento.  
  
 ![Corte de funcionários janela ancorada documento](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303&065;_DockedDocumentWindowRedline")  
  
 **Janela de documento encaixado**  
  
 ![Janela de documento flutuante aplicar linhas vermelhas no](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303&066;_FloatingDocumentWindowRedline")  
  
 **Janela de documentos flutuante**  
  
 Use...  
 em qualquer lugar você está criando a interface do usuário que você deseja corresponder a janela do documento.  
  
 Não use...  
 para qualquer interface do usuário que você não deseja automaticamente a alteração se o shell tem uma atualização de tema.  
  
 **Padrão**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 Documento: encaixado ou flutuante  
  
 Informações preliminares  
  
 Depende do tipo de documento  
  
 Primeiro plano (texto)  
  
 Depende do tipo de documento  
  
 Borda  
  
 `Environment.ToolWindowBorder`  
  
 ![Quadro com foco](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303&067;_FrameFocused")  
  
 **Quadro: flutuando, com foco**  
  
 Informações preliminares  
  
 `Environment.ToolWindowFloatingFrame`  
  
 Primeiro plano (texto)  
  
 `Environment.ToolWindowFloatingFrame`  
  
 Primeiro plano (glifos)  
  
 `Environment.RaftedWindowButtonActiveGlyph`  
  
 Borda  
  
 `Environment.MainWindowActiveDefaultBorder`  
  
 Borda (glifos)  
  
 `Environment.RaftedWindowButtonActiveBorder`  
  
 Definido como transparente  
  
 ![Quadro foco](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303&068;_FrameUnfocused")  
  
 **Quadro: flutuante, foco**  
  
 Informações preliminares  
  
 `Environment.ToolWindowFloatingFrameInactive`  
  
 Primeiro plano (texto)  
  
 `Environment.ToolWindowFloatingFrameInactive`  
  
 Primeiro plano (glifos)  
  
 `Environment.RaftedWindowButtonInactiveGlyph`  
  
 Borda  
  
 `Environment.MainWindowInactiveBorder`  
  
 Borda (glifos)  
  
 `Environment.RaftedWindowButtonInactiveBorder`  
  
 Definido como transparente  
  
 **Passe o mouse**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Quadro com foco em foco](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303&069;_FrameFocusedHover")  
  
 **Quadro: flutuando, com foco**  
  
 Plano de fundo (glifos)  
  
 `Environment.RaftedWindowButtonHoverActive`  
  
 Primeiro plano (glifos)  
  
 `Environment.RaftedWindowButtonHoverActiveGlyph`  
  
 Borda (glifos)  
  
 `Environment.RaftedWindowButtonHoverActiveBorder`  
  
 ![Quadro com foco em foco](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303&070;_FrameUnfocusedHover")  
  
 **Quadro: flutuante, foco**  
  
 Plano de fundo (glifos)  
  
 `EnvironmentRaftedWindowButtonHoverInactive`  
  
 Primeiro plano (glifos)  
  
 `Environment.RaftedWindowButtonHoverInactiveGlyph`  
  
 Borda (glifos)  
  
 `Environment.RaftedWindowButtonHoverInactiveBorder`  
  
 **Pressionado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Quadro com foco pressionado](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303&071;_FrameFocusedPressed")  
  
 **Quadro: flutuando, com foco**  
  
 Plano de fundo (glifos)  
  
 `Environment.RaftedWindowButtonDown`  
  
 Primeiro plano (glifos)  
  
 `Environment.RaftedWindowButtonDownGlyph`  
  
 Borda (glifos)  
  
 `Environment.RaftedWindowButtonDownBorder`  
  
### <a name="document-tabs"></a>Guias de documento  
 Guias de documento ficam no canal de guia para indicar quais documentos estão abertos, juntamente com o qual é o atual selecionado ou o documento ativo. Janelas de ferramenta também podem ser encaixadas no canal de guia de documento, se o usuário coloca lá. Nessa situação, usarem as mesmas cores de guia como janelas de documento. Se você estiver criando da interface do usuário que você deseja sempre corresponder as cores da janela de documento (incluindo atualizações de tema ou se novos temas instalados), e então fazer referência a esses tokens de cor.  
  
 ![Aplicar linhas vermelhas no guia de documento](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303&072;_DocumentTabRedline")  
  
 Use...  
 em qualquer lugar você está criando a interface do usuário que você deseja corresponder guias de documento e selecionar automaticamente o tema atualizações ou novas cores de tema.  
  
 Não use...  
 para qualquer interface do usuário que você não deseja alterar automaticamente quando o shell tem um tema de atualização.  
  
#### <a name="open-document-tabs"></a>Guias de documento aberto  
 Cada documento aberto tem uma guia no canal de guia de documento que exibe seu nome. Documentos podem ser selecionados ou abra no plano de fundo e suas guias refletem esses estados:  
  
-   A guia selecionada representa o documento que está sendo exibido no documento bem. Uma guia selecionada tem uma borda de documento que estende a borda superior do documento também.  
  
-   Guias de plano de fundo são guias qualquer documento que não estão na guia selecionada no momento. Quando clicado, eles se tornam a guia selecionada e obter todas as cores de plano de fundo, borda e texto desses nomes de token.  
  
 ![Aplicar linhas vermelhas no guia de documento aberto](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303&073;_OpenDocumentTabRedline")  
  
 Use...  
 Quando você cria guias de documento personalizado.  
  
 Não use...  
 -   para guias de provisionados (visualização).  
  
-   para qualquer interface do usuário que você não deseja alterar automaticamente se o shell tem uma atualização de tema.  
  
#### <a name="selected-tab"></a>Guia selecionada  
 **Com foco**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Guia selecionada focado](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303&074;_SelectedTabFocused")  
  
 **Guia de documento selecionado, com foco**  
  
 Informações preliminares  
  
 `Environment.FileTabSelectedGradientTop`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (texto)  
  
 `Environment.FileTabSelectedText`  
  
 Borda  
  
 `Environment.FileTabSelectedBorder`  
  
 Defina a mesma cor do plano de fundo.  
  
 Borda de documento  
  
 `Environment.FileTabDocumentBorderBackground`  
  
 **Foco**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Guia selecionada foco](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303&075;_SelectedTabUnfocused")  
  
 **Guia de documento selecionado, foco**  
  
 Informações preliminares  
  
 `Environment.FileTabInactiveGradientTop`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (texto)  
  
 `Environment.FileTabInactiveText`  
  
 Borda  
  
 `Environment.FileTabInactiveBorder`  
  
 Defina a mesma cor do plano de fundo.  
  
 Borda de documento  
  
 `Environment.FileTabInactiveDocumentBorderBackground`  
  
#### <a name="background-tab"></a>Guia de plano de fundo  
 **Padrão**  
  
 ![Guia de plano de fundo](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303&076;_BackgroundTab")  
  
 **Padrão de guia de plano de fundo**  
  
 Informações preliminares  
  
 `Environment.FileTabBackground`  
  
 Primeiro plano (texto)  
  
 `Environment.FileTabText`  
  
 Borda  
  
 `Environment.FileTabBorder`  
  
 Defina a mesma cor do plano de fundo.  
  
 **Passe o mouse**  
  
 ![Guia de plano de fundo em foco](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303&077;_BackgroundTabHover")  
  
 **Guia de plano de fundo em foco**  
  
 Informações preliminares  
  
 `Environment.FileTabHotGradientTop`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (texto)  
  
 `Environment.FileTabHotText`  
  
 Borda  
  
 `Environment.FileTabHotBorder`  
  
 Defina a mesma cor do plano de fundo.  
  
#### <a name="preview-tab"></a>Guia Visualização  
 Na guia Visualização aparece à direita do canal do guia de documento quando o usuário clica em um item na janela de ferramenta do Gerenciador de soluções. Ele atua como uma visualização do documento e também fornece ao usuário a opção de manter o documento aberto no lado esquerdo do canal do guia de documento. Guia de apenas uma visualização aberta pode ser aberto por vez. Guias de visualização têm ambos de plano de fundo e estados selecionados, como guias abertas e pode ser focalizado ou foco em seu estado ativo.  
  
 ![Aplicar linhas vermelhas no guia Visualizar](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303&078;_PreviewTabRedline")  
  
 Use...  
 em qualquer lugar, você está criando visualização temporária e deseja algum elemento para coincidir com a cor da guia visualização atual.  
  
 Não use...  
 -   para qualquer tipo de documento ou na guia que não é temporária (visualização).  
  
-   para qualquer interface do usuário que você não deseja alterar automaticamente se o shell tem uma atualização de tema.  
  
 **A guia visualização selecionada: foco**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![A guia Visualização focada](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303&079;_PreviewTabFocused")  
  
 **Guia Visualização focalizado**  
  
 Informações preliminares  
  
 `Environment.FileTabProvisionalSelectedActive`  
  
 Primeiro plano (texto)  
  
 `Environment.FileTabProvisionalSelectedActiveForeground`  
  
 Borda  
  
 `Environment.FileTabProvisionalSelectedActiveBorder`  
  
 Defina a mesma cor do plano de fundo.  
  
 Borda de documento  
  
 `Environment.FileTabProvisionalSelectedActiveBorder`  
  
 **A guia visualização selecionada: foco**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![A guia Visualização foco](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303&080;_PreviewTabUnfocused")  
  
 **Guia Visualização de foco**  
  
 Informações preliminares  
  
 `Environment.FileTabProvisionalSelectedInactive`  
  
 Primeiro plano (texto)  
  
 `Environment.FileTabProvisionalSelectedInactiveForeground`  
  
 Borda  
  
 `Environment.FileTabProvisionalSelectedInactiveBorder`  
  
 Borda de documento  
  
 `Environment.FileTabProvisionalSelectedInactiveBorder`  
  
 **Guia de visualização de plano de fundo: padrão**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Guia de plano de fundo da visualização](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303&081;_PreviewBackgroundTab")  
  
 **Guia de plano de fundo do guia de visualização**  
  
 Informações preliminares  
  
 `Environment.FileTabProvisionalInactive`  
  
 Primeiro plano (texto)  
  
 `Environment.FileTabProvisionalInactiveForeground`  
  
 Borda  
  
 `Environment.FileTabProvisionalInactiveBorder`  
  
 Defina a mesma cor do plano de fundo.  
  
 **Guia de visualização de plano de fundo: passe o mouse**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Guia de plano de fundo da visualização no foco](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303&082;_PreviewBackgroundTabHover")  
  
 **Guia de plano de fundo de guia Visualização em foco**  
  
 Informações preliminares  
  
 `Environment.FileTabProvisionalHover`  
  
 Primeiro plano (texto)  
  
 `Environment.FileTabProvisionalHoverForeground`  
  
 Borda  
  
 `Environment.FileTabProvisionalHoverBorder`  
  
 Defina a mesma cor do plano de fundo.  
  
#### <a name="document-overflow-button"></a>Botão de estouro do documento  
 O botão de estouro do documento está presente se há um ou mais documentos abertos, independentemente se há espaço vertical na configuração atual de acordo com todas as guias do documento. O menu suspenso de estouro de documento, que é controlado pelo **CommandBarMenu** cores (consulte [Menus](../../misc/shared-colors.md#BKMK_CommandMenus)), exibe uma lista de todos os documentos abertos, visíveis e ocultos e as alterações de glifo de estouro dependendo se todos os documentos abertos serão exibidos no canal de guia.  
  
 ![Aplicar linhas vermelhas no estouro](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303&083;_OverflowRedline")  
  
 Use...  
 Quando você estiver criando um botão de estouro do documento personalizado.  
  
 Não use...  
 -   interface do usuário que não é semelhante a um botão de estouro.  
  
-   para botões de estouro da barra de comando.  
  
 **Padrão**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Estouro](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303&084;_Overflow")  
  
 **Botão de estouro do documento**  
  
 Informações preliminares  
  
 `Environment.DocWellOverflowButtonBackground`  
  
 Primeiro plano (glifos)  
  
 `Environment.DocWellOverflowButtonGlyph`  
  
 Borda  
  
 N/A  
  
 **Passe o mouse**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Estouro no foco](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303&085;_OverflowHover")  
  
 **Botão de estouro do documento em foco**  
  
 Informações preliminares  
  
 `Environment.DocWellOverflowButtonMouseOverBackground`  
  
 Primeiro plano (glifos)  
  
 `Environment.DocWellOverflowButtonMouseOverGlyph`  
  
 Borda  
  
 `Environment.DocWellOverflowButtonMouseOverBorder`  
  
 **Pressionado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Estouro pressionado](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303&086;_OverflowPressed")  
  
 **Pressionado o botão de estouro do documento**  
  
 Informações preliminares  
  
 `Environment.DocWellOverflowButtonMouseDownBackground`  
  
 Primeiro plano (glifos)  
  
 `Environment.DocWellOverflowButtonMouseDownGlyph`  
  
 Borda  
  
 `Environment.DocWellOverflowButtonMouseDownBorder`  
  
## <a name="tool-windows"></a>Janelas de ferramenta  
 Não é necessário para replicar as janelas de ferramentas, porque eles são fornecidos pelo ambiente do Visual Studio. No entanto, você pode decidir que deseja utilizar as cores usadas em janelas de ferramenta para que a interface do usuário aparece sempre consistente com essa parte do ambiente do Visual Studio.  
  
 ![Janela da ferramenta de corte de funcionários](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303&087;_ToolWindowRedline")  
  
 Use...  
 em qualquer lugar você está criando a interface do usuário que você deseja corresponder janelas de ferramenta.  
  
 Não use...  
 para qualquer interface do usuário que você não deseja alterar automaticamente se o shell tem uma atualização de tema.  
  
### <a name="tool-window-frame"></a>Quadro de janela de ferramenta  
 Janelas de ferramenta no Visual Studio são usadas para várias tarefas diferentes e podem existir em um de vários estados diferentes. Se uma janela de ferramentas estiver aberta, pode ser atribuído a qualquer um dos quatro lados da área do documento. Janelas de ferramenta também podem flutuar fora do IDE, o que permitirá a ser reposicionadas em qualquer lugar na tela do usuário. Janelas flutuantes sempre ficam sobre o IDE. Finalmente, janelas de ferramentas podem ser encaixadas como janelas de documento e aparecem como uma guia no documento bem. Janelas de ferramenta que foi encaixadas como janelas de documento são coloridas em parte usando nomes de token de janela de documento.  
  
 ![Aplicar linhas vermelhas no quadro de janela de ferramenta](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303&088;_ToolWindowFrameRedline")  
  
 Use...  
 em qualquer lugar você está criando a interface do usuário que você deseja corresponder janelas de ferramenta.  
  
 Não use...  
 para qualquer interface do usuário que você não deseja alterar automaticamente se o shell tem uma atualização de tema.  
  
 **Encaixado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Janela de ferramenta encaixada](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303&089;_ToolWindowDocked")  
  
 Informações preliminares  
  
 `Environment.ToolWindowBackground`  
  
 Borda  
  
 `Environment.ToolWindowBorder`  
  
 **Flutuante: foco**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Janela de ferramenta focada](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303&090;_ToolWindowFocused")  
  
 Informações preliminares  
  
 `Environment.ToolWindowBackground`  
  
 Borda  
  
 `Environment.MainWindowActiveDefaultBorder`  
  
 **Flutuante: foco**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Janela de ferramenta foco](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303&091;_ToolWindowUnfocused")  
  
 Informações preliminares  
  
 `Environment.ToolWindowBackground`  
  
 Borda  
  
 `Environment.MainWindowInactiveBorder`  
  
### <a name="tool-window-title-bar"></a>Barra de título de janela de ferramenta  
 A borda da barra de título não é uma borda true, mas uma linha espessa na parte superior da barra de título. Ele não tem um nome de token para o estado de foco.  
  
 ![Aplicar linhas vermelhas no barra de título de janela de ferramenta](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303&092;_ToolWindowTitleBarRedline")  
  
 Use...  
 em qualquer lugar você está criando a interface do usuário que você deseja corresponder janelas de ferramenta.  
  
 Não use...  
 para qualquer interface do usuário que você não deseja alterar automaticamente se o shell tem uma atualização de tema.  
  
 **Com foco**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Foco da barra de título](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303&093;_TitleBarFocused")  
  
 **Barra de título de foco**  
  
 Informações preliminares  
  
 `Environment.TitleBarActiveGradientBegin`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (texto)  
  
 `Environment.TitleBarActiveText`  
  
 Borda  
  
 `Environment.TitleBarActiveBorder`  
  
 Defina a mesma cor do plano de fundo.  
  
 Arraste a alça  
  
 `Environment.TitleBarDragHandleActive`  
  
 **Foco**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Foco da barra de título](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303&094;_TitleBarUnfocused")  
  
 **Barra de título de foco**  
  
 Informações preliminares  
  
 `Environment.TitleBarInactiveGradientBegin`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (texto)  
  
 `Environment.TitleBarInactiveText`  
  
 Borda  
  
 N/A  
  
 Arraste a alça  
  
 `Environment.TitleBarDragHandle`  
  
#### <a name="title-bar-buttons"></a>Botões da barra de título  
 ![Aplicar linhas vermelhas no botão da barra de título](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303&095;_TitleBarButtonRedline")  
  
 Use...  
 para os botões que aparecem na interface do usuário que usa tokens de cor das barras de título da janela de ferramenta.  
  
 Não use...  
 -   para os botões que aparecem em outros locais.  
  
-   em qualquer combinação de plano de fundo/primeiro plano diferente do especificado.  
  
 **Padrão**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Focada do botão da barra de título](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303&096;_TitleBarButtonFocused")  
  
 **Com foco**  
  
 Informações preliminares  
  
 N/A  
  
 Primeiro plano (glifos)  
  
 `Environment.ToolWindowButtonActiveGlyph`  
  
 Borda  
  
 N/A  
  
 ![Foco do botão da barra de título](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303&097;_TitleBarButtonUnfocused")  
  
 **Foco**  
  
 Informações preliminares  
  
 N/A  
  
 Primeiro plano (glifos)  
  
 `Environment.ToolWindowButtonInactiveGlyph`  
  
 Borda  
  
 N/A  
  
 **Passe o mouse**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Botão da barra de título com foco em foco](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303&098;_TitleBarButtonFocusedHover")  
  
 **Com foco**  
  
 Informações preliminares  
  
 `Environment.ToolWindowButtonHoverActive`  
  
 Primeiro plano (glifos)  
  
 `Environment.ToolWindowButtonHoverActiveGlyph`  
  
 Borda  
  
 `Environment.ToolWindowButtonHoverActiveBorder`  
  
 ![Foco no foco do botão da barra de título](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303&099;_TitleBarButtonUnfocusedHover")  
  
 **Foco**  
  
 Informações preliminares  
  
 `Environment.ToolWindowButtonHoverInactive`  
  
 Primeiro plano (glifos)  
  
 `Environment.ToolWindowButtonHoverInactiveGlyph`  
  
 Borda  
  
 `Environment.ToolWindowButtonHoverInactiveBorder`  
  
 **Pressionado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Botão de foco e pressionado da barra de título](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303&100;_TitleBarButtonFocusedPressed")  
  
 **Com foco**  
  
 Informações preliminares  
  
 `Environment.ToolWindowButtonDown`  
  
 Primeiro plano (glifos)  
  
 `Environment.ToolWindowButtonDownActiveGlyph`  
  
 Borda  
  
 `Environment.ToolWindowButtonDownBorder`  
  
 ![Botão de barra de título foco e pressionado](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303&101;_TitleBarButtonUnfocusedPressed")  
  
 **Foco**  
  
 Informações preliminares  
  
 `Environment.ToolWindowButtonDown`  
  
 Primeiro plano (glifos)  
  
 `Environment.ToolWindowButtonDownInactiveGlyph`  
  
 Borda  
  
 `Environment.ToolWindowButtonDownBorder`  
  
### <a name="tool-window-tabs"></a>Guias da janela de ferramenta  
 ![Aplicar linhas vermelhas no guia da janela de ferramenta](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303&102;_ToolWindowTabRedline")  
  
 Use...  
 em qualquer lugar você está criando a interface do usuário que você deseja corresponder janelas de ferramenta.  
  
 Não use...  
 para qualquer interface do usuário que você não deseja alterar automaticamente se o shell tem uma atualização de tema.  
  
 **Guia selecionada**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Guia da janela de ferramenta focada](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303&103;_ToolWindowTabFocused")  
  
 **Guia da janela de ferramenta focalizado atualmente selecionado**  
  
 Informações preliminares  
  
 `Environment.ToolWindowTabSelectedTab`  
  
 Primeiro plano (texto)  
  
 `Environment.ToolWindowTabSelectedActiveText`  
  
 Borda  
  
 `Environment.ToolWindowTabSelectedBorder`  
  
 Defina a mesma cor do plano de fundo.  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Guia de janela de ferramenta foco](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303&104;_ToolWindowTabUnfocused")  
  
 **Guia da janela de ferramenta foco selecionado**  
  
 Informações preliminares  
  
 `Environment.ToolWindowTabSelectedTab`  
  
 Primeiro plano (texto)  
  
 `Environment.ToolWindowTabSelectedText`  
  
 Borda  
  
 `Environment.ToolWindowTabSelectedBorder`  
  
 Defina a mesma cor do plano de fundo.  
  
 **Guia de plano de fundo**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Guia de plano de fundo da janela de ferramenta](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303&105;_ToolWindowBackgroundTab")  
  
 **Guia de janela de ferramenta do plano de fundo**  
  
 Informações preliminares  
  
 `Environment.ToolWindowTabGradientBegin`  
  
 Marcas de gradiente definido como o mesmo valor de cor no Visual Studio 2013.  
  
 `Environment.ToolWindowTabGradientEnd`  
  
 Marcas de gradiente definido como o mesmo valor de cor no Visual Studio 2013.  
  
 Primeiro plano (texto)  
  
 `Environment.ToolWindowTabText`  
  
 Borda  
  
 `Environment.ToolWindowTabBorder`  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Guia de plano de fundo de janela de ferramenta no foco](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303&106;_ToolWindowBackgroundTabHover")  
  
 **Guia de janela de ferramenta do plano de fundo em foco**  
  
 Informações preliminares  
  
 `Environment.ToolWindowTabMouseOverBackgroundBegin`  
  
 Marcas de gradiente definido como o mesmo valor de cor no Visual Studio 2013.  
  
 `Environment.ToolWindowTabMouseOverBackgroundEnd`  
  
 Marcas de gradiente definido como o mesmo valor de cor no Visual Studio 2013.  
  
 Primeiro plano (texto)  
  
 `Environment.ToolWindowTabMouseOverText`  
  
 Borda  
  
 `Environment.ToolWindowTabMouseOverBorder`  
  
 Defina a mesma cor do plano de fundo.  
  
### <a name="auto-hide-tabs"></a>Guias de ocultar automaticamente  
 ![Corte de funcionários de ocultar automaticamente](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303&107;_AutoHideRedline")  
  
 Use...  
 em qualquer lugar você está criando a interface do usuário que você deseja corresponder guias da janela de ferramenta ocultos automaticamente.  
  
 Não use...  
 para qualquer interface do usuário que você não deseja alterar automaticamente se o shell tem uma atualização de tema.  
  
 **Padrão**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Guia de ocultar automaticamente](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303&108;_AutoHideTab")  
  
 **Guia de ocultação automática padrão**  
  
 Informações preliminares  
  
 `Environment.AutoHideTabBackgroundBegin`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (texto)  
  
 `Environment.AutoHideTabText`  
  
 Borda  
  
 `Environment.AutoHideTabBorder`  
  
 **Passe o mouse**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Guia de ocultar automaticamente ao focalizar](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303&109;_AutoHideTabHover")  
  
 **Guia de ocultar automaticamente em foco**  
  
 Informações preliminares  
  
 `Environment.AutoHideTabMouseOverBackgroundBegin`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (texto)  
  
 `Environment.AutoHideTabMouseOverText`  
  
 Borda  
  
 `Environment.AutoHideTabMouseOverBorder`  
  
## <a name="common-shared-controls"></a>Controles comuns do compartilhado  
 Quando você usa uma barra de comandos padrão do Visual Studio em seu recurso, você terá acesso a controles com estilo shell e você deve não re-modelo desses controles comuns. No entanto, se você precisar criar uma barra de comandos personalizada, você precisa criar controles personalizados também. Nesse caso, certifique-se de usar os nomes de token corretos para cada um dos seguintes controles para que a interface do usuário seja consistente com o restante do Visual Studio.  
  
### <a name="search-box"></a>Caixa de pesquisa  
 Sempre que possível, use o controle de pesquisa comuns fornecido pelo ambiente do Visual Studio. Cores da caixa de pesquisa são encontradas na categoria "SearchControl" no **ShellColors.pkgdef** arquivo, que contém nomes de token para o campo de entrada, o botão de ação, botão suspenso e menu suspenso.  
  
 Uma caixa de pesquisa pode ser um dos vários estados, alguns dos quais são mutuamente exclusivos:  
  
-   "Foco" ou "foco" refere-se ao se o cursor está na caixa de texto.  
  
-   "Active" ou "inativo" se refere ao se o usuário tem de entrada uma consulta de pesquisa na caixa de texto.  
  
-   "Sobreposição" significa que o usuário tem moused sobre a caixa de pesquisa com o mouse (esse estado substitui todos os outros estados).  
  
-   "Desabilitado" significa que a funcionalidade de pesquisa é desativada para o contexto atual.  
  
 ![Corte de funcionários da caixa de pesquisa](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303&110;_SearchBoxRedline")  
  
 Use...  
 Quando você está criando uma caixa de pesquisa personalizada.  
  
 Não use...  
 -   para qualquer coisa que não seja uma caixa de pesquisa.  
  
-   para qualquer coisa que você não deseja sempre correspondem à pesquisa de caixa de interface do usuário.  
  
 **Com foco**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Campo de entrada de pesquisa focado](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303&111;_SearchInputFieldFocused")  
  
 **Campo de entrada**  
  
 Informações preliminares  
  
 `SearchControl.FocusedBackground`  
  
 Primeiro plano (texto)  
  
 `SearchControl.FocusedBackground`  
  
 Borda  
  
 `SearchControl.FocusedBorder`  
  
 Separador  
  
 `SearchControl.FocusedDropDownSeparator`  
  
 ![Botão de ação de pesquisa foco](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303&112;_SearchActionButtonFocused")  
  
 **Botão de ação**  
  
 Informações preliminares  
  
 Nenhum  
  
 Primeiro plano (glifo de pesquisa)  
  
 `SearchControl.SearchGlyph`  
  
 Primeiro plano (glifos de interrupção)  
  
 `SearchControl.StopGlyph`  
  
 Primeiro plano (Limpar glifo)  
  
 `SearchControl.ClearGlyph`  
  
 Borda  
  
 N/A  
  
 ![Botão suspenso de pesquisa focada](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303&113;_SearchDropdownButtonFocused")  
  
 **Botão suspenso**  
  
 Informações preliminares  
  
 `SearchControl.FocusedDropDownButton`  
  
 Primeiro plano (glifos)  
  
 `SearchControl.FocusedDropDownButtonGlyph`  
  
 Borda  
  
 `SearchControl.FocusedDropDownButtonBorder`  
  
 **Foco**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Campo de pesquisa foco](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303&114;_SearchInputFieldUnfocused")  
  
 **Campo de entrada ativo**  
  
 Informações preliminares  
  
 `SearchControl.SearchActiveBackground`  
  
 Primeiro plano (texto)  
  
 `SearchControl.SearchActiveBackground`  
  
 Borda  
  
 `SearchControl.UnfocusedBorder`  
  
 Separador  
  
 `SearchControl.DropDownSeparator`  
  
 ![Campo de entrada de pesquisa sem foco e inativo](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")  
  
 **Campo de entrada inativo**  
  
 Informações preliminares  
  
 `SearchControl.Unfocused`  
  
 Primeiro plano (texto)  
  
 `SearchControl.Unfocused`  
  
 Borda  
  
 `SearchControl.UnfocusedBorder`  
  
 Separador  
  
 `SearchControl.DropDownSeparator`  
  
 ![Botão de ação de pesquisa foco](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303&115;_SearchActionButtonUnfocused")  
  
 **Botão de ação**  
  
 Informações preliminares  
  
 N/A  
  
 Primeiro plano (glifo de pesquisa)  
  
 `SearchControl.SearchGlyph`  
  
 Primeiro plano (glifos de interrupção)  
  
 `SearchControl.StopGlyph`  
  
 Primeiro plano (Limpar glifo)  
  
 `SearchControl.ClearGlyph`  
  
 Borda  
  
 N/A  
  
 ![Botão suspenso de pesquisa foco](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303&116;_SearchDropdownButtonUnfocused")  
  
 **Botão suspenso**  
  
 Informações preliminares  
  
 `SearchControl.UnfocusedDropDownButton`  
  
 Primeiro plano (glifos)  
  
 `SearchControl.UnfocusedDropDownButtonGlyph`  
  
 Borda  
  
 `SearchControl.UnfocusedDropDownButtonBorder`  
  
 **Pressionado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Botão de ação de pesquisa pressionado](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")  
  
 **Botão de ação**  
  
 Informações preliminares  
  
 `SearchControl.ActionButtonMouseDown`  
  
 Primeiro plano (glifos)  
  
 `SearchControl.ActionButtonMouseDownGlyph`  
  
 Borda  
  
 `SearchControl.ActionButtonMouseDownBorder`  
  
 ![Botão suspenso de pesquisa pressionado](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")  
  
 **Botão suspenso**  
  
 Informações preliminares  
  
 `SearchControl.MouseDownDropDownButton`  
  
 Primeiro plano (glifos)  
  
 `SearchControl.MouseDownDropDownButtonGlyph`  
  
 Borda  
  
 `SearchControl.MouseDownDropDownButtonBorder`  
  
 **Destaque (somente texto)**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Realce de campo de entrada de pesquisa](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303&120;_SearchInputFieldHighlight")  
  
 **Campo de entrada com texto realçado**  
  
 Informações preliminares  
  
 `SearchControl.Selection`  
  
 Primeiro plano (texto)  
  
 `SearchControl.FocusedBackground`  
  
 Borda  
  
 Nenhum  
  
 Separador  
  
 `SearchControl.FocusedDropDownSeparator`  
  
 **Desabilitado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Campo de entrada de pesquisa desabilitado](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303&121;_SearchInputFieldDisabled")  
  
 **Campo de entrada**  
  
 Informações preliminares  
  
 `SearchControl.Disabled`  
  
 Primeiro plano (texto)  
  
 `SearchControl.Disabled`  
  
 Borda  
  
 `SearchControl.DisabledBorder`  
  
 Separador  
  
 `SearchControl.DropDownSeparator`  
  
 ![Botão de ação de pesquisa desabilitado](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303&122;_SearchActionButtonDisabled")  
  
 **Botão de ação**  
  
 Informações preliminares  
  
 Nenhum  
  
 Primeiro plano (glifos)  
  
 `SearchControl.ActionButtonDisabledGlyph`  
  
 Borda  
  
 Nenhum  
  
 ![Botão suspenso de pesquisa desabilitado](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303&123;_SearchDropdownButtonDisabled")  
  
 **Botão suspenso**  
  
 Informações preliminares  
  
 Nenhum  
  
 Primeiro plano (glifos)  
  
 `SearchControl.DisabledDownButtonGlyph`  
  
 Borda  
  
 Nenhum  
  
#### <a name="search-drop-down-lists"></a>Listas suspensas de pesquisa  
 Menu de lista suspensa da caixa de pesquisa tem potencial para ser um pouco mais complexo do que outros menus suspensos no Visual Studio. As seções de "opções de pesquisa" e "pesquisas sugeridas" pode aparecer sozinhas ou juntos no menu e cada um deles é colorido separadamente. Uma linha também separa nessas duas seções quando aparecem juntos e uma borda ao redor do menu suspenso toda.  
  
 ![Aplicar linhas vermelhas no suspensa pesquisa](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303&124;_SearchDropdownRedline")  
  
 Use...  
 -   Quando você está criando uma lista suspensa de pesquisa personalizada.  
  
-   os nomes de token corretos para os componentes de lista correta.  
  
 Não use...  
 -   para listas suspensas que aparecem em outros contextos.  
  
-   em qualquer combinação de plano de fundo/primeiro plano diferente do especificado.  
  
 **Padrão (nenhum outro estado)**  
  
 Elemento  
  
 Nome de token: Category.color  
  
 Borda  
  
 `SearchControl.PopupBorder`  
  
 Separador  
  
 `SearchControl.PopupSectionHeaderSeparator`  
  
 Sombra  
  
 `Environment.DropShadowBackground`  
  
 **Padrão**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Pesquisa sugerida](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303&125;_SearchSuggested")  
  
 **Pesquisas sugeridas**  
  
 Informações preliminares  
  
 `SearchControl.PopupItemsListBackgroundGradientBegin`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (texto)  
  
 `SearchControl.PopupItemText`  
  
 ![Caixa de seleção Pesquisar](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303&126;_SearchCheckbox")  
  
 **Opções de pesquisa (caixa de seleção)**  
  
 ![Opções de pesquisa](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303&127;_SearchOptions")  
  
 **Opções de pesquisa (link)**  
  
 Informações preliminares  
  
 `SearchControl.PopupSectionBackgroundGradientBegin`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (caixa de texto)  
  
 `SearchControl.PopupCheckboxText`  
  
 Primeiro plano (texto de Link)  
  
 `SearchControl.PopupButtonText`  
  
 Plano de fundo do cabeçalho  
  
 `SearchControl.PopupSectionHeaderGradientBegin`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (texto do cabeçalho)  
  
 `SearchControl.PopupSectionHeaderText`  
  
 **Passe o mouse**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Pesquisa sugerida focalizar](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303&128;_SearchSuggestedHover")  
  
 **Pesquisas sugeridas**  
  
 Informações preliminares  
  
 `SearchControl.PopupControlMouseOverBackgroundGradientBegin`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (texto)  
  
 `SearchControl.PopupMouseOverItemText`  
  
 Borda  
  
 `SearchControl.PopupControlMouseOverBorder`  
  
 ![Caixa de seleção Pesquisar em foco](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303&129;_SearchCheckboxHover")  
  
 **Pesquisas sugeridas (caixa de seleção)**  
  
 ![Opções no foco de pesquisa](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303&130;_SearchOptionsHover")  
  
 **Opções de pesquisa**  
  
 Informações preliminares  
  
 `SearchControl.PopupControlMouseOverBackgroundGradientBegin`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (caixa de texto)  
  
 `SearchControl.PopupCheckboxMouseDownText`  
  
 Primeiro plano (texto de Link)  
  
 `SearchControl.PopupButtonMouseDownText`  
  
 Borda  
  
 `SearchControl.PopupControlMouseOverBorder`  
  
 **Pressionado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Pesquisa sugeridos pressionado](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303&131;_SearchSuggestedPressed")  
  
 **Pesquisas sugeridas (caixa de seleção)**  
  
 ![Pesquisar opções pressionadas](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303&132;_SearchOptionsPressed")  
  
 **Opções de pesquisa**  
  
 Plano de fundo da caixa de seleção  
  
 `SearchControl.PopupControlMouseDownBackgroundGradientBegin`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 `SearchControl.PopupControlMouseDownBackgroundGradientEnd`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (caixa de texto)  
  
 `SearchControl.PopupCheckboxMouseDownText`  
  
 Plano de fundo do link  
  
 `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`  
  
 Embora não usado na interface do usuário com temas modernos, há paradas de gradiente e valores para este plano de fundo.  
  
 Primeiro plano (texto de Link)  
  
 `SearchControl.PopupButtonMouseDownText`  
  
### <a name="hyperlink"></a>Hiperlink  
 O hiperlink é um controle que não tem um par de primeiro e segundo plano. Em todos os casos, use a cor do primeiro plano hiperlink, que será exibido corretamente nos planos de fundo brancos e cinzas escuros. Se você não usar o token de cor para o controle hyperlink, você verá a cor padrão do sistema para "pressionado", "que vai piscar vermelho. É o sinal de que o controle não está usando o token de cor correta do ambiente.  
  
 ![Aplicar linhas vermelhas no hiperlink](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303&133;_HyperlinkRedline")  
  
 Use...  
 Quando você precisa criar um hiperlink personalizado.  
  
 Não use...  
 para qualquer coisa que não é um hiperlink.  
  
 **Padrão**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Padrão de hiperlink](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303&134;_Hyperlink")  
  
 Primeiro plano (texto)  
  
 `Environment.PanelHyperlink`  
  
 **Passe o mouse**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Hiperlink focalizar](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303&135;_HyperlinkHover")  
  
 Primeiro plano (texto)  
  
 `Environment.PanelHyperlinkHover`  
  
 **Pressionado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Hiperlink pressionado](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303&136;_HyperlinkPressed")  
  
 Primeiro plano (texto)  
  
 `Environment.PanelHyperlinkPressed`  
  
 **Desabilitado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Hiperlink desabilitado](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303&137;_HyperlinkDisabled")  
  
 Primeiro plano (texto)  
  
 `Environment.PanelHyperlinkDisabled`  
  
### <a name="infobar"></a>Barra de informações  
 Infobars são usados para fornecer mais informações sobre um determinado contexto e sempre aparecem na parte superior de uma janela de documento ou janela de ferramenta.  
  
 ![Aplicar linhas vermelhas no barra de informações](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303&138;_InfobarRedline")  
  
 Use...  
 ao criar infobars personalizados.  
  
 Não use...  
 para elementos de interface do usuário que não são semelhantes de uma barra de informações.  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Barra de informações](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303&139;_Infobar")  
  
 **Barra de informações**  
  
 Informações preliminares  
  
 `Environment.InfoBackground`  
  
 Primeiro plano (texto)  
  
 `Environment.InfoText`  
  
 Borda  
  
 `Environment.ToolWindowBorder`  
  
### <a name="scroll-bar"></a>Barra de rolagem  
 Barras de rolagem são denominadas pelo ambiente do Visual Studio e não precisa ter temas. No entanto, você pode decidir que deseja utilizar as cores usadas em barras de rolagem para que a interface do usuário aparece sempre consistente com isso esta parte do ambiente do Visual Studio.  
  
 ![Corte de funcionários da barra de rolagem](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303&140;_ScrollbarRedline")  
  
 Use...  
 Quando você está criando a interface do usuário que você deseja corresponder as barras de rolagem do Visual Studio.  
  
 Não use...  
 para qualquer coisa que você não quer sempre corresponder scrollbar da interface do usuário.  
  
 **Padrão**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Barra de rolagem](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303&141;_Scrollbar")  
  
 **Barra de rolagem**  
  
 Barra de Rolagem  
  
 `Environment.ScrollBarBackground`  
  
 Primeiro plano (miniatura)  
  
 `Environment.ScrollBarThumbBackground`  
  
 ![Seta de barra de rolagem](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303&142;_ScrollbarArrow")  
  
 **Seta de rolagem**  
  
 Informações preliminares  
  
 `Environment.ScrollBarArrowBackground`  
  
 Defina a mesma cor que a barra de rolagem.  
  
 Primeiro plano (glifos)  
  
 `Environment.ScrollBarArrowGlyph`  
  
 **Passe o mouse**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Barra de rolagem no foco](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303&143;_ScrollbarHover")  
  
 **Barra de rolagem**  
  
 Barra de Rolagem  
  
 `Environment.ScrollBarBackground`  
  
 Primeiro plano (miniatura)  
  
 `Environment.ScrollBarThumbMouseOverBackground`  
  
 ![Seta no foco da barra de rolagem](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303&144;_ScrollbarArrowHover")  
  
 **Seta de rolagem**  
  
 Informações preliminares  
  
 `Environment.ScrollBarArrowMouseOverBackground`  
  
 Defina a mesma cor que a barra de rolagem.  
  
 Primeiro plano (glifos)  
  
 `Environment.ScrollBarArrowGlyphMouseOver`  
  
 **Pressionado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Barra de rolagem pressionado](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303&145;_ScrollbarPressed")  
  
 **Barra de rolagem**  
  
 Barra de Rolagem  
  
 `Environment.ScrollBarBackground`  
  
 Primeiro plano (miniatura)  
  
 `Environment.ScrollBarThumbPressedBackground`  
  
 ![Seta pressionada da barra de rolagem](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303&146;_ScrollbarArrowPressed")  
  
 **Seta de rolagem**  
  
 Informações preliminares  
  
 `Environment.ScrollBarArrowPressedBackground`  
  
 Defina a mesma cor scrollbar.  
  
 Primeiro plano (glifos)  
  
 `Environment.ScrollBarArrowGlyphPressed`  
  
###  <a name="a-namebkmktreeviewa-tree-view"></a><a name="BKMK_TreeView"></a>Exibição de árvore  
 Várias janelas de ferramenta, incluindo o Gerenciador de soluções, Server Explorer e Class View, implementam um esquema organizacional hierárquico cujas cores são controlados por nomes de cores na categoria de TreeView. Todos os itens em uma exibição de árvore têm cores de plano de fundo e texto. Itens que tem elementos filho aninhados também possuem glifos que indicam se o item está expandido ou recolhido.  
  
 ![Aplicar linhas vermelhas no modo de exibição de árvore](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303&147;_TreeViewRedline")  
  
 Use...  
 em qualquer lugar, você precisa implementar uma exibição organizacional hierárquica.  
  
 Não use...  
 -   para qualquer coisa que não seja semelhante a uma exibição de árvore.  
  
-   em qualquer combinação de plano de fundo/primeiro plano diferente do especificado.  
  
 **Padrão**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Exibição de árvore](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303&148;_TreeView")  
  
 Informações preliminares  
  
 `TreeView.Background`  
  
 Primeiro plano (texto)  
  
 `TreeView.Background`  
  
 Primeiro plano (glifos)  
  
 `TreeView.Glyph`  
  
 Borda  
  
 Nenhum  
  
 **Passe o mouse**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Exibição em foco em árvore](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303&149;_TreeViewHover")  
  
 Informações preliminares  
  
 `TreeView.Background`  
  
 Primeiro plano (texto)  
  
 `TreeView.Background`  
  
 Primeiro plano (glifos)  
  
 `TreeView.GlyphMouseOver`  
  
 Borda  
  
 Nenhum  
  
 **Arraste sobre**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Dragover de exibição de árvore](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303&150;_TreeViewDragOver")  
  
 Informações preliminares  
  
 `TreeView.DragOverItem`  
  
 Primeiro plano (texto)  
  
 `TreeView.DragOverItem`  
  
 Primeiro plano (glifos)  
  
 `TreeView.DragOverItemGlyph`  
  
 Borda  
  
 Nenhum  
  
 **Selecionado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Focada de exibição de árvore](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303&151;_TreeViewFocused")  
  
 **Com foco**  
  
 Informações preliminares  
  
 `TreeView.SelectedItemActive`  
  
 Primeiro plano (texto)  
  
 `TreeView.SelectedItemActive`  
  
 Primeiro plano (glifos)  
  
 `TreeView.SelectedItemActiveGlyph`  
  
 Borda  
  
 `TreeView.FocusVisualBorder`  
  
 ![Foco de exibição de árvore](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303&152;_TreeViewUnfocused")  
  
 **Foco**  
  
 Informações preliminares  
  
 `TreeView.SelectedItemInactive`  
  
 Primeiro plano (texto)  
  
 `TreeView.SelectedItemInactive`  
  
 Primeiro plano (glifos)  
  
 `TreeView.SelectedItemInactiveGlyph`  
  
 Borda  
  
 Nenhum  
  
 **Passe o mouse sobre selecionado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Com foco no foco de exibição de árvore](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303&153;_TreeViewFocusedHover")  
  
 **Com foco**  
  
 Informações preliminares  
  
 `TreeView.SelectedItemActive`  
  
 Primeiro plano (texto)  
  
 `TreeView.SelectedItemActive`  
  
 Primeiro plano (glifos)  
  
 `TreeView.SelectedItemActiveGlyphMouseOver`  
  
 Borda  
  
 Nenhum`TreeView.FocusVisualBorder`  
  
 ![Exibição sem foco no foco de árvore](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303&154;_TreeViewUnfocusedHover")  
  
 **Foco**  
  
 Informações preliminares  
  
 `TreeView.SelectedItemInactive`  
  
 Primeiro plano (texto)  
  
 `TreeView.SelectedItemInactive`  
  
 Primeiro plano (glifos)  
  
 `TreeView.SelectedItemActiveGlyphMouseOver`  
  
 Borda  
  
 Nenhum  
  
### <a name="button-controls"></a>Controles de botão  
 ![Aplicar linhas vermelhas no controle de botão](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303&155;_ButtonControlRedline")  
  
 Use...  
 para os botões corretamente o documento que você deseja integrar temas do Visual Studio (Light, escuro, azul ou um tema de alto contraste do sistema).  
  
 Não use...  
 para os botões que serão exibidos em um plano de fundo personalizado que não faz parte de um tema do Visual Studio.  
  
 **Padrão**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Botão](../../extensibility/ux-guidelines/media/0303-156_button.png "0303&156;_Button")  
  
 Botão  
  
 `CommonControls.Button`  
  
 Borda do botão  
  
 `CommonControls.ButtonBorder`  
  
 **Desabilitado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Botão desabilitado](../../extensibility/ux-guidelines/media/0303-157_buttondisabled.png "0303&157;_ButtonDisabled")  
  
 Botão  
  
 `CommonControls.ButtonDisabled`  
  
 Borda do botão  
  
 `CommonControls.ButtonBorderDisabled`  
  
 **Passe o mouse**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Botão em foco](../../extensibility/ux-guidelines/media/0303-158_buttonhover.png "0303&158;_ButtonHover")  
  
 Botão  
  
 `CommonControls.ButtonHover`  
  
 Borda do botão  
  
 `CommonControls.ButtonBorderHover`  
  
 **Pressionado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Botão pressionado](../../extensibility/ux-guidelines/media/0303-159_buttonpressed.png "0303&159;_ButtonPressed")  
  
 Botão  
  
 `CommonControls.ButtonPressed`  
  
 Borda do botão  
  
 `CommonControls.ButtonBorderPressed`  
  
 **Com foco**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Botão focado](../../extensibility/ux-guidelines/media/0303-160_buttonfocused.png "0303&160;_ButtonFocused")  
  
 Botão  
  
 `CommonControls.ButtonFocused`  
  
 Borda do botão  
  
 `CommonControls.ButtonBorderFocused`  
  
### <a name="check-box-controls"></a>Controles de caixa de seleção  
 ![Caixa de seleção Aplicar linhas vermelhas no](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303&161;_CheckboxRedline")  
  
 Use...  
 para controles de caixa de seleção contidos no documento bem.  
  
 Não use...  
 para qualquer interface de usuário que não é um controle de caixa de seleção.  
  
 **Padrão**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Caixa de seleção](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303&162;_Checkbox")  
  
 Informações preliminares  
  
 `CommonControls.CheckBoxBackground`  
  
 Borda  
  
 `CommonControls.CheckBoxBorder`  
  
 Texto  
  
 `CommonControls.CheckBoxText`  
  
 Glifo  
  
 `CommonControls.CheckBoxGlyph`  
  
 **Desabilitado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Caixa de seleção desabilitada](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303&163;_CheckboxDisabled")  
  
 Informações preliminares  
  
 `CommonControls.CheckBoxBackgroundDisabled`  
  
 Borda  
  
 `CommonControls.CheckBoxBorderDisabled`  
  
 Texto  
  
 `CommonControls.CheckBoxTextDisabled`  
  
 Glifo  
  
 `CommonControls.CheckBoxGlyphDisabled`  
  
 **Passe o mouse**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Caixa de seleção em foco](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303&164;_CheckboxHover")  
  
 Informações preliminares  
  
 `CommonControls.CheckBoxBackgroundHover`  
  
 Borda  
  
 `CommonControls.CheckBoxBorderHover`  
  
 Texto  
  
 `CommonControls.CheckBoxTextHover`  
  
 Glifo  
  
 `CommonControls.CheckBoxGlyphHover`  
  
 **Pressionado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Caixa de seleção pressionada](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303&165;_CheckboxPressed")  
  
 Informações preliminares  
  
 `CommonControls.CheckBoxBackgroundPressed`  
  
 Borda  
  
 `CommonControls.CheckBoxBorderPressed`  
  
 Texto  
  
 `CommonControls.CheckBoxTextPressed`  
  
 Glifo  
  
 `CommonControls.CheckBoxGlyphPressed`  
  
 **Com foco**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Caixa de seleção focada](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303&166;_CheckboxFocused")  
  
 Informações preliminares  
  
 `CommonControls.CheckBoxBackgroundFocused`  
  
 Borda  
  
 `CommonControls.CheckBoxBorderFocused`  
  
 Texto  
  
 `CommonControls.CheckBoxTextFocused`  
  
 Glifo  
  
 `CommonControls.CheckBoxGlyphFocused`  
  
### <a name="drop-boxcombo-box-controls"></a>Controles de caixa combo/caixa de soltar  
 ![Corte de funcionários da caixa de combinação/drop-down](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303&167;_DropDownComboBoxRedline")  
  
 Use...  
 para listas suspensas e combinação caixas que também são parte do documento.  
  
 Não use...  
 -   para qualquer interface do usuário que não é uma lista suspensa ou caixa de combinação.  
  
-   para uma [suspensa](../../misc/shared-colors.md#BKMK_CommandDropDown) ou [caixa de combinação](../../misc/shared-colors.md#BKMK_CommandComboBox) na barra de comandos.  
  
 **Padrão**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Caixa de combinação/drop-down](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303&168;_DropDownComboBox")  
  
 Informações preliminares  
  
 `CommonControls.ComboBoxBackground`  
  
 Borda  
  
 `CommonControls.ComboBoxBorder`  
  
 Texto  
  
 `CommonControls.ComboBoxText`  
  
 Separador  
  
 `CommonControls.ComboBoxSeparator`  
  
 Glifo  
  
 `CommonControls.ComboBoxGlyph`  
  
 Plano de fundo de glifo  
  
 `CommonControls.ComboBoxGlyphBackground`  
  
 **Desabilitado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Caixa de combinação/drop-down desabilitada](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303&169;_DropDownComboBoxDisabled")  
  
 Informações preliminares  
  
 `CommonControls.ComboBoxBackgroundDisabled`  
  
 Borda  
  
 `CommonControls.ComboBoxBorderDisabled`  
  
 Texto  
  
 `CommonControls.ComboBoxTextDisabled`  
  
 Separador  
  
 `CommonControls.ComboBoxSeparatorDisabled`  
  
 Glifo  
  
 `CommonControls.ComboBoxGlyphDisabled`  
  
 Plano de fundo de glifo  
  
 `CommonControls.ComboBoxGlyphBackgroundDisabled`  
  
 **Passe o mouse**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Caixa de combinação/drop-down em foco](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303&170;_DropDownComboBoxHover")  
  
 Informações preliminares  
  
 `CommonControls.ComboBoxBackgroundHover`  
  
 Borda  
  
 `CommonControls.ComboBoxBorderHover`  
  
 Texto  
  
 `CommonControls.ComboBoxTextHover`  
  
 Separador  
  
 `CommonControls.ComboBoxSeparatorHover`  
  
 Glifo  
  
 `CommonControls.ComboBoxGlyphHover`  
  
 Plano de fundo de glifo  
  
 `CommonControls.ComboBoxGlyphBackgroundHover`  
  
 **Pressionado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Caixa de combinação/drop-down pressionada](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303&171;_DropDownComboBoxPressed")  
  
 Informações preliminares  
  
 `CommonControls.ComboBoxBackgroundPressed`  
  
 Borda  
  
 `CommonControls.ComboBoxBorderPressed`  
  
 Texto  
  
 `CommonControls.ComboBoxTextPressed`  
  
 Separador  
  
 `CommonControls.ComboBoxSeparatorPressed`  
  
 Glifo  
  
 `CommonControls.ComboBoxGlyphPressed`  
  
 Plano de fundo de glifo  
  
 `CommonControls.ComboBoxGlyphBackgroundPressed`  
  
 **Com foco**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Caixa de combinação/drop-down focada](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303&172;_DropDownComboBoxFocused")  
  
 Informações preliminares  
  
 `CommonControls.ComboBoxBackgroundFocused`  
  
 Borda  
  
 `CommonControls.ComboBoxBorderFocused`  
  
 Texto  
  
 `CommonControls.ComboBoxTextFocused`  
  
 Separador  
  
 `CommonControls.ComboBoxSeparatorFocused`  
  
 Glifo  
  
 `CommonControls.ComboBoxGlyphFocused`  
  
 Plano de fundo de glifo  
  
 `CommonControls.ComboBoxGlyphBackgroundFocused`  
  
 **Seleção de entrada de texto**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Entrada de texto da caixa de combinação/drop-down](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303&173;_DropDownComboBoxTextInput")  
  
 Realçar  
  
 `CommonControls.ComboBoxTextInputSelection`  
  
 **Pressionado – modo de exibição de item de lista**  
  
 ![Exibição de lista da caixa de combinação/drop-down](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303&174;_DropDownComboBoxListView")  
  
 Informações preliminares  
  
 `CommonControls.ComboBoxListBackground`  
  
 `CommonControls.ComboBoxListBackgroundHover`  
  
 `CommonControls.ComboBoxListItemBackgroundPressed`  
  
 `CommonControls.ComboBoxListItemBackgroundFocused`  
  
 Borda  
  
 `CommonControls.ComboBoxListBorder`  
  
 `CommonControls.ComboBoxListBorderHover`  
  
 `CommonControls.ComboBoxListBorderPressed`  
  
 `CommonControls.ComboBoxListBorderFocused`  
  
 Texto do item  
  
 `CommonControls.ComboBoxListItemText`  
  
 `CommonControls.ComboBoxListItemTextHover`  
  
 `CommonControls.ComboBoxListItemTextPressed`  
  
 `CommonControls.ComboBoxListItemTextFocused`  
  
 Plano de fundo sombra  
  
 `CommonControls.ComboBoxListBackgroundShadow`  
  
### <a name="tabular-data-grid-controls"></a>Controles de dados tabulares (grade)  
 Controles de dados tabulares, também conhecido como controles de grade, são controles comuns do Visual Studio que pode ser usado para apresentar grandes quantidades de dados em várias colunas. Controles de dados de tabela padrão podem ser encontrados em vários locais dentro do Visual Studio: a janela da ferramenta de lista de erros, relatórios do IntelliTrace e exibição de heap de memória, entre outros. Sempre use os controles de dados de tabela padrão fornecidos. Em alguns casos raros, talvez você não tenha acesso aos controles de dados de tabela padrão. Nessas situações, use os seguintes nomes de token para garantir que a interface do usuário é consistente com outros controles de dados tabulares no Visual Studio.  
  
 ![Corte de funcionários em dados tabulares (controle de grade)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303&197;_TabularDataGridControlRedline")  
  
 Use...  
 para tabela ou controles de grade.  
  
 Não use...  
 para qualquer interface de usuário que não é um controle tabular ou de grade.  
  
#### <a name="column-headers"></a>Cabeçalhos de coluna  
 Cabeçalhos de coluna consistem em um plano de fundo, uma borda, o texto do título e um glifo opcional geralmente usado quando uma grade é classificada pela coluna.  
  
 Estado  
  
 Elemento  
  
 Nome de token: Category.color  
  
 Padrão  
  
 Informações preliminares  
  
 `Header.Default`  
  
 Primeiro plano (texto)  
  
 `Environment.CommandBarTextActive`  
  
 Primeiro plano (glifos)  
  
 `Header.Glyph`  
  
 Borda  
  
 `Header.SeparatorLine`  
  
 Focalizar  
  
 Informações preliminares  
  
 `Header.MouseOver`  
  
 Primeiro plano (texto)  
  
 `Environment.CommandBarTextHover`  
  
 Primeiro plano (glifos)  
  
 `Header.MouseOverGlyph`  
  
 Borda  
  
 `Header.SeparatorLine`  
  
 Pressionado  
  
 Informações preliminares  
  
 `CommonControls.CheckBoxBackgroundPressed`  
  
 Primeiro plano (texto)  
  
 `CommonControls.CheckBoxBorderPressed`  
  
 Primeiro plano (glifos)  
  
 `CommonControls.CheckBoxTextPressed`  
  
 Borda  
  
 `CommonControls.CheckBoxGlyphPressed`  
  
#### <a name="list-view-items"></a>Exibir itens de lista  
 Exibir itens de lista consistem em um plano de fundo e o conteúdo. O conteúdo pode ser texto, um ícone ou ambos.  
  
 Estado  
  
 Elemento  
  
 Nome de token: Category.color  
  
 Padrão  
  
 Informações preliminares  
  
 Transparente  
  
 Primeiro plano (texto)  
  
 `Environment.CommandBarTextActive`  
  
 Borda  
  
 Nenhum  
  
 Selecionado (ativo)  
  
 Informações preliminares  
  
 `TreeView.SelectedItemActive`  
  
 Primeiro plano (texto)  
  
 `TreeView.SelectedItemActiveText`  
  
 Borda  
  
 Nenhum  
  
 Selecionado (inativo)  
  
 Informações preliminares  
  
 `TreeView.SelectedItemInactive`  
  
 Primeiro plano (texto)  
  
 `TreeView.SelectedItemInactiveText`  
  
 Borda  
  
 Nenhum  
  
## <a name="manifest-designer"></a>Designer de manifesto  
 O Designer de manifesto foi projetado como uma maneira de torná-lo mais fácil de editar o arquivo de manifesto em projetos do Windows 8 e Windows Phone 8. Embora não haja nenhuma estrutura compartilhada disponíveis para consumo, pode ser apropriado para a correspondência entre as cores de guias de navegação/orientação e a estrutura geral e um layout de design. Para obter mais informações sobre os detalhes de layout, consulte [Layout para o Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
 ![Aplicar linhas vermelhas no Designer de manifesto](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303&175;_ManifestDesignerRedline")  
  
 Use...  
 -   para designers que são semelhantes para o Designer de manifesto.  
  
-   em vez de usar os controles comuns do guia na parte superior de um editor no documento bem.  
  
 Não use...  
 -   Se você tiver mais de seis guias.  
  
-   para qualquer interface do usuário não estruturado como o Designer de manifesto.  
  
 Estado  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 Padrão (selecionado)  
  
 Tabulação  
  
 Informações preliminares  
  
 `ManifestDesigner.TabActive`  
  
 Borda  
  
 Nenhum  
  
 Painel de descrição  
  
 Informações preliminares  
  
 `ManifestDesigner.DescriptionPane`  
  
 Página de conteúdo  
  
 Informações preliminares  
  
 `ManifestDesigner.Background`  
  
 Texto de Ajuda da caixa de diálogo  
  
 `ManifestDesigner.WatermarkText`  
  
 Esse nome de token não coincide com a função.  
  
 Não selecionado  
  
 Tabulação  
  
 Informações preliminares  
  
 `ManifestDesigner.Tab.Inactive`  
  
 Focalizar  
  
 Tabulação  
  
 Informações preliminares  
  
 `ManifestDesigner.Tab.Mouseover`  
  
## <a name="tagging"></a>Marcação  
 Visual Studio oferece suporte à marcação, que permite que um usuário declarar as palavras-chave pesquisáveis para fins de acompanhamento. Por exemplo, os desenvolvedores e gerentes de projeto podem usar o Team Foundation Server (TFS) para marcar itens de trabalho. As tabelas a seguir dar nomes de cor para a marca em si e o glifo "fechar o ícone" que aparece em foco e estados selecionados.  
  
 ![Corte de funcionários em marcação](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303&176;_TaggingRedline")  
  
 Use...  
 interface do usuário que dá suporte à marcação.  
  
 Não use...  
 para qualquer outro tipo de interface do usuário.  
  
### <a name="tag"></a>Marca  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Marca](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303&177;_Tag")  
  
 **Padrão**  
  
 Informações preliminares  
  
 `Tag.Background`  
  
 Primeiro plano (texto)  
  
 `Tag.Background`  
  
 ![Marca focalizar](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303&178;_TagHover")  
  
 **Passe o mouse**  
  
 Informações preliminares  
  
 `Tag.HoverBackground`  
  
 Primeiro plano (texto)  
  
 `Tag.HoverBackgroundText`  
  
 ![Marca pressionada](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303&179;_TagPressed")  
  
 **Pressionado**  
  
 Informações preliminares  
  
 `Tag.PressedBackground`  
  
 Primeiro plano (texto)  
  
 `Tag.PressedBackgroundText`  
  
 ![Marca selecionada](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303&180;_TagSelected")  
  
 **Selecionado**  
  
 Informações preliminares  
  
 `Tag.SelectedBackground`  
  
 Primeiro plano (texto)  
  
 `Tag.SelectedBackgroundText`  
  
### <a name="glyph-close-icon"></a>Glifo (ícone de fechar)  
 **Padrão**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Marca (glifos)](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303&181;_TagGlyph")  
  
 **Padrão (padrão de marca)**  
  
 Informações preliminares  
  
 N/A  
  
 Primeiro plano (glifos)  
  
 `Tag.TagHoverGlyph`  
  
 **Passe o mouse**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Marca (glifos) ao focar](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303&182;_TagGlyphHover")  
  
 **Passe o mouse (padrão de marca)**  
  
 Informações preliminares  
  
 `Tag.TagHoverGlyphHoverBackground`  
  
 Primeiro plano (glifos)  
  
 `Tag.TagHoverGlyphHover`  
  
 Borda  
  
 `Tag.TagHoverGlyphHoverBorder`  
  
 **Pressionado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Marca (glifos) pressionada](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303&183;_TagGlyphPressed")  
  
 **Pressionado (padrão de marca)**  
  
 Informações preliminares  
  
 `Tag.TagHoverGlyphPressedBackground`  
  
 Primeiro plano (glifos)  
  
 `Tag.TagHoverGlyphPressed`  
  
 Borda  
  
 `Tag.TagHoverGlyphPressedBorder`  
  
 **Marca selecionada/glifos padrão**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Marca selecionada](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303&184;_TagSelected")  
  
 **Padrão (tag selecionada)**  
  
 Informações preliminares  
  
 N/A  
  
 Primeiro plano (glifos)  
  
 `Tag.TagSelectedGlyph`  
  
 **Em foco selecionado/glifo de marca**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Marca selecionada no foco](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303&185;_TagSelectedHover")  
  
 **Passe o mouse (tag selecionada)**  
  
 Informações preliminares  
  
 `Tag.TagSelectedGlyphHoverBackground`  
  
 Primeiro plano (glifos)  
  
 `Tag.TagSelectedGlyphHover`  
  
 Borda  
  
 `Tag.TagSelectedGlyphHoverBorder`  
  
 **Selecionado/marca pressionada**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Marca selecionada pressionado](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303&186;_TagSelectedPressed")  
  
 **Pressionado (tag selecionada)**  
  
 Informações preliminares  
  
 `Tag.TagSelectedGlyphPressedBackground`  
  
 Foreground(glyph)  
  
 `Tag.TagSelectedGlyphPressed`  
  
 Borda  
  
 `Tag.TagSelectedGlyphPressedBorder`  
  
## <a name="shell"></a>Shell  
  
### <a name="background"></a>Informações preliminares  
 O plano de fundo do ambiente consiste em duas camadas. A camada inferior é uma cor sólida que abrange todo o IDE. A camada superior se encaixa em prateleira comando e entre os canais de ocultação automática de janela de ferramenta nas bordas esquerdas e direita do IDE. A partir do Visual Studio 2013, as camadas de plano de fundo superior e inferior são definidas para a mesma cor nos temas claro e escuro.  
  
 ![Aplicar linhas vermelhas no plano de fundo do shell](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303&187;_ShellBackgroundRedline")  
  
 Use...  
 para os locais que você deseja corresponder o plano de fundo do ambiente do Visual Studio.  
  
 Não use...  
 -   como um preenchimento de locais que não são superfícies de plano de fundo.  
  
-   como um plano de fundo no qual você deseja colocar os elementos de primeiro plano.  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 Camada inferior  
  
 Informações preliminares  
  
 `Environment.EnvironmentBackground`  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 Camada superior  
  
 Informações preliminares  
  
 *Marcas de gradiente definido como o mesmo valor de cor em temas claro de 2013 do Visual Studio e escuro.*  
  
 `Environment.EnvironmentBackgroundGradientBegin`  
  
 `Environment.EnvironmentBackgroundGradientEnd`  
  
 `Environment.EnvironmentBackgroundGradientMiddle1`  
  
 `Environment.EnvironmentBackgroundGradientMiddle2`  
  
### <a name="command-shelf"></a>Prateleira de comando  
 Dois conjuntos de nomes de token são usados para os planos de fundo de prateleira de comando: um conjunto para onde fica a barra de menus e uma para onde as barras de comando ficam. Um grupo da barra de comando individual tem seus próprios valores de cor do plano de fundo, são discutidos em mais detalhes na seção "barra de comandos". Barra de menus da barra e comando texto é abordado nas seções de barra de menu e o comando, respectivamente.  
  
 ![Corte de funcionários de prateleira do comando](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303&188;_CommandShelfRedline")  
  
 Use...  
 -   para as áreas onde você coloca menus ou barras de ferramentas.  
  
-   com o plano de fundo correto /? combinação de nome de token de primeiro plano.  
  
 Não use...  
 para as áreas que não são semelhantes a uma prateleira de comando.  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 Barra de menus  
  
 Informações preliminares  
  
 *Marcas de gradiente definido como o mesmo valor de cor em temas claro de 2013 do Visual Studio e escuro.*  
  
 `Environment.CommandShelfHighlightGradientBegin`  
  
 `Environment.CommandShelfHighlightGradientMiddle`  
  
 `Environment.CommandShelfHighlightGradientEnd`  
  
 Barra de comandos  
  
 Informações preliminares  
  
 *Marcas de gradiente definido como o mesmo valor de cor em temas claro de 2013 do Visual Studio e escuro.*  
  
 `Environment.CommandShelfBackgroundGradientBegin`  
  
 `Environment.CommandShelfBackgroundGradientMiddle`  
  
 `Environment.CommandShelfBackgroundGradientEnd`  
  
## <a name="toolbox"></a>Caixa de Ferramentas  
 A caixa de ferramentas é um das janelas de ferramentas comum que é usado com mais frequência no Visual Studio. Ele é essencialmente um controle de árvore com um tema especial e um estilo aplicado.  
  
 ![Corte de funcionários da caixa de ferramentas](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303&189;_ToolboxRedline")  
  
 Use...  
 Quando você está criando uma janela de ferramenta deve sempre ser consistente com a caixa de ferramentas do shell.  
  
 Não use...  
 para qualquer coisa que não é semelhante à caixa de ferramentas da interface do usuário, ou se você não tiver certeza se a interface do usuário terá problemas se a caixa de ferramentas de shell cores de alteração.  
  
 **Padrão**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Nó pai de caixa de ferramentas](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303&190;_ToolboxParentNode")  
  
 **Nó pai**  
  
 ![Nó filho de caixa de ferramentas](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303&191;_ToolboxChildNode")  
  
 **Nó filho**  
  
 Informações preliminares  
  
 `Environment.ToolboxContent`  
  
 Títulos  
  
 `Environment.ToolWindowBackground`  
  
 Itens individuais ou toda a janela se não há controles disponíveis  
  
 Borda  
  
 Nenhum  
  
 Primeiro plano (glifos)  
  
 `Environment.ToolboxContent`  
  
 Primeiro plano (texto)  
  
 `Environment.ToolboxContent`  
  
 **Passe o mouse**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Nó filho de caixa de ferramentas no foco](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303&192;_ToolboxChildNodeHover")  
  
 **Foco da caixa de ferramentas no nó filho**  
  
 Informações preliminares  
  
 `Environment.ToolboxContentMouseOver`  
  
 Somente os itens individuais  
  
 Borda  
  
 Nenhum  
  
 Primeiro plano (texto)  
  
 `Environment.ToolboxContentMouseOver`  
  
 Somente os itens individuais  
  
 **Selecionado**  
  
 Componente  
  
 Elemento  
  
 Nome de token: Category.color  
  
 ![Nó pai de caixa de ferramentas voltado para](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303&193;_ToolboxParentNodeFocused")  
  
 **Nó pai de foco**  
  
 ![Foco do nó filho de caixa de ferramentas](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303&194;_ToolboxChildNodeFocused")  
  
 **Nó filho de foco**  
  
 Informações preliminares  
  
 `TreeView.SelectedItemActive`  
  
 De [exibição em árvore](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) categoria  
  
 Borda  
  
 `TreeView.FocusVisualBorder`  
  
 De [exibição em árvore](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) categoria  
  
 Primeiro plano (glifos)  
  
 `TreeView.SelectedItemActive`  
  
 De [exibição em árvore](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) categoria  
  
 Primeiro plano (texto)  
  
 `TreeView.SelectedItemActive`  
  
 De [exibição em árvore](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) categoria  
  
 ![Nó pai da caixa de ferramentas foco](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303&195;_ToolboxParentNodeUnfocused")  
  
 **Nó pai de foco**  
  
 ![Nó filho da caixa de ferramentas foco](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303&196;_ToolboxChildNodeUnfocused")  
  
 **Nó filho sem foco**  
  
 Informações preliminares  
  
 `TreeView.SelectedItemInactive`  
  
 De [exibição em árvore](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) categoria  
  
 Borda  
  
 Nenhum  
  
 Primeiro plano (glifos)  
  
 `TreeView.SelectedItemInactive`  
  
 De [exibição em árvore](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) categoria  
  
 Primeiro plano (texto)  
  
 `TreeView.SelectedItemInactive`  
  
 De [exibição em árvore](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) categoria
