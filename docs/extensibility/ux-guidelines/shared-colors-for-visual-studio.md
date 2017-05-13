---
title: Compartilhado cores para o Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 04/26/2017
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9524ecc3cadef58821fba857de8e82e59eea9b43
ms.openlocfilehash: 027e57a8d6ba4b4d317289cbdb74aa064de2ef4e
ms.contentlocale: pt-br
ms.lasthandoff: 05/04/2017

---
# <a name="shared-colors-for-visual-studio"></a>Cores de compartilhado para o Visual Studio
Quando você estiver criando uma interface do usuário que usa os elementos comuns de shell do Visual Studio, ou você deseja que o elemento de interface para ser consistente com recursos semelhantes, use nomes de token existentes nos arquivos de definição de pacote para escolher e atribuir cores. Isso garante que a interface do usuário permanece consistente com o ambiente geral do Visual Studio e que atualiza automaticamente quando os temas são adicionados ou atualizados.  

Este artigo descreve os elementos de interface de usuário comuns e os nomes de token que eles usam, que você pode fazer referência ao compilar semelhante da interface do usuário. Para obter informações específicas sobre como acessar esses tokens de cor, consulte [o serviço de VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  

Certifique-se de usar nomes de token corretamente:  

-   **Use nomes de token com base em função, não na própria cor.** As cores compartilhadas comuns são associadas aos elementos de interface específica e destinam-se somente a ser usado para os recursos idênticos ou semelhantes. Por exemplo, não reutilize a cor de uma caixa de combinação pressionado para a animação de progresso giratório só porque você gosta de cor. As funções de caixa de combinação e a animação são diferentes, e se a cor associados com as alterações de caixa de combinação, ele pode não ser mais uma cor apropriada para seu elemento de animação. O uso consistente de cor ajuda a orientar os usuários e evitar confusão.  

-   **Use cores de plano de fundo e texto da combinação correta.** Cores de plano de fundo que se destinam a ser usado com texto terá uma cor de texto associada. Não use cores de texto que não seja o que é especificado para esse plano de fundo. Se não houver uma cor de texto associada, não use essa cor de plano de fundo para qualquer área em que você pretende exibir texto. Outras combinações de cores de texto e plano de fundo podem resultar em uma interface ilegível.  

-   **Use cores de controle que são apropriadas para seu local.** Em alguns estados, alguns controles do Visual Studio não tem borda separada e cores de plano de fundo. Em vez disso, selecione as cores de superfícies por trás deles. Certifique-se de que você sempre use os nomes de token que são apropriados para o local onde você está colocando o controle.  

> [!IMPORTANT]
> Não use tokens localizadas nas categorias de "Página inicial" ou "Cider".  

## <a name="common-shared-controls"></a>Controles comuns do compartilhado

Quando você usar uma barra de comandos padrão do Visual Studio em seu recurso, você terá acesso aos controles de shell com estilo. Você não deve re-modelo desses controles comuns. No entanto, se você precisar criar uma barra de comando, talvez seja necessário criar controles personalizados também. Nesse caso, certifique-se de usar os nomes de token corretos para cada um dos seguintes controles de forma que a interface do usuário é consistente com o restante do Visual Studio.

### <a name="button-controls"></a>Controles de botão

![Aplicar linhas vermelhas no controle de botão](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303 155_ButtonControlRedline")

| Uso... | Não use... |
| --- | --- |
| ... para botões corretamente o documento que você deseja integrar com temas do Visual Studio (claro, escuro, azul ou um tema de alto contraste do sistema). | ... para os botões que serão exibidos em um plano de fundo personalizado que não faz parte de um tema do Visual Studio. |

**Botão: estado padrão**

![Botão padrão](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03.Button.Standard")<br />Botão padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Botão | `CommonControls.Button` |
| Borda do botão | `CommonControls.ButtonBorder` |

**Botão: estado padrão**

![Botão padrão](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03.Button.Default")<br />Botão padrão

| Elemento | Nome do token: Category.color | 
| --- | --- | 
| Botão | `CommonControls.ButtonDefault` |
| Borda do botão | `CommonControls.ButtonBorderDefault` |

**Botão: estado desabilitado**  

![Botão desabilitado](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.Button.Disabled")<br />Botão desabilitado  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Botão | `CommonControls.ButtonDisabled` |
| Borda do botão | `CommonControls.ButtonBorderDisabled` |

**Botão: estado de foco**  

![Botão em foco](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />Botão em foco  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Botão | `CommonControls.ButtonHover` |
| Borda do botão | `CommonControls.ButtonBorderHover` |

**Botão: estado pressionado**  

![Botão pressionado](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03.Button.Pressed")<br />Botão pressionado  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Botão | `CommonControls.ButtonPressed` |
| Borda do botão | `CommonControls.ButtonBorderPressed` |

**Botão: estado de foco**  

![Botão focalizado](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.Focused")<br />Botão focalizado  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Botão | `CommonControls.ButtonFocused` |
| Borda do botão | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Controles de caixa de seleção  
![Caixa de seleção (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303-161_CheckboxRedline")<br />Caixa de seleção (corte de funcionários)  

| Uso... | Não use... |
| --- | --- |
| ... para controles de caixa de seleção contidos no documento bem. | ... para qualquer interface de usuário que não é um controle de caixa de seleção. |

**Caixa de seleção: padrão de estado**  

![Caixa de seleção](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303-162_Checkbox")<br />Caixa de seleção padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `CommonControls.CheckBoxBackground` |
| Borda | `CommonControls.CheckBoxBorder` |
| Texto | `CommonControls.CheckBoxText` |
| Glifo | `CommonControls.CheckBoxGlyph` |

**Caixa de seleção: estado desabilitado**  

![Caixa de seleção desabilitada](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303-163_CheckboxDisabled")<br />Caixa de seleção desabilitada  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `CommonControls.CheckBoxBackgroundDisabled` |
| Borda | `CommonControls.CheckBoxBorderDisabled` |
| Texto | `CommonControls.CheckBoxTextDisabled` |
| Glifo | `CommonControls.CheckBoxGlyphDisabled` |

**Caixa de seleção: passe o estado**  

 ![Caixa de seleção em foco](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303-164_CheckboxHover")<br />Caixa de seleção em foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `CommonControls.CheckBoxBackgroundHover` |
| Borda | `CommonControls.CheckBoxBorderHover` |
| Texto | `CommonControls.CheckBoxTextHover` |
| Glifo | `CommonControls.CheckBoxGlyphHover` |  

**Caixa de seleção: pressionado estado**  

![Caixa de seleção pressionada](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303-165_CheckboxPressed")<br />Caixa de seleção pressionada  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `CommonControls.CheckBoxBackgroundPressed` |
| Borda | `CommonControls.CheckBoxBorderPressed` |
| Texto | `CommonControls.CheckBoxTextPressed` |
| Glifo | `CommonControls.CheckBoxGlyphPressed` |  

**Caixa de seleção: voltada para o estado**  

![Caixa de seleção focada](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303-166_CheckboxFocused")<br />Caixa de seleção focada  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `CommonControls.CheckBoxBackgroundFocused` |
| Borda | `CommonControls.CheckBoxBorderFocused` |
| Texto | `CommonControls.CheckBoxTextFocused` |
| Glifo | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Listas suspensas e combinação caixas
![Caixa de combinação/drop-down (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")<br />Caixa de combinação/drop-down (corte de funcionários)  

| Uso... | Não use... |
| --- | --- |
| ... para listas suspensas e combinação das caixas no documento bem. | ... para qualquer interface de usuário que não é uma lista suspensa ou caixa de combinação. |  
| | ... para a barra de comandos [suspensas](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) ou [caixas de combinação](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox). |

**Listas suspensas e combinação caixas: padrão de estado**  

![Caixa de combinação/drop-down padrão](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303-168_DropDownComboBox")<br />Caixa de combinação/drop-down padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `CommonControls.ComboBoxBackground` |
| Borda | `CommonControls.ComboBoxBorder` |
| Texto | `CommonControls.ComboBoxText` |
| Separador | `CommonControls.ComboBoxSeparator` |
| Glifo | `CommonControls.ComboBoxGlyph` |
| Plano de fundo de glifo | `CommonControls.ComboBoxGlyphBackground` |

**Listas suspensas e combinação caixas: estado desabilitado**  

![Caixa de combinação/drop-down desabilitada](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")<br />Caixa de combinação/drop-down desabilitada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `CommonControls.ComboBoxBackgroundDisabled` |
| Borda | `CommonControls.ComboBoxBorderDisabled` |
| Texto | `CommonControls.ComboBoxTextDisabled` |
| Separador | `CommonControls.ComboBoxSeparatorDisabled` |
| Glifo | `CommonControls.ComboBoxGlyphDisabled` |
| Plano de fundo de glifo | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Listas suspensas e combinação caixas: passe o estado**  

![Caixa de combinação/drop-down em foco](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")<br />Caixa de combinação/drop-down em foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `CommonControls.ComboBoxBackgroundHover` |
| Borda | `CommonControls.ComboBoxBorderHover` |
| Texto | `CommonControls.ComboBoxTextHover` |
| Separador | `CommonControls.ComboBoxSeparatorHover` |
| Glifo | `CommonControls.ComboBoxGlyphHover` |
| Plano de fundo de glifo | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Listas suspensas e combinação caixas: pressionado estado**  

![Caixa de combinação/drop-down de pressionado](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")<br />Caixa de combinação/drop-down de pressionado  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `CommonControls.ComboBoxBackgroundPressed` |
| Borda | `CommonControls.ComboBoxBorderPressed` |
| Texto | `CommonControls.ComboBoxTextPressed` |
| Separador | `CommonControls.ComboBoxSeparatorPressed` |
| Glifo | `CommonControls.ComboBoxGlyphPressed` |
| Plano de fundo de glifo | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Exibição de item de lista de caixas de listas suspensas e combinação: pressionado estado**  

 ![Caixa de combinação/drop-down pressionado o modo de exibição de item de lista](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")<br />Caixa de combinação/drop-down pressionado o modo de exibição de item de lista  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares |  `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Borda | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Texto do item | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Plano de fundo sombra | `CommonControls.ComboBoxListBackgroundShadow` |

**Listas suspensas e combinação caixas: voltada para o estado**  

![Caixa de combinação/drop-down com foco](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")<br />Caixa de combinação/drop-down com foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `CommonControls.ComboBoxBackgroundFocused` |
| Borda | `CommonControls.ComboBoxBorderFocused` |
| Texto | `CommonControls.ComboBoxTextFocused` |
| Separador | `CommonControls.ComboBoxSeparatorFocused` |
| Glifo | `CommonControls.ComboBoxGlyphFocused` |
| Plano de fundo de glifo | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Listas suspensas e combinação caixas: seleção de entrada de texto**  

![Seleção de entrada de texto da caixa de combinação/drop-down](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")<br />Seleção de entrada de texto da caixa de combinação/drop-down  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Realçar | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Controles de dados de tabela (grade)  
Controles de dados de tabela, também conhecido como controles de grade, são controles comuns para Visual Studio que pode ser usado para apresentar grandes quantidades de dados em várias colunas. Controles de dados de tabela padrão podem ser encontrados em vários locais dentro do Visual Studio: a janela da ferramenta de lista de erros, relatórios do IntelliTrace e exibição de heap de memória, entre outros. Sempre use os controles de dados de tabela padrão fornecidos. Em alguns casos raros, talvez você não tenha acesso aos controles de dados de tabela padrão. Nessas situações, use os seguintes nomes de token para garantir que a interface do usuário é consistente com outros controles de dados de tabela no Visual Studio.  

![Controle de grade/dados tabulares (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")<br />Controle de grade/dados tabulares (corte de funcionários)

| Uso... | Não use... |
| --- | --- |
| ... para tabela ou controles de grade. | ... para qualquer interface de usuário que não é um tabela ou controle de grade. |

#### <a name="column-headers"></a>Cabeçalhos de coluna  
Cabeçalhos de coluna consistem em um plano de fundo, uma borda, o texto do título e um glifo opcional que geralmente usado quando uma grade é classificada pela coluna.  

**Cabeçalho de coluna: padrão de estado**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Header.Default` |
| Em primeiro plano (texto) | `Environment.CommandBarTextActive` |
| Em primeiro plano (glifo) | `Header.Glyph` |
| Borda | `Header.SeparatorLine` |

**Cabeçalho de coluna: passe o estado**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Header.MouseOver` |
| Em primeiro plano (texto) | `Environment.CommandBarTextHover` |
| Em primeiro plano (glifo) | `Header.MouseOverGlyph` |
| Borda | `Header.SeparatorLine` |

**Cabeçalho de coluna: pressionado estado**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `CommonControls.CheckBoxBackgroundPressed` |
| Em primeiro plano (texto) | `CommonControls.CheckBoxBorderPressed` |
| Em primeiro plano (glifo) | `CommonControls.CheckBoxTextPressed` |
| Borda | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Itens de exibição de lista  
 Itens de exibição de lista consistem em um plano de fundo e o conteúdo. O conteúdo pode ser texto, um ícone ou ambos.  

**Itens de exibição de lista: padrão de estado**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | Transparente |
| Em primeiro plano (texto) | `Environment.CommandBarTextActive` |
| Borda | Nenhum |

**Itens de exibição de lista: estado ativo**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `TreeView.SelectedItemActive` |
| Em primeiro plano (texto) | `TreeView.SelectedItemActiveText` |
| Borda | Nenhum |

**Itens de exibição de lista: estado inativo**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `TreeView.SelectedItemInactive` |
| Em primeiro plano (texto) | `TreeView.SelectedItemInactiveText` |
| Borda | Nenhum |  

### <a name="ui-text"></a>Texto de interface do usuário

#### <a name="instructional-text"></a>Texto de instrução
Texto de instrução fornece uma explicação proeminente principal do que fazer em uma página da caixa de diálogo ou documento.

![Texto de instrução padrão](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Texto de instrução padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Em primeiro plano (texto) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Texto de instrução secundário
Nas páginas do documento com muitos de texto e controles, algum texto das instruções usa um valor de cor diferente. Isso ajuda a transmitir quais informações são mais importantes e diminuir a densidade geral dos elementos da interface do usuário. (Consulte também a seção no texto de dica abaixo.)

![Texto de instrução secundário](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Texto de instrução secundário

| Elemento | Nome do token: Category.color |
| --- | --- |
| Em primeiro plano (texto) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Texto de dica
Texto de dica aparece em um controle vazio, abaixo de um controle, ou em uma superfície de documento vazio para mostrar ao usuário o que fazer em seguida. Você pode usar o texto de dica com planos de fundo de uma janela ou controle.

**Texto de dica de padrão**

![Texto de dica de padrão](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Texto de dica de padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Em primeiro plano (texto) | `Environment.ControlEditHintText` |

**Texto de dica necessária**

![Texto de dica necessária](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Texto de dica necessária

| Elemento | Nome do token: Category.color |
| --- | --- |
| Em primeiro plano (texto) | `Environment.ControlRequiredHintText` |
| Informações preliminares | `Environment.ControlRequiredBackground` |

**Texto de controle de caixa de pesquisa**

> Consulte [caixas de pesquisa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) para outros tokens de cor relacionados ao controle de pesquisa.

![Texto de controle de caixa de pesquisa](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Texto de controle de caixa de pesquisa

| Elemento | Nome do token: Category.color |
| --- | --- |
| Em primeiro plano (texto) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Hiperlink  
O hiperlink é um controle que não tenha um par de primeiro e segundo plano. Em todos os casos, use a cor do hiperlink do primeiro plano, que será exibido corretamente nos planos de fundo escuros, cinzas e brancos. Se você não usar o token de cor para o controle hyperlink, você verá a cor padrão do sistema para "pressionado", que pisca vermelho. É o sinal de que o controle não está usando o token de cor ambiente correto.  

![Hiperlink (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303-133_HyperlinkRedline")<br />Hiperlink (corte de funcionários)

| Uso... | Não use... |
| --- | --- |
| ... quando você precisa criar um hiperlink personalizado. | ... para qualquer coisa que não é um hiperlink. |

**Hiperlink: estado padrão**  

![Hiperlink padrão](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303-134_Hyperlink")<br />Hiperlink padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Em primeiro plano (texto) | `Environment.PanelHyperlink` |

**Hiperlink: estado de foco**

![Hiperlink em foco](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303-135_HyperlinkHover")<br />Hiperlink em foco  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Em primeiro plano (texto) | `Environment.PanelHyperlinkHover` |

**Hiperlink: estado pressionado**

![Hiperlink pressionado](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303-136_HyperlinkPressed")<br />Hiperlink pressionado  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Em primeiro plano (texto) | `Environment.PanelHyperlinkPressed` |

**Hiperlink: estado desabilitado**

![Hiperlink desabilitado](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303-137_HyperlinkDisabled")<br />Hiperlink desabilitado  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Em primeiro plano (texto) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Infobars  
Infobars são usados para fornecer mais informações sobre um determinado contexto e sempre serão exibidos na parte superior de uma janela de documento ou janela de ferramenta.  

![Barra de informações (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303-138_InfobarRedline")<br />Barra de informações (corte de funcionários)

| Uso... | Não use... |
| --- | --- |
| ... ao criar infobars personalizados. | ... para elementos de interface do usuário que não são semelhantes a uma barra de informações. |

**Barra de informações: estado padrão**

![Barra de informações de padrão](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303-139_Infobar")<br />Barra de informações de padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `InfoBar.InfoBarBackground` |
| Em primeiro plano (texto) | `InfoBar.InfoBar` |
| Borda | `InfoBar.InfoBarBorder` |

**Fechar a barra de informações (&times;) botão: padrão de estado**

![Padrão Fechar barra de informações (&times;) botão](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Padrão Fechar barra de informações (&times;) botão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `InfoBar.CloseButton` |
| Borda | `InfoBar.CloseButtonBorder` |
| Glifo | `InfoBar.CloseButtonGlyph` |

**Fechar a barra de informações (&times;) botão: passe o estado**

![Fechar a barra de informações (&times;) botão em foco](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Fechar a barra de informações (&times;) botão em foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `InfoBar.CloseButtonHover` |
| Borda | `InfoBar.CloseButtonHoverBorder` |
| Glifo | `InfoBar.CloseButtonHoverGlyph` |

**Fechar a barra de informações (&times;) botão: pressionado estado**

![Pressionado Fechar barra de informações (&times;) botão](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Pressionado Fechar barra de informações (&times;) botão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `InfoBar.CloseButtonDown` |
| Borda | `InfoBar.CloseButtonDownBorder` |
| Glifo | `InfoBar.CloseButtonDownGlyph` |

**Botão de hiperlink da barra de informações: padrão de estado**

![Botão de hiperlink de barra de informações de padrão](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Botão de hiperlink de barra de informações de padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Em primeiro plano (texto) | `InfoBar.Hyperlink` |

**Botão de hiperlink da barra de informações: passe o estado**

![Botão de hiperlink da barra de informações em foco](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Botão de hiperlink da barra de informações em foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Em primeiro plano (texto) | `Infobar.HyperlinkMouseOver`<br />(Com sublinhado) |

**Botão de hiperlink da barra de informações: pressionado estado**

![Botão de hiperlink pressionado barra de informações](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Botão de hiperlink pressionado barra de informações

| Elemento | Nome do token: Category.color |
| --- | --- |
| Em primeiro plano (texto) | `Infobar.HyperlinkMouseDown`<br />(Com sublinhado) |

**Barra de informações embutido hyperlink (dentro de uma sentença): padrão de estado**

![Botão de hiperlink padrão embutido barra de informações](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Botão de hiperlink padrão embutido barra de informações

| Elemento | Nome do token: Category.color |
| --- | --- |
| Em primeiro plano (texto) | `InfoBar.Hyperlink` |

**Barra de informações embutido hyperlink (dentro de uma sentença): passe o estado**

![Botão de hiperlink embutido barra de informações em foco](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Botão de hiperlink embutido barra de informações em foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Em primeiro plano (texto) | `Infobar.HyperlinkMouseOver`<br />(Com sublinhado) |

**Barra de informações embutido hyperlink (dentro de uma sentença): pressionado estado**

![Barra de informações embutido hyperlink botão pressionado](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Barra de informações embutido hyperlink botão pressionado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Em primeiro plano (texto) | `Infobar.HyperlinkMouseDown`<br />(Com sublinhado) |

**Botão de barra de informações: padrão de estado**

![Botão de barra de informações de padrão](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Botão de barra de informações de padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `InfoBar.Button` |
| Em primeiro plano (texto) | `InfoBar.Button` |
| Borda | `InfoBar.ButtonBorder` |

**Botão de barra de informações: passe o estado**

![Botão de barra de informações em foco](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Botão de barra de informações em foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `InfoBar.ButtonMouseOver` |
| Em primeiro plano (texto) | `InfoBar.ButtonMouseOver` |
| Borda | `InfoBar.ButtonMouseOverBorder` |

**Botão de barra de informações: pressionado estado**

![Botão de barra de informações pressionado](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Botão de barra de informações pressionado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `InfoBar.ButtonMouseDown` |
| Em primeiro plano (texto) | `InfoBar.ButtonMouseDown` |
| Borda | `InfoBar.ButtonMouseDownBorder` |

**Botão de barra de informações: estado desabilitado**

![Botão de barra de informações desabilitado](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Botão de barra de informações desabilitado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `InfoBar.ButtonDisabled` |
| Em primeiro plano (texto) | `InfoBar.ButtonDisabled` |
| Borda | `InfoBar.ButtonDisabledBorder` |

**Botão de barra de informações: voltada para o estado**

![Botão de barra de informações focada](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Botão de barra de informações focada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `InfoBar.ButtonFocus` |
| Em primeiro plano (texto) | `InfoBar.ButtonFocus` |
| Borda | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Barras de rolagem  
Barras de rolagem são denominadas pelo ambiente do Visual Studio e não precisará ser com tema. No entanto, você pode decidir que deseja utilizar as cores usadas em barras de rolagem para que a interface do usuário aparece sempre consistente com essa parte do ambiente do Visual Studio.  

![Barra de rolagem (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303-140_ScrollbarRedline")<br />Barra de rolagem (corte de funcionários)

| Uso... | Não use... |
| --- | --- |
| ... ao criar interface do usuário que você deseja corresponder barras de rolagem do Visual Studio. | ... para qualquer coisa que você não deseja corresponder sempre da interface do usuário da barra de rolagem. |

**Barra de rolagem: padrão de estado**  

![Barra de rolagem de padrão](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303-141_Scrollbar")<br />Barra de rolagem de padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Barra de rolagem | `Environment.ScrollBarBackground` |
| Em primeiro plano (miniatura) | `Environment.ScrollBarThumbBackground` |

**Barra de rolagem: passe o estado**

![Barra de rolagem em foco](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303-143_ScrollbarHover")<br />Barra de rolagem em foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Barra de rolagem | `Environment.ScrollBarBackground` |
| Em primeiro plano (miniatura) | `Environment.ScrollBarThumbMouseOverBackground` |

*Barra de rolagem: pressionado estado**

![Pressionada a barra de rolagem](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303-145_ScrollbarPressed")<br />Pressionada a barra de rolagem  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Barra de rolagem | `Environment.ScrollBarBackground` |
| Em primeiro plano (miniatura) | `Environment.ScrollBarThumbPressedBackground` |

**Seta de barra de rolagem: padrão de estado**  

![Seta de barra de rolagem de padrão](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303-142_ScrollbarArrow")<br />Seta de barra de rolagem de padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ScrollBarArrowBackground`<br />(Definido para a mesma cor barra de rolagem). |
| Em primeiro plano (glifo) | `Environment.ScrollBarArrowGlyph` |

**Seta de barra de rolagem: passe o estado**

![Seta de barra de rolagem em foco](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br />Seta de barra de rolagem em foco  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ScrollBarArrowMouseOverBackground`<br />(Definido para a mesma cor barra de rolagem). |
| Em primeiro plano (glifo) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Seta de barra de rolagem: pressionado estado**  

![Pressionado seta de barra de rolagem](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br />Pressionado seta de barra de rolagem

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ScrollBarArrowPressedBackground`<br />(Definido para a mesma cor barra de rolagem). |
| Em primeiro plano (glifo) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="BKMK_SearchBoxes"></a>Caixas de pesquisa  
Sempre que possível, use o controle de pesquisa comuns fornecido pelo ambiente do Visual Studio. Cores da caixa de pesquisa são encontradas na categoria "SearchControl" no **ShellColors.pkgdef** arquivo, que contém nomes de token para o campo de entrada, o botão de ação, o botão suspenso e o menu suspenso.  

Uma caixa de pesquisa pode ser um dos vários estados, alguns dos quais são mutuamente exclusivos:  

-   "Foco" ou "foco" refere-se ao se o cursor estiver na caixa de texto.  

-   "Ativo" ou "inativo" refere-se se o usuário tem entrada uma consulta de pesquisa na caixa de texto.  

-   "Hover" significa que o usuário tem moused sobre a caixa de pesquisa com o mouse (esse estado substitui todos os outros estados).  

-   "Desabilitado" significa que a funcionalidade de pesquisa é desativada para o contexto atual.  

![Caixa de pesquisa (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303-110_SearchBoxRedline")<br />Caixa de pesquisa (corte de funcionários)  

| Uso... | Não use... |
| --- | --- |
| ... ao criar uma caixa de pesquisa personalizada. | ... para qualquer coisa que não é uma caixa de pesquisa. |
| | ... para tudo que você não deseja sempre coincidir com a pesquisa caixa da interface do usuário. |

**Voltada para o campo de entrada de pesquisa**

![Voltada para o campo de entrada de pesquisa](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br />Voltada para o campo de entrada de pesquisa  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `SearchControl.FocusedBackground` |
| Em primeiro plano (texto) | `SearchControl.FocusedBackground` |
| Borda | `SearchControl.FocusedBorder` |
| Separador | `SearchControl.FocusedDropDownSeparator` |

**Campo de entrada de pesquisa sem foco, ativo**

![Campo de pesquisa foco](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br />Campo de entrada de pesquisa sem foco, ativo

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `SearchControl.SearchActiveBackground` |
| Em primeiro plano (texto) | `SearchControl.SearchActiveBackground` |
| Borda | `SearchControl.UnfocusedBorder` |
| Separador | `SearchControl.DropDownSeparator` |

**Campo de entrada de pesquisa sem foco, inativa**

![Campo de entrada de pesquisa sem foco, inativa](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Campo de entrada de pesquisa sem foco, inativa  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `SearchControl.Unfocused` |
| Em primeiro plano (texto) | `SearchControl.Unfocused` |
| Borda | `SearchControl.UnfocusedBorder` |
| Separador | `SearchControl.DropDownSeparator` |

**Campo de entrada de pesquisa realçado (somente texto)**

![Campo de entrada de pesquisa realçado](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br />Campo de entrada de pesquisa realçado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `SearchControl.Selection` |
| Em primeiro plano (texto) | `SearchControl.FocusedBackground` |
| Borda | Nenhum |
| Separador | `SearchControl.FocusedDropDownSeparator` |

**Campo de entrada de pesquisa desabilitado**

![Campo de entrada de pesquisa desabilitado](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br />Campo de entrada de pesquisa desabilitado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `SearchControl.Disabled` |
| Em primeiro plano (texto) | `SearchControl.Disabled` |
| Borda | `SearchControl.DisabledBorder` |
| Separador | `SearchControl.DropDownSeparator` |

**Botão de ação de pesquisa restrita**

![Botão de ação de pesquisa com foco](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br />Botão de ação de pesquisa restrita

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | Nenhum |
| Em primeiro plano (glifo de pesquisa) | `SearchControl.SearchGlyph` |
| Em primeiro plano (glifo de parada) | `SearchControl.StopGlyph` |
| Em primeiro plano (Limpar glifo) | `SearchControl.ClearGlyph` |
| Borda | N/A |

**Botão de ação de pesquisa sem foco**  

![Botão de ação de pesquisa sem foco](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br />Botão de ação de pesquisa sem foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | N/A |
| Em primeiro plano (glifo de pesquisa) | `SearchControl.SearchGlyph` |
| Em primeiro plano (glifo de parada) | `SearchControl.StopGlyph` |
| Em primeiro plano (Limpar glifo) | `SearchControl.ClearGlyph` |
| Borda | N/A |

**Pressionado o botão de ação de pesquisa**

![Pressionado o botão de ação de pesquisa](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Pressionado o botão de ação de pesquisa

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `SearchControl.ActionButtonMouseDown` |
| Em primeiro plano (glifo) | `SearchControl.ActionButtonMouseDownGlyph` |
| Borda | `SearchControl.ActionButtonMouseDownBorder` |

**Botão de ação de pesquisa desabilitado**

![Botão de ação de pesquisa desabilitado](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br />Botão de ação de pesquisa desabilitado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | Nenhum |
| Em primeiro plano (glifo) | `SearchControl.ActionButtonDisabledGlyph` |
| Borda | Nenhum |

**Botão suspenso de pesquisa restrita**

![Botão suspenso de pesquisa restrita](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br />Botão suspenso de pesquisa restrita

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `SearchControl.FocusedDropDownButton` |
| Em primeiro plano (glifo) | `SearchControl.FocusedDropDownButtonGlyph` |
| Borda | `SearchControl.FocusedDropDownButtonBorder` |

**Botão suspenso de pesquisa sem foco**

![Botão suspenso de pesquisa sem foco](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br />Botão suspenso de pesquisa sem foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `SearchControl.UnfocusedDropDownButton` |
| Em primeiro plano (glifo) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Borda | `SearchControl.UnfocusedDropDownButtonBorder` |

**Pressionado o botão suspenso de pesquisa**

![Pressionado o botão suspenso de pesquisa](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Pressionado o botão suspenso de pesquisa

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `SearchControl.MouseDownDropDownButton` |
| Em primeiro plano (glifo) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Borda | `SearchControl.MouseDownDropDownButtonBorder` |

**Botão suspenso de pesquisa desabilitado**

![Botão suspenso de pesquisa desabilitado](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br />Botão suspenso de pesquisa desabilitado

| Elemento | Nome do token: Category.color |
| --- | --- |  
| Informações preliminares | Nenhum |
| Em primeiro plano (glifo) | `SearchControl.DisabledDownButtonGlyph` |
| Borda | Nenhum |

#### <a name="search-drop-down-lists"></a>Listas suspensas de pesquisa  
Menu suspenso de caixa pesquisa tem o potencial de ser um pouco mais complexo do que outros menus suspensos no Visual Studio. As seções "opções de pesquisa" e "pesquisas sugeridas" podem aparecer sozinho ou em conjunto no menu, e cada um é colorido separadamente. Uma linha também separa nessas duas seções quando aparecem juntos e uma borda ao redor no menu suspenso de inteiro.  

![Lista suspensa de pesquisa (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303-124_SearchDropdownRedline")<br />Lista suspensa de pesquisa (corte de funcionários)

| Uso... | Não use... |
| --- | --- |
| ... quando você estiver criando uma lista suspensa de pesquisa personalizada. | ... em listas suspensas que aparecem em outros contextos. |
| ... os nomes de token corretos para os componentes da lista correta. | ... em qualquer combinação de plano de fundo/primeiro plano diferente do especificado. |

**Elementos da lista suspensa de pesquisa**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Borda | `SearchControl.PopupBorder` |
| Separador | `SearchControl.PopupSectionHeaderSeparator` |
| Sombra | `Environment.DropShadowBackground` |

**Sugerido pesquisas: padrão de estado**

![Padrão de pesquisas sugeridas](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303-125_SearchSuggested")<br />Padrão de pesquisas sugeridas  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (texto) | `SearchControl.PopupItemText` |

**Sugerido pesquisas: passe o estado**

![Pesquisas sugeridas em foco](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br />Pesquisas sugeridas em foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (texto) | `SearchControl.PopupMouseOverItemText` |
| Borda | `SearchControl.PopupControlMouseOverBorder` |

**Opções de pesquisa: padrão de estado**

![Caixa de seleção de pesquisa](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303-126_SearchCheckbox")<br />Opções de pesquisa padrão (caixa de seleção)  

![Opções de pesquisa](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303-127_SearchOptions")<br />Opções de pesquisa padrão (link)  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (caixa de texto) | `SearchControl.PopupCheckboxText` |
| Em primeiro plano (texto do Link) | `SearchControl.PopupButtonText` |
| Plano de fundo do cabeçalho | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (texto de cabeçalho) | `SearchControl.PopupSectionHeaderText` |

**Opções de pesquisa: passe o estado**

![Opções de pesquisa (caixa de seleção) em foco](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br />Opções de pesquisa (caixa de seleção) em foco  

![Opções de pesquisa (link) em foco](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303-130_SearchOptionsHover")<br />Opções de pesquisa (link) em foco  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (caixa de texto) | `SearchControl.PopupCheckboxMouseDownText` |
| Em primeiro plano (texto do Link) | `SearchControl.PopupButtonMouseDownText` |
| Borda | `SearchControl.PopupControlMouseOverBorder` |

**Opções de pesquisa: pressionado estado**  

![Pressionado opções de pesquisa (caixa de seleção)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br />Pressionado opções de pesquisa (caixa de seleção)   

![Pressionado opções de pesquisa (link)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303-132_SearchOptionsPressed")<br />Pressionado opções de pesquisa (link)  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Plano de fundo da caixa de seleção | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (caixa de texto) | `SearchControl.PopupCheckboxMouseDownText` |
| Plano de fundo de link | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (texto do Link) | `SearchControl.PopupButtonMouseDownText` |

###  <a name="BKMK_TreeView"></a>Modos de exibição de árvore  
Várias janelas de ferramentas, incluindo o Gerenciador de soluções, Gerenciador de servidores e modo de exibição de classe, implementam um esquema de organização hierárquico cujas cores são controlados por nomes de cor no `TreeView` categoria. Todos os itens em uma exibição de árvore têm cores de plano de fundo e texto. Itens que têm aninhada elementos filho também possuem glifos que indicam se o item é expandido ou recolhido.  

![Exibição de árvore (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303-147_TreeViewRedline")<br />Exibição de árvore (corte de funcionários)

| Uso... | Não use... |
| --- | --- |
| ... em qualquer lugar em que você precisa implementar uma exibição hierárquica de organizacional. | ... para tudo que não é semelhante a uma exibição de árvore. |
| | ... em qualquer combinação de plano de fundo/primeiro plano diferente do especificado. |

**Item de exibição de árvore: padrão de estado**

![Item de exibição de árvore padrão](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303-148_TreeView")<br />Item de exibição de árvore padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `TreeView.Background` |
| Em primeiro plano (texto) | `TreeView.Background` |
| Em primeiro plano (glifo) | `TreeView.Glyph` |
| Borda | Nenhum |

**Item de exibição de árvore: passe o estado**

![Item de exibição de árvore em foco](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303-149_TreeViewHover")<br />Item de exibição de árvore em foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `TreeView.Background` |  
| Em primeiro plano (texto) | `TreeView.Background` |
| Em primeiro plano (glifo) | `TreeView.GlyphMouseOver` |
| Borda | Nenhum |

**Item de exibição de árvore: arraste por estado**

![Arraste o item de exibição de árvore na sobre](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303-150_TreeViewDragOver")<br />Arraste o item de exibição de árvore na sobre  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `TreeView.DragOverItem` |
| Em primeiro plano (texto) | `TreeView.DragOverItem` |
| Em primeiro plano (glifo) | `TreeView.DragOverItemGlyph` |
| Borda | Nenhum |

**Item de exibição de árvore: selecionada, voltada para o estado**

![Item de exibição de árvore selecionada e se concentrem](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303-151_TreeViewFocused")<br />Item de exibição de árvore selecionada e se concentrem

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `TreeView.SelectedItemActive` |
| Em primeiro plano (texto) | `TreeView.SelectedItemActive` |
| Em primeiro plano (glifo) | `TreeView.SelectedItemActiveGlyph` |
| Borda | `TreeView.FocusVisualBorder` |

**Item de exibição de árvore: estado selecionado, sem foco**  

![Item de exibição de árvore selecionada e foco](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303-152_TreeViewUnfocused")<br />Item de exibição de árvore selecionada e foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `TreeView.SelectedItemInactive` |
| Em primeiro plano (texto) | `TreeView.SelectedItemInactive` |
| Em primeiro plano (glifo) | `TreeView.SelectedItemInactiveGlyph` |
| Borda | Nenhum |

**Item de exibição de árvore: focalizado selecionado e voltada para o estado**

![Item de exibição de árvore selecionada e se concentrem em foco](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br />Item de exibição de árvore selecionada e se concentrem em foco  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `TreeView.SelectedItemActive` |
| Em primeiro plano (texto) | `TreeView.SelectedItemActive` |
| Em primeiro plano (glifo) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Borda | `TreeView.FocusVisualBorder` |

**Item de exibição de árvore: estado foco focalizado e selecionado**

![Item de exibição de árvore selecionada e foco em foco](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br />Item de exibição de árvore selecionada e foco em foco  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `TreeView.SelectedItemInactive` |
| Em primeiro plano (texto) | `TreeView.SelectedItemInactive` |
| Em primeiro plano (glifo) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Borda | Nenhum |

## <a name="shell-appearance"></a>Aparência de shell

### <a name="background"></a>Informações preliminares  
O plano de fundo do ambiente consiste em duas camadas. A camada inferior é uma cor sólida que abrange todo o IDE. A camada superior se encaixa em prateleira comando e entre os canais de janela da ferramenta ocultar automaticamente as bordas esquerda e direita do IDE. As camadas de plano de fundo superior e inferior são definidas com a mesma cor nos temas claro e escuro.  

![O plano de fundo do Visual Studio shell (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303-187_ShellBackgroundRedline")<br />O plano de fundo do Visual Studio shell (corte de funcionários)

| Uso... | Não use... |
| --- | --- |
| ... para locais de onde você deseja corresponder o plano de fundo do ambiente do Visual Studio. | ... como um preenchimento de locais que não sejam de superfícies de plano de fundo. |
| | ... como um plano de fundo para colocar elementos de primeiro plano no. |

**Aparência de shell de camada inferior**

| Elemento | Nome do token: Category.color |
| --- | --- |  
| Informações preliminares | `Environment.EnvironmentBackground` |

**Aparência de shell de camada superior**

> Marcas de gradiente definido como o mesmo valor de cor em temas de luz de 2013 do Visual Studio e o escuro.

| Elemento | Nome do token: Category.color |
| --- | --- |  
| Informações preliminares | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |  

### <a name="command-shelf"></a>Prateleira de comando  
Dois conjuntos de nomes de token são usados para os planos de fundo do comando shelf: um conjunto de onde se encontra a barra de menus e uma para onde as barras de comando ficam. Um grupo de barra de comandos individuais tem seus próprios valores de cor do plano de fundo, são discutidas mais detalhadamente na seção "barra de comandos". Barra de menus da barra e comando texto é discutido nas seções barra menu e comando, respectivamente.  

![Prateleira de comando do Visual Studio (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303-188_CommandShelfRedline")<br />Prateleira de comando do Visual Studio (corte de funcionários)  

| Uso... | Não use... |
| --- | --- |
| ... para as áreas onde você coloca menus ou barras de ferramentas. | ... para as áreas que não são semelhantes a validade de um comando. |
|com a combinação de nome de token correto de plano de fundo/primeiro plano. | |

**Barra de menus do comando prateleira**

> Marcas de gradiente definido como o mesmo valor de cor em temas de luz de 2013 do Visual Studio e o escuro.

| Elemento | Nome do token: Category.color |
| --- | --- |  
| Informações preliminares | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

* * O comando prateleira comando barra * *

> Marcas de gradiente definido como o mesmo valor de cor em temas de luz de 2013 do Visual Studio e o escuro.

| Elemento | Nome do token: Category.color |
| --- | --- |  
| Informações preliminares | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Designer de manifesto  
O Designer de manifesto foi projetado como uma maneira de tornar mais fácil editar o arquivo de manifesto em projetos do Windows 8 e Windows Phone 8. Embora não haja nenhuma estrutura compartilhada disponíveis para consumo, pode ser apropriado para a correspondência com o layout de design e cores da estrutura geral e guias de navegação/orientação. Para obter mais informações sobre detalhes de layout, consulte [Layout para o Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  

![Designer de manifesto (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303-175_ManifestDesignerRedline")<br />Designer de manifesto (corte de funcionários)

| Uso... | Não use... |
| --- | --- |
| ... para designers que são semelhantes para o Designer de manifesto. | ... Se você tiver mais de seis guias. |
| ... em vez de usar controles comuns do guia na parte superior de um editor no documento bem. | ... para qualquer interface de usuário que não é estruturado como o Designer de manifesto. |

**Guia selecionada do manifesto Designer: padrão de estado**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `ManifestDesigner.TabActive` |
| Borda | Nenhum |

**Painel de descrição selecionado de Designer de manifesto: padrão de estado**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `ManifestDesigner.DescriptionPane` |

**Página de conteúdo selecionada manifesto do Designer: padrão de estado**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `ManifestDesigner.Background` |
| Texto de Ajuda da caixa de diálogo | `ManifestDesigner.WatermarkText`<br />(Esse nome de token não corresponder à sua função). |

**Guia de Designer de manifesto: cancelou a seleção de estado**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `ManifestDesigner.Tab.Inactive` |

**Guia de Designer de manifesto: passe o estado**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Estruturas de comando  

###  <a name="BKMK_CommandMenus"></a>Menus  
Menus podem ocorrer em vários locais dentro do Visual Studio: barra de menu principal, inserida no documento ou a ferramenta windows ou no botão direito do mouse em vários locais em todo o IDE. Implementações de menus associados com outros elementos de interface do usuário são discutidas na seção do elemento do respectivos. Você sempre deve usar a implementação de menu padrão fornecida pelo ambiente do Visual Studio. No entanto, em alguns casos raros talvez você não tenha acesso para os menus padrão do Visual Studio. Nessas situações, use os seguintes nomes de token para garantir que a interface do usuário é consistente com outros menus no Visual Studio.  

![Menu do Visual Studio (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303-000_MenuRedline")<br />Menu do Visual Studio (corte de funcionários)

| Uso... | Não use... |
| --- | --- |
| ... quando você precisa criar um menu personalizado.| ... a cor de plano de fundo sozinha. Sempre use a combinação de plano de fundo/primeiro plano conforme especificado. |
| ... quando você tem um novo componente de interface do usuário que você deseja corresponder os menus do Visual Studio.| |

#### <a name="menu-titles"></a>Títulos de menus  
Títulos de menus consistem em um plano de fundo, uma borda e o texto do título, bem como um glifo opcional, normalmente quando o menu é encontrado em uma barra de comandos.  

![Título de menu (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303-001_MenuTitleRedline")<br />Título de menu (corte de funcionários)  

| Uso... | Não use... |
| --- | --- |
| ... sempre que você estiver criando um título de menu personalizados. | ... para tudo que você não deseja sempre coincidir com o título de menu. |
| | ... em qualquer combinação de plano de fundo/primeiro plano diferente do especificado. |

**Título de menu: padrão de estado**

![Título de menu padrão](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303-002_MenuTitleDefault")<br />Título de menu padrão

![Título de menu padrão com glifo](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br />Título de menu padrão com glifo

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | Nenhum |
| Em primeiro plano (texto) | `Environment.CommandBarTextActive` |
| Em primeiro plano (glifo) | `Environment.CommandBarMenuGlyph` |
| Borda | Nenhum |

**Título de menu: passe o estado**  

![Título de menu em foco](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303-004_MenuTitleHover")<br />Título de menu em foco  

![Título de menu com glifo em foco](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br />Título de menu com glifo em foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (texto) | `Environment.CommandBarTextHover` |
| Em primeiro plano (glifo) | `Environment.CommandBarMenuMouseOverGlyph` |  
| Borda | `Environment.CommandBarBorder` |

**Título de menu: pressionado estado**  

![Título de menu pressionado](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303-006_MenuTitlePressed")<br />Título de menu pressionado

![Título de menu com glifo de pressionado](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br />Título de menu com glifo de pressionado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (texto) | `Environment.CommandBarTextActive` |
| Em primeiro plano (glifo) | `Environment.CommandBarMenuMouseDownGlyph` |
| Borda | `Environment.CommandBarMenuBorder`<br />(Somente à esquerda, superior e direita.) |  

**Título de menu: estado desabilitado**  

![Título de menu desativado com glifo](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br />Título de menu desativado com glifo

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | Nenhum |
| Em primeiro plano (texto) | `Environment.CommandBarTextInactive` |
| Em primeiro plano (glifo) | `Environment.CommandBarTextInactive` |
| Borda | Nenhum |

#### <a name="menu-items"></a>Itens de menu
Um item de menu individuais consiste o texto do menu e um ícone opcional, caixa de seleção ou glifo de submenu. As alterações de cor do plano de fundo e texto em foco. Esse token de cor é um par de plano de fundo/primeiro plano.  

![Corte de funcionários em itens de menu](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303 009_MenuItemRedline")  

| Uso... | Não use...  |
|---|---|
| ... para qualquer lista suspensa que é iniciado de uma barra de menu ou barra de comandos. | ... para qualquer lista suspensa em outro contexto. |
| | ... em qualquer combinação de plano de fundo/primeiro plano diferente do especificado. |

**Itens de menu: padrão de estado**

![Itens de menu padrão](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303-010_MenuDefault")<br />Itens de menu padrão  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (texto) | `Environment.CommandBarTextActive` |
| Em primeiro plano (glifo Submenu) | `Environment.CommandBarMenuSubmenuGlyph` |
| Borda | `Environment.CommandBarMenuBorder` |
| O plano de fundo do ícone canal | `Environment.CommandBarMenuIconBackground` |
| Separador | `Environment.CommandBarMenuSeparator` |
| Sombra | `Environment.DropShadowBackground` |

**Itens de menu: marcado e selecionado Estados**  

![Menu marcada](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303-011_MenuChecked")<br />Item de menu marcados

![Menu selecionado](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303-012_MenuSelected")<br />Item de menu selecionado    

| Elemento | Nome do token: Category.color |
| --- | --- |
| Marca de seleção | `Environment.CommandBarCheckBox` |  
| Marca de verificação em segundo plano | `Environment.CommandBarSelectedIcon` |  
| Plano de fundo do ícone | `Environment.CommandBarSelected` |
| Borda de ícone | `Environment.CommandBarSelectedBorder` |

**Itens de menu: passe o estado**  

![Sobreposição de menu](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303-013_MenuHover")<br />Item de menu em foco

![Passe o mouse menu marcado](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303-014_MenuHoverChecked")<br />Verificado o item de menu em foco

![Passe o mouse menu selecionado](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303-015_MenuHoverSelected")<br />Item de menu selecionado em foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.CommandBarMenuItemMouseOver` |
| Em primeiro plano (texto) | `Environment.CommandBarMenuItemMouseOver` |
| Em primeiro plano (glifo Submenu) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Marca de seleção | `Environment.CommandBarCheckBoxMouseOver` |
| Marca de verificação em segundo plano | `Environment.CommandBarHoverOverSelectedIcon` |
| Plano de fundo do ícone | `Environment.CommandBarHoverOverSelected` |
| Borda de ícone | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Itens de menu: estado desabilitado**  

![Menu desativado](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303-016_MenuDisabled")<br />Item de menu desativado

![Menu desabilitada marcada](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303-017_MenuDisabledChecked")<br />Item de menu desativado com a marca de seleção

| Elemento | Nome do token: Category.color |
| --- | --- |
| Em primeiro plano (texto) | `Environment.CommandBarTextInactive` |
| Em primeiro plano (glifo Submenu) | `Environment.CommandBarMenuSubmenuGlyph` |
| Marca de seleção | `Environment.CommandBarCheckBoxDisabled` |
| Marca de verificação em segundo plano | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Barras de comando  
Uma barra de comandos pode aparecer em vários locais no IDE do Visual Studio, mais notoriamente comando comercial e inseridos na ferramenta ou janelas de documentos.  

Em geral, use sempre a implementação da barra de comando padrão fornecida pelo ambiente do Visual Studio. Usando o mecanismo padrão garante que todos os detalhes do visual serão exibido corretamente e que os elementos interativos, comporte consistente com outros controles de barra de comando do Visual Studio. No entanto, se for necessário para criar sua própria barra de comandos, certifique-se de que estilo corretamente usando os seguintes nomes de token.  

![Redline da barra de comando](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303-018_CommandBarRedline")<br />Barra de comandos (corte de funcionários)  

![Aplicar linhas vermelhas no botão de estouro](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303-019_OverflowButtonRedline")<br />Botão de estouro (corte de funcionários)  

| Uso... | Não use... |
| --- | --- |
| ... em locais onde você precisa de uma barra de comandos inseridos, mas são não é possível usar a implementação de barra de comando padrão do Visual Studio. | ... para elementos de interface do usuário que não são semelhantes à barra de comando. |
| | ... para componentes de barra de comando que não sejam aqueles para os quais o token nomes estão especificados. |

#### <a name="command-bar-groups"></a>Grupos de barra de comando  
Um grupo de barra de comando consiste em um conjunto relacionado de controles da barra de comando e pode conter qualquer número de botões, dividir os botões, menus suspensos, caixas de combinação ou menus. Cores para os controles são governadas por nomes de token separados e são discutidas individualmente em outro lugar neste guia. Uma linha divisória é usada para dividir um grupo de barra de comandos em subgrupos relacionados.  

![Aplicar linhas vermelhas no grupo da barra de comandos](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303-020_CommandBarGroupRedline")<br />Grupo de barra de comandos (corte de funcionários)

| Uso... | Não use... |
| --- | --- |  
| ... em locais onde você precisa de uma barra de comandos inseridos, mas são não é possível usar a implementação de barra de comando padrão do Visual Studio. | ... para elementos de interface do usuário que não são semelhantes à barra de comando. |
| | ... para componentes de barra de comando que não sejam aqueles para os quais o token nomes estão especificados. |

**Grupo de barra de comandos: padrão de estado**  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.CommandBarGradientBegin`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Borda | `Environment.CommandBarToolBarBorder` |
| Arraste a alça | `Environment.CommandBarDragHandle` |
| Separador | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Ícones de comando  
![Aplicar linhas vermelhas no ícone de comando](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303-021_CommandIconRedline1")<br />Ícone do comando (corte de funcionários)  

![Aplicar linhas vermelhas no ícone de comando com texto](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303-022_CommandIconRedline2")<br />Ícone de comando com texto (corte de funcionários)  

| Uso... | Não use... |
| --- | --- |
| ... para os botões que serão colocados em uma barra de comandos. | ... para controles que têm seus próprios nomes de token. |
| | ... em qualquer combinação de plano de fundo/primeiro plano diferente do especificado. |

**Ícone de comando: padrão de estado**  

![Comando ícone padrão](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303-023_CommandIconDefault")<br />Ícone de comando padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | N/d (herda do plano de fundo da barra de comando) |
| Em primeiro plano (texto) | `Environment.CommandBarTextActive` |
| Borda | N/A |

**Ícone de comando: padrão de estado, selecionado**

![Padrão, o ícone do comando selecionado](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br />Padrão, o ícone do comando selecionado  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.CommandBarSelected` |
| Em primeiro plano (texto) | `Environment.CommandBarTextSelected` |
| Borda | `Environment.CommandBarSelectedBorder` |

**Ícone de comando: hover ou foco Estados**  

![Ícone de comando em foco ou passe o mouse](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303-025_CommandIconHover")<br />Ícone de comando em foco ou passe o mouse

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (texto) | `Environment.CommandBarTextHover` |
| Borda | `Environment.CommandBarBorder` |

**Ícone de comando: estados em foco ou foco, selecionados**

![Ícone de comando selecionado em foco ou passe o mouse](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br />Ícone de comando selecionado em foco ou passe o mouse

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.CommandBarHoverOverSelected` |
| Em primeiro plano (texto) | `Environment.CommandBarTextHoverOverSelected` |
| Borda | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Ícone de comando: pressionado estado**  

![Ícone do comando pressionado](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303-027_CommandIconPressed")<br />Ícone do comando pressionado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (texto) | `Environment.CommandBarTextMouseDown` |
| Borda | `Environment.CommandBarBorder` |

**Ícone de comando: estado desabilitado**  

![Ícone de comandos desabilitada](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303-028_CommandIconDisabled")<br />Ícone de comandos desabilitada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | N/d (herda do plano de fundo da barra de comando) |
| Em primeiro plano (texto) | `Environment.CommandBarTextInactive` |
| Borda | N/A |

####  <a name="BKMK_CommandComboBox"></a>Caixas de combinação de barra de comando

> [!IMPORTANT]
> Caixas de combinação são semelhantes às listas suspensas, mas incluam uma região de texto editável. Se a lista suspensa não incluir um texto editável região, use os tokens de cor para [listas suspensas de barra de comandos](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).  

![Corte de funcionários de caixa de combinação de barra de comando](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303-029_ComboBoxRedline")<br />Caixa de combinação de barra de comando (corte de funcionários)  

| Uso... | Não use... |
| --- | --- |
| ... ao criar caixas de combinação personalizada. | ... para qualquer coisa não quiser sempre coincidir com o comando da barra da interface do usuário. |
| ... ao criar um controle de barra de comando que é semelhante a uma caixa de combinação. | ... quando você tem acesso a uma caixa de combinação de estilo. |

**Campo de caixa de combinação barra de comando entrada: padrão de estado**

![Campo de caixa de combinação barra de comando entrada](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303-030_ComboBoxInputField")<br />Campo de caixa de combinação barra de comando entrada  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ComboBoxBackground` |
| Em primeiro plano (texto) | `Environment.ComboBoxText` |
| Borda | `Environment.ComboBoxBorder` |
| Separador | Nenhum separador |

**Botão de lista suspensa da barra de comandos: padrão de estado**  

![Caixa de combinação caixa drop &#45; abaixo do botão](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br />Botão de lista suspensa da barra de comandos

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | N/d (herda do plano de fundo da barra de comando) |
| Em primeiro plano (glifo) | `Environment.ComboBoxGlyph` |

**Lista de lista suspensa da barra de comando: padrão de estado**

![Lista de lista suspensa da barra de comando](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br />Lista de lista suspensa da barra de comando

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ComboBoxPopupBackgroundBegin`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (texto) | `Environment.ComboBoxItemText` |
| Borda | `Environment.ComboBoxPopupBorder` |

**Campo de caixa de combinação barra de comando entrada: passe o estado**  

![Comando barra combinação caixa campo de entrada em foco](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br />Comando barra combinação caixa campo de entrada em foco  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (texto) | `Environment.ComboBoxMouseOverText` |
| Borda | `Environment.ComboBoxMouseOverBorder` |
| Separador | `Environment.ComboBoxMouseOverSeparator` |

 **Botão de lista suspensa da barra de comandos: passe o estado**  

![Botão de menu suspenso de barra de comandos em foco](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br />Botão de menu suspenso de barra de comandos em foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ComboBoxButtonMouseOverBackground` |
| Em primeiro plano (glifo) | `Environment.ComboBoxMouseOverGlyph` |

**Lista de lista suspensa da barra de comando: passe o estado**

 ![Lista de lista suspensa de barra de comando em foco](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br />Lista de lista suspensa de barra de comando em foco  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Plano de fundo (item de Menu) | `Environment.ComboBoxItemMouseOverBackground` |
| Em primeiro plano (texto) | `Environment.ComboBoxItemMouseOverText` |
| Borda (item de Menu) | `Environment.ComboBoxItemMouseOverBorder` |

 **Campo de caixa de combinação barra de comando entrada: voltada para o estado**  

![Voltada para o campo de caixa de combinação barra de comando entrada](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br />Voltada para o campo de caixa de combinação barra de comando entrada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ComboBoxFocusedBackground` |
| Em primeiro plano (texto) | `Environment.ComboBoxFocusedText` |
| Borda | `Environment.ComboBoxFocusedBorder` |
| Separador | `Environment.ComboBoxFocusedButtonSeparator` |

**Botão de lista suspensa da barra de comandos: voltada para o estado**  

![Comando foco barra botão suspenso](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br />Comando foco barra botão suspenso

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ComboBoxFocusedButtonBackground` |
| Em primeiro plano (glifo) | `Environment.ComboBoxFocusedGlyph` |

 **Campo de caixa de combinação barra de comando entrada: pressionado estado**  

![Campo de caixa de combinação barra de comando entrada de pressionado](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br />Campo de caixa de combinação barra de comando entrada de pressionado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ComboBoxMouseDownBackground` |
| Em primeiro plano (texto) | `Environment.ComboBoxMouseDownText` |
| Borda | `Environment.ComboBoxMouseDownBorder` |
| Separador | `Environment.ComboBoxMouseDownSeparator` |

**Botão de lista suspensa da barra de comandos: pressionado estado**

![Pressionado o botão suspenso da barra de comandos](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br />Pressionado o botão suspenso da barra de comandos  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ComboBoxButtonMouseDownBackground` |
| Em primeiro plano (glifo) | `Environment.ComboBoxMouseDownGlyph` |

**Campo de caixa de combinação barra de comando entrada: estado desabilitado**  

![Comando desabilitado barra campo de entrada de caixa de combinação](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br />Comando desabilitado barra campo de entrada de caixa de combinação  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ComboBoxDisabledBackground` |
| Em primeiro plano (texto) | `Environment.ComboBoxDisabledText` |
| Borda | `Environment.ComboBoxDisabledBorder` |
| Separador | Nenhum separador |

**Botão de lista suspensa da barra de comandos: estado desabilitado**  

![Comando desabilitado barra botão suspenso](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br />Comando desabilitado barra botão suspenso

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | Nenhum |
| Em primeiro plano (glifo) | `Environment.ComboBoxDisabledGlyph` |

####  <a name="BKMK_CommandDropDown"></a>Comando barra listas suspensas

> [!IMPORTANT]
>  Listas suspensas são semelhantes às caixas de combinação, mas não têm regiões de texto editável. Se a lista suspensa inclui uma área de texto editável, use os tokens de cor para [caixas de combinação da barra de comando](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).  

![Lista suspensa da barra de comandos (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303-042_DropdownRedline")<br />Lista suspensa da barra de comandos (corte de funcionários)

| Uso... | Não use... |
| --- | --- |
| ... ao criar controles de lista suspensa personalizada. | ... para tudo que não é semelhante a uma lista suspensa. |
| | ... para caixas de combinação ou botões de divisão. |   

**Campo de seleção de lista suspensa de barra de comando: padrão de estado**  

![Campo de seleção de lista suspensa de barra de comando padrão](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303-043_DropdownSelectionField")<br />Campo de seleção de lista suspensa de barra de comando padrão  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.DropDownBackground` |
| Em primeiro plano (texto) | `DropDownText` |
| Borda | `DropDownBorder` |
| Separador | Nenhum separador |

**Botão de lista suspensa da barra de comandos: padrão de estado**

![Botão de menu suspenso de barra de comandos padrão](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303-044_DropdownButton")<br />Botão de menu suspenso de barra de comandos padrão  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | Nenhum |
| Em primeiro plano (glifo) | `Environment.DropDownGlyph` |

**Lista de lista suspensa da barra de comando: padrão de estado**

![Lista de lista suspensa de barra de comandos padrão](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303-045_DropdownList")<br />Lista de lista suspensa de barra de comandos padrão  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.DropDownPopupBackgroundBegin`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (texto) | `Environment.ComboBoxItemText` |
| Borda | `Environment.DropDownPopupBorder` |
| Sombra | `Environment.DropShadowBackground` |

**Campo de seleção de lista suspensa de barra de comando: passe o estado**  

![Campo de seleção de lista suspensa de barra de comando em foco](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br />Campo de seleção de lista suspensa de barra de comando em foco  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.DropDownMouseOverBackgroundBegin`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (texto) | `Environment.DropDownMouseOverText` |
| Borda | `Environment.DropDownMouseOverBorder` |
| Separador | `Environment.DropDownButtonMouseOverSeparator` |

**Botão de lista suspensa da barra de comandos: passe o estado**  

![Botão de menu suspenso de barra de comandos em foco](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br />Botão de menu suspenso de barra de comandos em foco  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.DropDownButtonMouseOverBackground` |
| Em primeiro plano (glifo) | `Environment.DropDownMouseOverGlyph` |

**Lista de lista suspensa da barra de comando: passe o estado**  

![Lista de lista suspensa de barra de comando em foco](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303-048_DropdownListHover")<br />Lista de lista suspensa de barra de comando em foco  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Plano de fundo (item de Menu) | `Environment.ComboBoxItemMouseOverBackground` |
| Em primeiro plano (texto) | `Environment.ComboBoxItemMouseOverText` |
| Borda (item de Menu) | `Environment.ComboBoxItemMouseOverBorder` |

 **Campo de seleção de lista suspensa de barra de comando: pressionado estado**  

![Remover &#45; para o campo de seleção pressionado](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br />Pressionado comando barra campo seleção suspensa

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.DropDownMouseDownBackground` |
| Em primeiro plano (texto) | `Environment.DropDownMouseDownText` |
| Borda | `Environment.DropDownMouseDownBorder` |
| Separador | `Environment.DropDownButtonMouseDownSeparator` |

**Botão de lista suspensa da barra de comandos: pressionado estado**

![Pressionado o botão suspenso da barra de comandos](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br />Pressionado o botão suspenso da barra de comandos  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.DropDownButtonMouseDownBackground` |
| Em primeiro plano (glifo) | `Environment.DropDownMouseDownGlyph` |

**Campo de seleção de lista suspensa de barra de comando: estado desabilitado**  

![Comando desabilitado barra campo seleção suspensa](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")<br />Comando desabilitado barra campo seleção suspensa

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.DropDownDisabledBackground` |
| Em primeiro plano (texto) | `Environment.DropDownDisabledText` |
| Borda | `Environment.DropDownDisabledBorder` |
| Separador | Nenhum separador |

**Botão de lista suspensa da barra de comandos: estado desabilitado**

![Comando desabilitado barra botão suspenso](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")<br />Comando desabilitado barra botão suspenso

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | N/A |
| Em primeiro plano (glifo) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Barra de comandos dividir botões
Botões de divisão compartilham muitos nomes de token com outros controles de barra de comando, como botões, menus e texto da barra de comando. Todas as ações necessárias e nomes de token do botão suspenso são repetidos aqui por conveniência. Listas de lista suspensa de botão de divisão são implementações de [menus de barra de comandos](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).  

![Aplicar linhas vermelhas no botão de divisão](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303-053_SplitButtonRedline")<br />Botão de divisão de barra de comandos (corte de funcionários)  

| Uso... | Não use... |
| --- | --- |
| ... ao criar um botão de divisão personalizado. | ... para outros tipos de botões. |
| | ... em qualquer combinação de plano de fundo/primeiro plano diferente do especificado. |

**Botão de divisão de barra de comandos: padrão de estado**  

![Botão de divisão de barra de comandos padrão](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303-054_SplitButton")<br />Botão de divisão de barra de comandos padrão  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | Nenhum |
| Em primeiro plano (texto) | `Environment.CommandBarTextActive` |
| Em primeiro plano (glifo) | `Environment.CommandBarSplitButtonGlyph` |
| Borda | N/A |
| Separador | N/A |

**Botão de divisão de barra de comandos: passe o estado**  

![Botão em foco de divisão de barra de comandos](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303-055_SplitButtonHover")<br />Botão em foco de divisão de barra de comandos

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (texto) | `Environment.CommandBarTextHover` |
| Em primeiro plano (glifo) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Borda | `Environment.CommandBarBorder` |
| Separador | `Environment.CommandBarSplitButtonSeparator` |

**Botão de divisão de barra de comandos: pressionado estado**  

![Barra de comandos pressionado o botão de divisão](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303-056_SplitButtonPressed")<br />Barra de comandos pressionado o botão de divisão  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (texto) | `Environment.CommandBarTextMouseDown` |
| Em primeiro plano (glifo) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Borda | `Environment.CommandBarBorder` |
| Separador | N/A |

**Botão de divisão de barra de comandos: estado desabilitado**

![Botão de divisão de barra de comandos desabilitada](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br />Botão de divisão de barra de comandos desabilitada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | N/A |
| Em primeiro plano (texto) | `Environment.ComboBoxItemTextInactive` |
| Em primeiro plano (glifo) | `Environment.CommandBarTextInactive` |
| Borda | N/A |
| Separador | N/A |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Botões de comando da barra 'Mais opções' e 'Overflow'  
O botão "Mais opções" é usado quando um grupo de barra de comando é personalizável, adicionando ou removendo botões da barra de comando relacionado. Botão de "Estouro" é exibida quando uma barra de comandos truncada devido à falta de espaço horizontal e clique em mostra um menu que contém os botões da barra de comando que não podem ser exibidos. Cores para esses dois botões são controladas pelo mesmo conjunto de nomes de token.  

![Comando barra botão 'Mais opções' (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303-058_MoreOptionsRedline")<br />Comando barra botão 'Mais opções' (corte de funcionários)  

| Uso... | Não use... |
| --- | --- |
| ... para personalizado 'mais opções' ou 'Overflow' botões. | ... para os botões que não tem uma funcionalidade semelhante a um 'Mais opções' ou o botão 'Estouro'. |

**'Mais opções' e 'Overflow' botões de barra de comandos: padrão de estado**  

![Barra de comandos 'Mais opções' botão padrão](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303-059_MoreOptions")<br />Barra de comandos 'Mais opções' botão padrão

!['Overflow' botão de barra de comandos padrão](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303-060_Overflow")<br />'Overflow' botão de barra de comandos padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.CommandBarOptionsBackground` |
| Em primeiro plano (glifo) | `Environment.CommandBarOptionsGlyph` |

**'Mais opções' e 'Overflow' botões de barra de comandos: passe o estado**

![Botão 'Mais opções' em foco da barra de comandos](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303-061_MoreOptionsHover")<br />Botão 'Mais opções' em foco da barra de comandos  

![Botão de 'Overflow' de barra de comandos em foco](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303-062_OverflowOptions")<br />Botão de 'Overflow' de barra de comandos em foco   

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (glifo) | `Environment.CommandBarOptionsMouseDownGlyph` |

**'Mais opções' e 'Overflow' botões de barra de comandos: pressionado estado**  

![Pressionado o botão 'Mais opções' da barra de comandos](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303-063_MoreOptionsPressed")<br />Pressionado o botão 'Mais opções' da barra de comandos  

![Estouro pressionado](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303-064_OverflowPressed")<br />Pressionado o botão da barra de comando 'Overflow'  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (glifo) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Janelas de documento  
Não é necessário para replicar as janelas de documento, porque elas são fornecidas pelo ambiente do Visual Studio. No entanto, você pode decidir que deseja utilizar as cores usadas em janelas de documento para que a interface do usuário aparece sempre consistente com essa parte do ambiente do Visual Studio.  

Ao usar tokens de cor de janela de documento, tenha cuidado para usá-los somente para elementos semelhantes e sempre em pares. Se você não fizer isso, você pode obter resultados inesperados na sua interface do usuário.  

### <a name="document-window-frames"></a>Quadros de janela de documento  
Janelas de documentos podem ser encaixados no IDE ou flutuante como uma janela separada. Quando uma janela de documento é flutuante fora do IDE, ele ainda está corretamente um documento e tem o plano de fundo, borda, texto e as cores de guia são as mesmas quando ele é parte do IDE. No entanto, o documento se encontra em um quadro que tem seu próprio plano de fundo, borda e cores de texto. Quando as janelas de ferramentas são encaixadas corretamente o documento, eles herdam o comportamento e a cor de suas guias de nomes de token de janela de documento.  

![Janela de documento encaixada (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")<br />Janela de documento encaixada (corte de funcionários)  

![Janela de documentos flutuante (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")<br />Janela de documentos flutuante (corte de funcionários)  

| Uso... | Não use... |
| --- | --- |
| ... em qualquer lugar que está criando a interface do usuário que você deseja corresponder a janela do documento. | ... para qualquer interface de usuário que você não deseja automaticamente alterado se o shell tem uma atualização de tema. |

**Janela de documento encaixado ou flutuante: padrão de estado**  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | Depende do tipo de documento |
| Em primeiro plano (texto) | Depende do tipo de documento |
| Borda | `Environment.ToolWindowBorder` |

**Determinados flutuante quadro de janela de documento: padrão de estado**

![Padrão centrado, flutuante quadro de janela de documento](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303-067_FrameFocused")<br />Padrão centrado, flutuante quadro de janela de documento

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ToolWindowFloatingFrame` |
| Em primeiro plano (texto) | `Environment.ToolWindowFloatingFrame` |
| Em primeiro plano (glifo) | `Environment.RaftedWindowButtonActiveGlyph` |
| Borda | `Environment.MainWindowActiveDefaultBorder` |
| Borda (glifo) | `Environment.RaftedWindowButtonActiveBorder`<br />(Definido como transparente) |

**Quadro de janela de documentos flutuante foco: padrão de estado**  

![Padrão de quadro de janela de documentos flutuante sem foco](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303-068_FrameUnfocused")<br />Padrão de quadro de janela de documentos flutuante sem foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ToolWindowFloatingFrameInactive` |
| Em primeiro plano (texto) | `Environment.ToolWindowFloatingFrameInactive` |
| Em primeiro plano (glifo) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Borda | `Environment.MainWindowInactiveBorder` |
| Borda (glifo) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Definido como transparente) |

**Determinados flutuante quadro de janela de documento: passe o estado**

![Determinados flutuante quadro de janela de documento em foco](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303-069_FrameFocusedHover")<br />Determinados flutuante quadro de janela de documento em foco  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Plano de fundo (glifo) | `Environment.RaftedWindowButtonHoverActive` |
| Em primeiro plano (glifo) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Borda (glifo) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Quadro de janela de documentos flutuante foco: passe o estado**  

![Quadro de janela de documentos flutuante foco em foco](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br />Quadro de janela de documentos flutuante foco em foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Plano de fundo (glifo) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Em primeiro plano (glifo) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Borda (glifo) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Determinados flutuante quadro de janela de documento: pressionado estado**  

![Determinados flutuante quadro de janela de documento em pressione](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303-071_FrameFocusedPressed")<br />Determinados flutuante quadro de janela de documento em pressione

| Elemento | Nome do token: Category.color |
| --- | --- |
| Plano de fundo (glifo) | `Environment.RaftedWindowButtonDown` |
| Em primeiro plano (glifo) | `Environment.RaftedWindowButtonDownGlyph` |
| Borda (glifo) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Guias de documento  
Guias do documento ficam no canal de guia para indicar quais documentos estão abertos no momento, juntamente com o qual é a atual selecionada ou o documento ativo. Janelas de ferramentas também podem ser encaixadas no canal de guia de documento, se o usuário coloca nesse local. Nessa situação, usarem as mesmas cores de guia como janelas de documentos. Se você estiver criando da interface do usuário que você deseja sempre coincidir com as cores da janela de documento (incluindo atualizações de tema ou se novos temas instalados), em seguida, fazer referência a esses tokens de cor.  

![Guias de documento (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303-072_DocumentTabRedline")<br />Guias de documento (corte de funcionários)

| Uso... | Não use... |
| --- | --- |
| ... em qualquer lugar que está criando a interface do usuário que você deseja corresponder guias do documento e selecionar automaticamente atualizações de tema ou novas cores de tema. | ... para qualquer interface de usuário que você não deseja alterar automaticamente quando o shell tem um tema de atualização. |

#### <a name="open-document-tabs"></a>Guias de documentos abertos  
Cada documento aberto tem uma guia no canal de guia de documento que exibe seu nome. Documentos podem ser selecionados ou abra no plano de fundo e suas guias refletem esses estados:  

-   A guia selecionada representa o documento que está sendo exibido no documento bem. Uma guia selecionada tem uma borda de documento que estende bem entre a borda superior do documento.  

-   Guias de plano de fundo são qualquer guias do documento que não estão na guia selecionada no momento. Quando clicado, eles se tornam a guia selecionada e adquirem todas as cores de plano de fundo, a borda e o texto desses nomes de token.  

![Guia de documento aberto (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")<br />Guia de documento aberto (corte de funcionários)

| Uso...  | Não use... |
| --- | --- |
| ... ao criar guias de documento personalizadas. | ... para as guias provisionados (visualização). |
| | ... para qualquer interface de usuário que você não deseja alterar automaticamente se o shell tem uma atualização de tema. |

**Guia do documento selecionada, determinados**  

![Guia do documento selecionada, determinados](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303-074_SelectedTabFocused")<br />Guia do documento selecionada, determinados

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.FileTabSelectedGradientTop`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (texto) | `Environment.FileTabSelectedText` |
| Borda | `Environment.FileTabSelectedBorder`<br />(Definido para a mesma cor do plano de fundo). |
| Borda de documento | `Environment.FileTabDocumentBorderBackground` |

**Guia do documento selecionada, o foco**

![Guia do documento selecionada, o foco](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br />Guia do documento selecionada, o foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.FileTabInactiveGradientTop`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (texto) | `Environment.FileTabInactiveText` |
| Borda | `Environment.FileTabInactiveBorder`<br />(Definido para a mesma cor do plano de fundo). |
| Borda de documento | `Environment.FileTabInactiveDocumentBorderBackground` |

**Guia de plano de fundo do documento: padrão de estado**  

![Guia de documento do plano de fundo padrão](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303-076_BackgroundTab")<br />Guia de documento do plano de fundo padrão  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.FileTabBackground` |
| Em primeiro plano (texto) | `Environment.FileTabText` |
| Borda | `Environment.FileTabBorder`<br />(Definido para a mesma cor do plano de fundo). |

**Guia de plano de fundo do documento: passe o estado**  

![Guia de plano de fundo do documento em foco](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303-077_BackgroundTabHover")<br />Guia de plano de fundo do documento em foco  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.FileTabHotGradientTop`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (texto) | `Environment.FileTabHotText` |
| Borda | `Environment.FileTabHotBorder`<br />(Definido para a mesma cor do plano de fundo). |

#### <a name="preview-tab"></a>Guia de visualização  
Também chamado de uma guia de "provisional". Na guia Visualização aparece à direita do canal de guia do documento quando o usuário clica em um item na janela de ferramenta do Gerenciador de soluções. Ele atua como uma visualização do documento e também fornece ao usuário a opção de manter o documento aberto no lado esquerdo do canal de guia do documento. Guia de visualização apenas abrir pode ser aberto por vez. Guias de visualização têm ambos em segundo plano e estados selecionados, como guias abertas e pode ser focalizado ou foco em seu estado ativo.  

![Guia de visualização (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303-078_PreviewTabRedline")<br />Guia de visualização (corte de funcionários)

| Uso... | Não use... |
| --- | --- |
| ... em qualquer lugar que você está criando provisional visualizar e deseja algum elemento para coincidir com a cor de guia de visualização atual. | ... para qualquer tipo de documento ou guia não é provisional (visualização). |
| | ... para qualquer interface de usuário que você não deseja alterar automaticamente se o shell tem uma atualização de tema. |

**Guia Visualizar determinados, selecionada**  

![Guia Visualizar determinados, selecionada](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303-079_PreviewTabFocused")<br />Guia Visualizar determinados, selecionada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.FileTabProvisionalSelectedActive` |
| Em primeiro plano (texto) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Borda | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Definido para a mesma cor do plano de fundo). |
| Borda de documento | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Guia de visualização de foco, selecionado**  

![Guia de visualização de foco, selecionado](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br />Guia de visualização de foco, selecionado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.FileTabProvisionalSelectedInactive` |
| Em primeiro plano (texto) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Borda | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Borda de documento | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Guia de visualização do plano de fundo: padrão de estado**  

![Guia de visualização de plano de fundo padrão](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br />Guia de visualização de plano de fundo padrão  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.FileTabProvisionalInactive` |
| Em primeiro plano (texto) | `Environment.FileTabProvisionalInactiveForeground` |
| Borda | `Environment.FileTabProvisionalInactiveBorder`<br />(Definido para a mesma cor do plano de fundo). |

**Guia de visualização do plano de fundo: passe o estado**  

![Guia de visualização de plano de fundo em foco](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br />Guia de visualização de plano de fundo em foco  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.FileTabProvisionalHover` |
| Em primeiro plano (texto) | `Environment.FileTabProvisionalHoverForeground` |
| Borda | `Environment.FileTabProvisionalHoverBorder`<br />(Definido para a mesma cor do plano de fundo). |

#### <a name="document-overflow-button"></a>Botão de estouro de documento  
O botão de estouro do documento estiver presente, se houver um ou mais documentos abertos, independentemente se há espaço vertical na configuração atual de acordo com todas as guias do documento. O menu suspenso de estouro de documento, que é controlado pelo [menu da barra de comando](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) cores, exibe uma lista de todos os documentos abertos, visíveis e ocultos e o estouro glifo se altera dependendo se todos os documentos abertos são exibidos no canal de guia.  

![Botão de estouro de documento (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303-083_OverflowRedline")<br />Botão de estouro de documento (corte de funcionários)

| Uso... | Não use... |
| --- | --- |
| ... ao criar um botão de estouro de documento personalizadas. | ... para a interface do usuário que não é semelhante a um botão de estouro. |
| | ... para botões de estouro de barra de comandos. |

**Botão de estouro de documento: padrão de estado**  

![Botão de estouro de documento padrão](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303-084_Overflow")<br />Botão de estouro de documento padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.DocWellOverflowButtonBackground` |
| Em primeiro plano (glifo) | `Environment.DocWellOverflowButtonGlyph` |
| Borda | N/A |

**Botão de estouro de documento: passe o estado**

![Botão de estouro de documento em foco](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303-085_OverflowHover")<br />Botão de estouro de documento em foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Em primeiro plano (glifo) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Borda | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Botão de estouro de documento: pressionado estado**  

![Botão de estouro de documento na pressione](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303-086_OverflowPressed")<br />Botão de estouro de documento na pressione

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Em primeiro plano (glifo) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Borda | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Marcação  
Visual Studio oferece suporte à marcação, que permite que um usuário declarar as palavras-chave pesquisáveis para fins de acompanhamento. Por exemplo, os desenvolvedores e gerentes de projeto podem usar o Team Foundation Server (TFS) para marcar os itens de trabalho. As tabelas a seguir dar nomes de cor para a própria marca e o símbolo "Fechar ícone" que aparece nos Estados selecionados e passe o mouse.  

![Marcação no Visual Studio (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303-176_TaggingRedline")<br />Marcação no Visual Studio (corte de funcionários)  

| Uso... | Não use... |
| --- | --- |
| ... para a interface do usuário que dá suporte à marcação. | ... para qualquer outro tipo de interface do usuário. |

#### <a name="tags"></a>Marcas  

**Marca: estado padrão**

![Marca padrão](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303-177_Tag")<br />Marca padrão

| Elemento | Nome do token: Category.color |
| --- | --- |  
| Informações preliminares | `Tag.Background` |
| Em primeiro plano (texto) | `Tag.Background` |

**Marca: estado de foco**  

![Marca em foco](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303-178_TagHover")<br />Marca em foco  

| Elemento | Nome do token: Category.color |
| --- | --- |  
| Informações preliminares | `Tag.HoverBackground` |
| Em primeiro plano (texto) | `Tag.HoverBackgroundText` |

**Marca: estado de pressionamento**

![Marca pressionada](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303-179_TagPressed")<br />Marca pressionada  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Tag.PressedBackground` |
| Em primeiro plano (texto) | `Tag.PressedBackgroundText` |

**Marca: estado selecionado**

![Marca selecionada](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303-180_TagSelected")<br />Marca selecionada  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Tag.SelectedBackground` |
| Em primeiro plano (texto) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Fechar (&times;) glifo de marca

**Fechar (&times;) marca glifo: padrão de estado**

![Padrão de fechamento (&times;) glifo de marca](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303-181_TagGlyph")<br />Padrão de fechamento (&times;) glifo de marca

| Elemento | Nome do token: Category.color |
| --- | --- |  
| Informações preliminares | N/A |
| Em primeiro plano (glifo) | `Tag.TagHoverGlyph` |

**Fechar (&times;) marca glifo: passe o estado**

![Fechar (&times;) marca glifo em foco](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303-182_TagGlyphHover")<br />Fechar (&times;) marca glifo em foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Tag.TagHoverGlyphHoverBackground` |
| Em primeiro plano (glifo) | `Tag.TagHoverGlyphHover` |
| Borda | `Tag.TagHoverGlyphHoverBorder` |

**Fechar (&times;) marca glifo: pressionado estado**

![Pressionado fechar (&times;) glifo de marca](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303-183_TagGlyphPressed")<br />Pressionado fechar (&times;) glifo de marca

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Tag.TagHoverGlyphPressedBackground` |
| Em primeiro plano (glifo) | `Tag.TagHoverGlyphPressed` |
| Borda | `Tag.TagHoverGlyphPressedBorder` |

**Selecionado marca de fechamento (&times;) glifo: padrão de estado**

![Padrão de marca selecionada com fechamento (&times;) glifo](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303-184_TagSelected")<br />Padrão de marca selecionada com fechamento (&times;) glifo

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | N/A |
| Em primeiro plano (glifo) | `Tag.TagSelectedGlyph` |

**Selecionado marca de fechamento (&times;) glifo: passe o estado**  

![Selecionado marca de fechamento (&times;) glifo em foco](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303-185_TagSelectedHover")<br />Selecionado marca de fechamento (&times;) glifo em foco  


| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Tag.TagSelectedGlyphHoverBackground` |
| Em primeiro plano (glifo) | `Tag.TagSelectedGlyphHover` |
| Borda | `Tag.TagSelectedGlyphHoverBorder` |

**Selecionado marca de fechamento (&times;) glifo: pressionado estado**  

![Selecionada, pressionado marca de fechamento (&times;) glifo](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303-186_TagSelectedPressed")<br />Selecionada, pressionado marca de fechamento (&times;) glifo

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Tag.TagSelectedGlyphPressedBackground` |
| Foreground(glyph) | `Tag.TagSelectedGlyphPressed` |
| Borda | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Janelas de ferramentas  
Não é necessário para replicar as janelas de ferramentas, pois elas são fornecidas pelo ambiente do Visual Studio. No entanto, você pode decidir que deseja utilizar as cores usadas na janela de ferramenta para que a interface do usuário aparece sempre consistente com essa parte do ambiente do Visual Studio.  

![Janela de ferramenta (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303-087_ToolWindowRedline")<br />Janela de ferramenta (corte de funcionários)

| Uso... | Não use... |
| --- | --- |
| ... em qualquer lugar que está criando a interface do usuário que você deseja corresponder janelas de ferramentas. | ... para qualquer interface de usuário que você não deseja alterar automaticamente se o shell tem uma atualização de tema. |

### <a name="tool-window-frame"></a>Quadro de janela de ferramenta  
Janelas de ferramentas no Visual Studio são usadas para muitas tarefas diferentes e podem existir em um dos vários estados diferentes. Se uma janela de ferramentas estiver aberta, ele pode ser atribuído a qualquer um dos quatro lados da área do documento. Janelas de ferramentas também podem flutuar fora do IDE, o que permitirá a ser reposicionadas em qualquer lugar a tela do usuário. Windows flutuantes sempre ficam na parte superior do IDE. Por fim, janelas de ferramentas podem ser encaixadas como janelas de documentos e aparecem como uma guia no documento bem. Janelas de ferramentas foi encaixadas como janelas de documentos são coloridas em parte usando nomes de token de janela de documento.  

![Quadro de janela de ferramenta (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")<br />Quadro de janela de ferramenta (corte de funcionários)

| Uso... | Não use... |
| --- | --- |
| ... em qualquer lugar que está criando a interface do usuário que você deseja corresponder janelas de ferramentas. | ... para qualquer interface de usuário que você não deseja alterar automaticamente se o shell tem uma atualização de tema. |

**Janela de ferramentas encaixada**  

![Janela de ferramentas encaixada](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303-089_ToolWindowDocked")<br />Janela de ferramentas encaixada  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ToolWindowBackground` |
| Borda | `Environment.ToolWindowBorder` |

**Flutuante, voltada para a janela de ferramenta**

![Flutuante, voltada para a janela de ferramenta](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303-090_ToolWindowFocused")<br />Flutuante, voltada para a janela de ferramenta

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ToolWindowBackground` |
| Borda | `Environment.MainWindowActiveDefaultBorder` |

**Flutuante, a janela da ferramenta sem foco**  

![Flutuante, a janela da ferramenta sem foco](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303-091_ToolWindowUnfocused")<br />Flutuante, a janela da ferramenta sem foco  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ToolWindowBackground` |
| Borda | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Janelas com a caixa de ferramentas
A caixa de ferramentas é uma das janelas de ferramenta comuns mais usados no Visual Studio. É essencialmente um controle de árvore com um tema especial e o estilo aplicado.  

![Janela de caixa de ferramentas (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303-189_ToolboxRedline")<br />Janela de caixa de ferramentas (corte de funcionários)

| Uso... | Não use... |
| --- | --- |
| ... ao criar uma janela de ferramenta que você deseja sempre são consistentes com a caixa de ferramentas do shell. | ... para qualquer coisa que não seja semelhante à caixa de ferramentas da interface do usuário, ou se não tiver certeza se a interface do usuário terá problemas se a caixa de ferramentas do shell de alterações de cores. |

**Nós de caixa de ferramentas: padrão de estado**

![Nó de pai de caixa de ferramentas padrão](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303-190_ToolboxParentNode")<br />Nó de pai de caixa de ferramentas padrão

![Nó de filho de caixa de ferramentas padrão](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303-191_ToolboxChildNode")<br />Nó de filho de caixa de ferramentas padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ToolboxContent`<br />(Títulos) |
| Informações preliminares | `Environment.ToolWindowBackground`<br />(Itens individuais ou toda a janela se controles não disponível) |
| Borda | Nenhum |
| Em primeiro plano (glifo) | `Environment.ToolboxContent` |
| Em primeiro plano (texto) | `Environment.ToolboxContent` |

**Nós filho de caixa de ferramentas: passe o estado**

![Nó filho de caixa de ferramentas em foco](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br />Nó filho de caixa de ferramentas em foco  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ToolboxContentMouseOver`<br />(Somente para itens individuais) |
| Borda | Nenhum |
| Em primeiro plano (texto) | `Environment.ToolboxContentMouseOver`<br />(Somente para itens individuais) |

**Caixa de ferramentas nós selecionados: voltada para o estado**

![Nó pai de foco, selecionado da caixa de ferramentas](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br />Nó pai de foco, selecionado da caixa de ferramentas  

![Nó filho de foco, selecionado da caixa de ferramentas](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br />Nó filho de foco, selecionado da caixa de ferramentas

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `TreeView.SelectedItemActive`<br />De [exibição de árvore](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) categoria |
| Borda | `TreeView.FocusVisualBorder`<br />De [exibição de árvore](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) categoria |
| Em primeiro plano (glifo) | `TreeView.SelectedItemActive`<br />De [exibição de árvore](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) categoria |
| Em primeiro plano (texto) | `TreeView.SelectedItemActive`<br />De [exibição de árvore](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) categoria |

**Caixa de ferramentas nós selecionados: o estado de foco**

![Nó de pai selecionado, o foco da caixa de ferramentas](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br />Nó de pai selecionado, o foco da caixa de ferramentas  

![Nó de filho selecionado, o foco da caixa de ferramentas](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br />Nó de filho selecionado, o foco da caixa de ferramentas  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `TreeView.SelectedItemInactive`<br />De [exibição de árvore](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) categoria |
| Borda | Nenhum |
| Em primeiro plano (glifo) | `TreeView.SelectedItemInactive`<br />De [exibição de árvore](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) categoria |
| Em primeiro plano (texto) | `TreeView.SelectedItemInactive`<br />De [exibição de árvore](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) categoria |

### <a name="tool-window-title-bar"></a>Barra de título de janela de ferramenta  
A borda da barra de título não é uma borda true, é uma linha espessa na parte superior da barra de título. Ele não tem um nome de token para seu estado de foco.  

![Barra de título de janela de ferramenta (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")<br />Barra de título de janela de ferramenta (corte de funcionários)

| Uso... | Não use... |
| --- | --- |
| ... em qualquer lugar que está criando a interface do usuário que você deseja corresponder janelas de ferramentas. | ... para qualquer interface de usuário que você não deseja alterar automaticamente se o shell tem uma atualização de tema. |

**Barra de título focada**

![Barra de título focada](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303-093_TitleBarFocused")<br />Barra de título focada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.TitleBarActiveGradientBegin`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (texto) | `Environment.TitleBarActiveText` |
| Borda | `Environment.TitleBarActiveBorder`<br />(Definido para a mesma cor do plano de fundo). |
| Arraste a alça | `Environment.TitleBarDragHandleActive` |

**Barra de título de foco**  

![Barra de título do foco](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303-094_TitleBarUnfocused")<br />Barra de título de foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.TitleBarInactiveGradientBegin`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (texto) | `Environment.TitleBarInactiveText` |
| Borda | N/A |
| Arraste a alça | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Botões de barra de título de janela de ferramenta  
![Botão da barra de título (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")<br />Botão da barra de título (corte de funcionários)  

| Uso... | Não use... |
| --- | --- |
| ... para os botões que aparecem na interface do usuário que usa tokens de cor das barras de título da janela de ferramenta. | ... para os botões que aparecem em outros locais. |
| | ... em qualquer combinação de plano de fundo/primeiro plano diferente do especificado. |

**Botões da barra de título de foco: padrão de estado**

![Padrão, botões da barra de título focada](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br />Padrão, botões da barra de título focada  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | N/A |
| Em primeiro plano (glifo) | `Environment.ToolWindowButtonActiveGlyph` |
| Borda | N/A |

**Botões da barra de título de foco: padrão de estado**

![Padrão, botões da barra de título de foco](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br />Padrão, botões da barra de título de foco    

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | N/A |
| Em primeiro plano (glifo) | `Environment.ToolWindowButtonInactiveGlyph` |
| Borda | N/A |

**Botões da barra de título de foco: passe o estado**  

![Botões da barra de título focada em foco](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br />Botões da barra de título focada em foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ToolWindowButtonHoverActive` |
| Em primeiro plano (glifo) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Borda | `Environment.ToolWindowButtonHoverActiveBorder` |

**Botões da barra de título de foco: passe o estado**  

![Botões da barra de título foco em foco](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br />Botões da barra de título foco em foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ToolWindowButtonHoverInactive` |
| Em primeiro plano (glifo) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Borda | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Botões da barra de título de foco: pressionado estado**

![Botões da barra de título focada em pressione](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br />Botões da barra de título focada em pressione

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ToolWindowButtonDown` |
| Em primeiro plano (glifo) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Borda | `Environment.ToolWindowButtonDownBorder` |

**Botões da barra de título de foco: pressionado estado**

![Botões da barra de título foco em pressione](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br />Botões da barra de título foco em pressione  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ToolWindowButtonDown` |
| Em primeiro plano (glifo) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Borda | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Guias da janela de ferramenta  
![Guia da janela de ferramenta (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303-102_ToolWindowTabRedline")<br />Guia da janela de ferramenta (corte de funcionários)

| Uso... | Não use... |
| --- | --- |
| ... em qualquer lugar que está criando a interface do usuário que você deseja corresponder janelas de ferramentas. | ... para qualquer interface de usuário que você não deseja alterar automaticamente se o shell tem uma atualização de tema. |

**Guia da janela de ferramenta focalizado atualmente selecionado**

![Guia da janela de ferramenta focalizado atualmente selecionado](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br />Guia da janela de ferramenta focalizado atualmente selecionado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ToolWindowTabSelectedTab` |
| Em primeiro plano (texto) | `Environment.ToolWindowTabSelectedActiveText` |
| Borda | `Environment.ToolWindowTabSelectedBorder`<br />(Definido para a mesma cor do plano de fundo). |

**Guia da ferramenta selecionada, o foco de janela**  

![Guia da ferramenta selecionada, o foco de janela](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br />Guia da ferramenta selecionada, o foco de janela

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ToolWindowTabSelectedTab` |
| Em primeiro plano (texto) | `Environment.ToolWindowTabSelectedText` |
| Borda | `Environment.ToolWindowTabSelectedBorder`<br />(Definido para a mesma cor do plano de fundo). |

**Guia de janela de ferramenta do plano de fundo: padrão de estado**

![Guia de janela de ferramenta de plano de fundo padrão](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br />Guia de janela de ferramenta de plano de fundo padrão  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(O gradiente interrompe definido como o mesmo valor de cor no Visual Studio 2013.) |
| Em primeiro plano (texto) | `Environment.ToolWindowTabText` |
| Borda | `Environment.ToolWindowTabBorder` |

**Guia de janela de ferramenta do plano de fundo: passe o estado**

![Guia de janela de ferramenta do plano de fundo em foco](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br />Guia de janela de ferramenta do plano de fundo em foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(O gradiente interrompe definido como o mesmo valor de cor no Visual Studio 2013.) |
| Em primeiro plano (texto) | `Environment.ToolWindowTabMouseOverText` |
| Borda | `Environment.ToolWindowTabMouseOverBorder`<br />(Definido para a mesma cor do plano de fundo). |  

### <a name="auto-hide-tabs"></a>Guias de ocultar automaticamente  

![Guias de ocultar automaticamente (corte de funcionários)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303 107_AutoHideRedline")guias de ocultar automaticamente (corte de funcionários)

| Uso... | Não use... |
| --- | --- |
| ... em qualquer lugar que está criando a interface do usuário que você deseja corresponder guias da janela de ferramenta ocultas automaticamente. | ... para qualquer interface de usuário que você não deseja alterar automaticamente se o shell tem uma atualização de tema. |

**Ocultar automaticamente guias: padrão de estado**  

![Guia de ocultar automaticamente padrão](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303-108_AutoHideTab")<br />Guia de ocultar automaticamente padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.AutoHideTabBackgroundBegin`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (texto) | `Environment.AutoHideTabText` |
| Borda | `Environment.AutoHideTabBorder` |

**Ocultar automaticamente guias: passe o estado**

![Guia de ocultar automaticamente em foco](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303-109_AutoHideTabHover")<br />Guia de ocultar automaticamente em foco  

| Elemento | Nome do token: Category.color |
| --- | --- |
| Informações preliminares | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Marcas de gradiente para este token não é usado na interface do usuário com tema.) |
| Em primeiro plano (texto) | `Environment.AutoHideTabMouseOverText` |
| Borda | `Environment.AutoHideTabMouseOverBorder` |

