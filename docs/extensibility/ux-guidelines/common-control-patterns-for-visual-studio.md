---
title: "Padrões de controle comum do Visual Studio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: 7
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
ms.openlocfilehash: 0eb872e56c95e5090ea21d7daa6f697219bc9d6f
ms.lasthandoff: 02/22/2017

---
# <a name="common-control-patterns-for-visual-studio"></a>Padrões de controle comum do Visual Studio
##  <a name="a-namebkmkcommoncontrolsa-common-controls"></a><a name="BKMK_CommonControls"></a>Controles comuns  
  
### <a name="overview"></a>Visão Geral  
 Controles comuns compõem a maior parte da interface do usuário no Visual Studio. Controles mais comuns usados na interface do Visual Studio devem seguir o [diretrizes de interação de área de trabalho do Windows](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx). Este documento é específico para o Visual Studio e aborda situações especiais ou detalhes de incrementar essas diretrizes do Windows.  
  
#### <a name="common-controls-in-this-topic"></a>Controles comuns neste tópico  
  
-   [Barras de rolagem](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)  
  
-   [Campos de entrada](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)  
  
-   [Caixas de combinação e listas suspensas](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)  
  
-   [Caixas de seleção](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)  
  
-   [Botões de opção](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)  
  
-   [Quadros de grupo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)  
  
-   [Controles de texto](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
-   [Botões e hiperlinks](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
-   [Modos de exibição de árvore](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)  
  
#### <a name="visual-style"></a>Estilo Visual  
 A primeira coisa a considerar ao definir o estilo de controles é se os controles serão usados na interface do usuário com temas. Controles de interface do usuário padrão são a interface do usuário não tema e devem seguir [estilo normal do Windows Desktop](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx), que significa que eles não são re-modelo e devem aparecer na sua aparência de controle padrão.  
  
-   **Caixas de diálogo padrão (utilitário):** não tema. Fazer não re-modelo. Use padrões de estilo de controle básico.  
  
-   **Ferramentas, editores de documento, superfícies de design e caixas de diálogo com temas:** usar especializada aparência com temas usando o serviço de cor.  
  
###  <a name="a-namebkmkscrollbarsa-scrollbars"></a><a name="BKMK_Scrollbars"></a>Barras de rolagem  
 Barras de rolagem devem seguir [padrões comuns de interação para barras de rolagem do Windows](https://msdn.microsoft.com/en-us/library/windows/desktop/bb787527\(v=vs.85\).aspx) , a menos que eles são aumentados com informações de conteúdo, como no editor de códigos.  
  
###  <a name="a-namebkmkinputfieldsa-input-fields"></a><a name="BKMK_InputFields"></a>Campos de entrada  
 Para comportamento de interação típica, siga o [diretrizes de área de trabalho do Windows para caixas de texto](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742442\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Estilo Visual  
  
-   Campos de entrada não devem ser colocados em caixas de diálogo do utilitário. Use o estilo básico intrínseco ao controle.  
  
-   Campos de entrada com temas só devem ser usados no temas caixas de diálogo e janelas de ferramenta.  
  
#### <a name="specialized-interactions"></a>Interações especializadas  
  
-   Campos somente leitura terá um plano de fundo cinza (desabilitado) mas primeiro plano padrão (ativa).  
  
-   Necessário campos devem ter ** \<necessária >** como marcas d'água dentro deles. Você não deve alterar a cor do plano de fundo, exceto em situações raras.  
  
-   Validação de erro: consulte [notificações e o progresso do Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)  
  
-   Campos de entrada devem ser ajustados para caber o conteúdo para se ajustar a largura da janela em que elas são mostradas, nem arbitrariamente corresponde ao tamanho de um campo longo, como um caminho. Comprimento pode ser uma indicação ao usuário de limitações sobre quantos caracteres é permitido no campo.  
  
     ![Largura do controle de campo de entrada incorreta](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")   
     **Tamanho do campo de entrada incorreta: é improvável que o nome será longo.**  
  
     ![Largura do controle de campo de entrada correto](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")   
     **Corrija o comprimento do campo de entrada: O campo de entrada é uma largura razoável para o conteúdo esperado.**  
  
###  <a name="a-namebkmkcomboboxesanddropdownsa-combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a>Caixas de combinação e listas suspensas  
 Para comportamento de interação típica, siga o [diretrizes de área de trabalho do Windows para listas suspensas e caixas de combinação](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742404\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Estilo Visual  
  
-   Nas caixas de diálogo do utilitário, fazer não re-modelo de controle. Use o estilo básico intrínseco ao controle.  
  
-   Na interface do usuário com temas, caixas de combinação e listas suspensas seguem o tema padrão para os controles.  
  
#### <a name="layout"></a>Layout  
 Menus suspensos e caixas de combinação devem ser ajustados para caber o conteúdo para se ajustar a largura da janela em que elas são mostradas, nem arbitrariamente corresponde ao tamanho de um campo longo, como um caminho.  
  
 ![Layout de lista suspensa incorreto](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707&03;_IncorrectDropDownLayout")  
  
 **Tamanho do campo incorreto para um controle de lista suspensa**  
  
 ![Layout da lista suspensa correto](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707&04;_CorrectDropDownLayout")  
  
 **Comprimento do campo correto para um controle de lista suspensa**  
  
###  <a name="a-namebkmkcheckboxesa-check-boxes"></a><a name="BKMK_CheckBoxes"></a>Caixas de seleção  
 Para comportamento de interação típica, siga o [diretrizes de área de trabalho do Windows para caixas de seleção](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742401\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Estilo Visual  
  
-   Nas caixas de diálogo do utilitário, fazer não re-modelo de controle. Use o estilo básico intrínseco ao controle.  
  
-   Na interface do usuário com temas, caixas de seleção siga o tema padrão para os controles.  
  
#### <a name="specialized-interactions"></a>Interações especializadas  
  
-   Interação com uma caixa de seleção nunca deve aparecer uma caixa de diálogo ou navegar para outra área.  
  
-   Alinhe as caixas de seleção com a linha de base da primeira linha de texto.  
  
     ![Alinhamento da caixa de seleção incorreto](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")   
     **Alinhamento da caixa de seleção incorreto: caixa de seleção é centralizada no texto.**  
  
     ![Caixa de seleção correta de alinhamento](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")   
     **Corrija o alinhamento da caixa de seleção: caixa de seleção é alinhada com a linha de base da primeira linha de texto.**  
  
###  <a name="a-namebkmkradiobuttonsa-radio-buttons"></a><a name="BKMK_RadioButtons"></a>Botões de opção  
 Para comportamento de interação típica, siga o [diretrizes de área de trabalho do Windows para botões de opção](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742436\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Estilo Visual  
 Nas caixas de diálogo do utilitário, fazer não botões de opção de estilo. Use o estilo básico intrínseco ao controle.  
  
#### <a name="specialized-interactions"></a>Interações especializadas  
 Não é necessário usar um quadro de grupo para incluir opções de rádio.  
  
###  <a name="a-namebkmkgroupframesa-group-frames"></a><a name="BKMK_GroupFrames"></a>Quadros de grupo  
 Para comportamento de interação típica, siga o [diretrizes de área de trabalho do Windows para quadros de grupo](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742405\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Estilo Visual  
 Nas caixas de diálogo do utilitário, fazer não quadros de grupo de estilo. Use o estilo básico intrínseco ao controle.  
  
#### <a name="layout"></a>Layout  
  
-   Não é necessário usar um quadro de grupo para incluir opções de rádio, a menos que seja necessário manter a distinção de grupo em um layout forte.  
  
-   Nunca use um quadro de grupo para um único controle.  
  
-   Às vezes, é aceitável usar uma régua horizontal em vez de um contêiner de quadro do grupo.  
  
##  <a name="a-namebkmktextcontrolsa-text-controls"></a><a name="BKMK_TextControls"></a>Controles de texto  
  
### <a name="labels"></a>Rótulos  
  
#### <a name="active-label-state"></a>Estado ativo do rótulo  
  
##### <a name="utility-standard-dialogs"></a>Utilitário de caixas de diálogo (padrão))  
  
-   Em geral, siga as orientações de área de trabalho do Windows para rótulos de controle.  
  
-   Nas caixas de diálogo do utilitário, rótulos devem aparecer negrito, na cor de fonte e texto de ambiente padrão. Consulte [fontes e formatação para o Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).  
  
-   Elipses devem sempre seguir rótulos.  
  
##### <a name="signature-themed-dialogs"></a>Caixas de diálogo (temas) de assinatura)  
 Controles de rótulo podem ser em negrito ou cinza claro.  
  
#### <a name="disabled-label-state"></a>Estado de rótulo desativado  
 Rótulos devem refletir a aparência do controle que estão associados. Por exemplo, se o controle associado estiver desabilitado, o rótulo deve aparecer cinza e desabilitado. Isso costuma ser tratado pelo sistema operacional e não exige nenhum tratamento especial.  
  
#### <a name="dynamic-labels"></a>Rótulos dinâmicos  
 Alterar rótulos dinâmico com base na seleção atual. Sempre que possível, use rótulos dinâmicos em layouts de mestre/detalhes para ajudar o usuário a entender que as informações exibidas são relevantes para uma seleção específica e informações gerais não.  
  
 ![Rótulo dinâmico usado com conteúdo dinâmico](../../extensibility/ux-guidelines/media/070702-01_dynamiclabel.png "070702&01;_DynamicLabel")  
  
 **Exemplo de um rótulo dinâmico usado com conteúdo dinâmico**  
  
#### <a name="instructional-text"></a>Texto de instrução  
 Alguns elementos de interface se beneficiar de textos com instruções para ajudar o usuário a entender a finalidade da interface do usuário ou para indicar qual ação executar.  
  
-   Texto de instrução é mais comum na parte superior das caixas de diálogo, mas pode aparecer em outras áreas para dar instruções ao agrupamento de um controle complexo.  
  
-   Texto de instrução não é interativo, mas pode conter hiperlinks para tópicos da Ajuda.  
  
-   Usar instruções com parcimônia e somente quando necessário.  
  
##### <a name="formatting"></a>Formatação  
 Texto de instruções deve ser fonte de ambiente, o texto de controle (com tema) padrão. Consulte [fontes e formatação para o Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).  
  
 Para obter detalhes sobre como escrever instruções, consulte [UI texto e terminologia](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).  
  
 ![Formatação de texto com instrução](../../extensibility/ux-guidelines/media/070702-02_instructionaltextformatting.png "070702&02;_InstructionalTextFormatting")  
  
 **Texto de instruções em uma caixa de diálogo do Visual Studio**  
  
#### <a name="informational-text"></a>Texto informativo  
 Texto informativo é texto que fornece as informações adicionais do usuário. Pode ser estático ou dinâmico ou usado como uma notificação. É sempre somente leitura, mas se ele é útil para o usuário tenha a capacidade de copiar as informações, texto dinâmico deve ser colocado em um contêiner de controle como um campo de texto somente leitura.  
  
##### <a name="dynamic-context-specific-text"></a>Texto (contexto específico) dinâmico  
 Texto de informações dinâmicas muda dependendo do contexto, como quando o usuário alterna o foco. Geralmente, mas nem sempre, conteúdo dinâmico é emparelhado com um rótulo dinâmico.  
  
 ![Texto de informações dinâmicas](../../extensibility/ux-guidelines/media/070702-03_informationaldynamictext.png "070702&03;_InformationalDynamicText")  
  
 **Texto informativo dinâmico altera dependendo do contexto.**  
  
##### <a name="formatting"></a>Formatação  
 Para exibir campos de texto somente leitura de duas maneiras: diretamente na interface do usuário de superfície (veja acima) ou contido dentro de outro controle, como uma caixa de texto ou o quadro do grupo. O está correta dependendo da situação. É responsabilidade do designer de recurso para determinar como apresentar as informações somente leitura.  
  
 Pode ser texto dentro de uma caixa de texto somente leitura. Isso geralmente indica que o conteúdo pode ser selecionado e copiado, embora ele não pode ser editado.  
  
 ![Formatação de campos somente leitura de texto informativo](../../extensibility/ux-guidelines/media/070702-04_informationalformatting.png "070702&04;_InformationalFormatting")  
  
 **Formatação de campos somente leitura de texto informativo**  
  
#### <a name="watermarks"></a>Marcas d'água  
 Embora o texto pode ser o mesmo, a diferença entre as marcas d'água e texto de instrução é que as marcas d'água são substituídas pelo conteúdo quando a janela/controle não está vazia e texto de instrução permanece visível em todos os momentos.  
  
 Marcas d'água devem ser usadas quando um controle ou janela está vazia. Eles indicam o que precisa ser feito para preencher a área e podem incluir links de ação para abrir o windows relevante, como uma fonte.  
  
##### <a name="visual-style"></a>Estilo Visual  
  
-   Marcas d'água devem ser centralizadas horizontalmente dentro da janela.  
  
-   Marcas d'água devem ser centralizado, não alinhado à esquerda.  
  
-   Marcas d'água podem ser centralizadas verticalmente ou posicionadas na parte superior da área. Se localizado próximo à parte superior da área, deve haver espaço suficiente acima para que a marca d'água se destaca.  
  
-   Use o `Environment.GrayText` fonte de ambiente padrão e token de cor. Hiperlinks devem usar os tokens de hyperlink padrão compartilhado: `Environment.PanelHyperlink`, `Environment.PanelHyperlinkHover`, `Environment.PanelHyperlinkPressed`, e `Environment.PanelHyperlinkDisabled`.  
  
-   Marcas d'água não podem ser selecionadas no plano de fundo  
  
-   Se possível, inclua links em marca d'água para ajudar o usuário a se familiarizar.  
  
 ![Marca d'água de texto em uma janela de designer](../../extensibility/ux-guidelines/media/070702-05_watermark1.png "070702&05;_Watermark1")  
  
 ![Marca d'água de texto em uma janela de ferramenta](../../extensibility/ux-guidelines/media/070702-06_watermark2.png "070702&06;_Watermark2")  
  
 **Exemplos de texto de marca d'água no Visual Studio**  
  
##  <a name="a-namebkmkbuttonsandhyperlinksa-buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a>Botões e hiperlinks  
  
### <a name="overview"></a>Visão Geral  
 Controles de botões e links (hiperlinks) devem seguir [orientações básicas da área de trabalho do Windows em hiperlinks](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742406\(v=vs.85\).aspx) para uso, frase, dimensionamento e espaçamento.  
  
### <a name="choosing-between-buttons-and-links"></a>Escolhendo entre botões e links  
 Tradicionalmente, os botões foram usados para ações e hiperlinks foram reservados para navegação. Botões podem ser usados em todos os casos, mas a função de links foi expandida no Visual Studio para que os botões e links são mais intercambiáveis em algumas condições.  
  
 Quando usar os botões de comando:  
  
-   Comandos primários  
  
-   Exibindo do windows usada para coletar informações ou fazer escolhas, mesmo se eles são comandos secundários  
  
-   Ações destrutivas ou irreversíveis  
  
-   Botões de compromisso em assistentes e fluxos de página  
  
 Evitar botões de comando nas janelas de ferramentas, ou se precisar de mais de duas palavras para o rótulo. Os links podem ter mais rótulos.  
  
 Quando usar links:  
  
-   Navegação para outra janela, documento ou página da web  
  
-   Situações que exigem um rótulo mais ou uma frase curta para descrever a intenção da ação  
  
-   Espaços rígidos onde um botão poderia sobrecarregar a interface do usuário, desde que a ação não destrutivo ou irreversível  
  
-   Ocupando comandos secundários em situações em que há muitos comandos  
  
#### <a name="examples"></a>Exemplos  
 ![Uma mensagem de status a seguir os links de comando barra de informações](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703&01;_CommandLinkInfobar")  
  
 **Comando vínculos usados em uma mensagem de status a seguir na barra de informações**  
  
 ![Links usados na janela pop-up do CodeLens](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703&02;_LinksInCodeLens")  
  
 **Links usados na janela pop-up do CodeLens**  
  
 ![Links usados como comandos secundários](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703&03;_LinksAsSecondaryCommands")  
  
 **Usado para comandos secundários onde botões atrairia muita atenção de links**  
  
### <a name="common-buttons"></a>Botões comuns  
  
#### <a name="text"></a>Texto  
 Siga as diretrizes de escrita de [UI texto e terminologia](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).  
  
#### <a name="visual-style"></a>Estilo Visual  
  
##### <a name="standard-dialogs"></a>Caixas de diálogo padrão  
 A maioria dos botões no Visual Studio aparecerão nas caixas de diálogo padrão e não deve ser estilizados. Eles devem refletir a aparência padrão dos botões conforme determinado pelo sistema operacional.  
  
##### <a name="themed"></a>Com temas  
 Em alguns casos, botões podem ser usados dentro da interface do usuário com estilo e esses botões devem ser estilizados adequadamente. Consulte [Dialogs](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) para obter informações sobre controles com temas.  
  
### <a name="special-buttons"></a>Botões especiais  
  
#### <a name="browse-buttons"></a>Procure... botões  
 **[Procurar...] ** botões são usados em grades, caixas de diálogo, janelas de ferramentas e outros elementos de interface do usuário sem janela restrita. Eles exibem um seletor que ajuda o usuário a preencher um valor em um controle. Há duas variações deste botão curtos e longos.  
  
 ![Tempo [...] botão](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703&04;_BrowseLong")  
  
 **O longo botão [procurar...]**  
  
 ![Curto somente reticências [...] botão](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703&05;_BrowseShort")  
  
 **O botão de reticências somente curto [...]**  
  
 Quando usar o botão somente reticências curto:  
  
-   Se houver mais de um longo **[procurar...] ** botão em uma caixa de diálogo, como quando vários campos permitem para navegação. Usar o short **[...] ** botão de cada um para evitar as chaves de acesso confuso criadas por essa situação (**< / procurar** e **B < / rocurar** na mesma caixa de diálogo).  
  
-   Em uma caixa de diálogo rígida ou quando não há nenhum local razoável para colocar o botão longo.  
  
-   Se o botão será exibido em um controle de grade.  
  
 Diretrizes para usar o botão:  
  
-   Não use uma chave de acesso. Para acessá-lo usando o teclado, o usuário deve guia no controle adjacente. Certifique-se de que a ordem de tabulação é, de modo que qualquer botão fica imediatamente após o campo será preenchido. Nunca use um sublinhado abaixo do primeiro período.  
  
-   Definir o Microsoft Active Accessibility (MSAA) **nome** propriedade **procurar... ** (incluindo as reticências) para que a tela leitores Leia como "Procurar" e não "ponto-ponto-ponto" ou "período período-período." Para controles gerenciados, isso significa configuração o **AccessibleName** propriedade.  
  
-   Nunca use reticências **[...] ** botão para nada, exceto uma ação de navegação. Por exemplo, se você precisa de um **[novo...] ** botão, mas não tiver espaço suficiente para o texto, em seguida, a caixa de diálogo precisa ser reprojetada.  
  
##### <a name="sizing-and-spacing"></a>Espaçamento e dimensionamento  
 ![Botões de dimensionamento [procurar...]](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703&06;_BrowseSizing")  
  
 **Botões de dimensionamento [procurar...]**  
  
 ![Botões de espaçamento [procurar...]](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703&07;_BrowseSpacing")  
  
 **Botões de espaçamento [procurar...]**  
  
#### <a name="graphical-buttons"></a>Botões gráficos  
 Alguns botões devem sempre usar uma imagem gráfica e nunca inclua texto para conservar espaço e evitar problemas de localização. Eles geralmente são usados em outras listas classificáveis e seletores de campo.  
  
> [!NOTE]
>  Os usuários precisam de guia para esses botões (não há nenhuma chave de acesso), então colocá-los em uma ordem adequada. Mapear a propriedade de nome do botão para a ação que leva para que os leitores de tela interpretam corretamente a ação do botão.  
  
|||  
|-|-|  
|Adicionar|![Botão gráfico de "Adicionar"](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703&08;_ButtonAdd")|  
|Remover|![Botão gráfico "Remover"](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703&09;_ButtonRemove")|  
|Adicionar Tudo|![Botão gráfico de "Adicionar todos"](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703&10;_ButtonAddAll")|  
|Remover Tudo|![Botão gráfico de "Remover tudo"](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703&11;_ButtonRemoveAll")|  
|Mover Para Cima|![Botão gráfico de "Mover para cima"](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703&12;_ButtonMoveUp")|  
|Mover Para Baixo|![Botão gráfico de "Mover para baixo"](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703&13;_ButtonMoveDown")|  
|Excluir|![Botão "Excluir" gráfico](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703&14;_ButtonDelete")|  
  
##### <a name="sizing-and-spacing"></a>Espaçamento e dimensionamento  
 Dimensionamento para botões gráficos é a mesma versão resumida do **[procurar...] ** botão (26 x&23; pixels):  
  
 ![Botão com e sem cor transparente mostrando](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703&15;_GraphicalButtonSpacing")  
  
 **Aparência de uma imagem gráfica no botão, com e sem cor transparente mostrando**  
  
### <a name="hyperlinks"></a>Hiperlinks  
 Os hiperlinks são adequados para ações com base em navegação, como abrir um tópico da Ajuda, a caixa de diálogo modal ou o assistente. Se for usado um hiperlink para um comando, ele sempre deve exibir uma alteração visível e visível na interface do usuário. Em geral, ações confirmar uma ação (como salvar, cancelar e excluir) são comunicadas melhor usando um botão.  
  
#### <a name="writing-style"></a>Estilo de escrita  
 Execute o [diretrizes de área de trabalho do Windows para o texto da interface do usuário](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx). Não use "Saiba mais sobre," "Conte-me mais sobre" ou a frase "Get help com isso". Frase em vez disso, o texto do link de Ajuda em termos de primário respondida pelo conteúdo da Ajuda. Por exemplo, "**como adicionar um servidor para o Gerenciador de servidores?**"  
  
#### <a name="visual-style"></a>Estilo Visual  
  
-   Os hiperlinks devem sempre usar [o serviço de VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Se um hiperlink não possui estilo corretamente, ela pisca em vermelho quando ativo ou mostra uma cor diferente depois que está sendo visitado.  
  
-   Não inclua sublinhados no controle de posicionar o estado, a menos que o link é um fragmento da sentença em uma frase completa, como em uma marca d'água.  
  
-   Sublinhado não deve aparecer em foco. Em vez disso, os comentários para o usuário que o link está ativo são uma alteração de cor pequena e o cursor de link apropriado.  
  
##  <a name="a-namebkmktreeviewsa-tree-views"></a><a name="BKMK_TreeViews"></a>Modos de exibição de árvore  
  
### <a name="overview"></a>Visão Geral  
 Modos de exibição de árvore fornecem uma maneira de organizar complexo lista em grupos pai-filho. Um usuário pode expandir ou recolher grupos pai para revelar ou ocultar itens filho subjacente. Cada item em uma exibição de árvore pode ser selecionado para fornecer mais ação.  
  
 Este tópico aborda o uso aceitável, design apropriado e funcionalidade de modos de exibição de árvore.  
  
#### <a name="in-this-topic"></a>Neste tópico  
  
-   [Estilo Visual](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewVisualStyle)  
  
-   [Interações](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewInteractions)  
  
###  <a name="a-namebkmktreeviewvisualstylea-visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a>Estilo Visual  
  
#### <a name="expanders"></a>Expansores  
 Controles de exibição de árvore devem estar de acordo com o design de expansor usado pelo Windows e Visual Studio. Cada nó usa um controle expansor para mostrar ou ocultar os itens subjacentes. Usar um controle expansor fornece consistência para os usuários que podem encontrar modos de exibição de árvore diferente no Windows e o Visual Studio.  
  
 ![Corrija o controle de exibição de árvore](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705&1;_TreeViewCorrect")  
  
 **Correto: estilo adequado exibição do nó de árvore usando um controle expansor**  
  
 ![Nós de modo de exibição de árvore incorreto](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705&2;_TreeViewIncorrect1")  
  
 **Incorreto: estilo de inadequada exibição do nó de árvore**  
  
#### <a name="selection"></a>Seleção  
 Quando um nó é selecionado no modo de exibição de árvore, o realce deve expandir a largura total do controle de exibição de árvore. Isso ajuda os usuários a identificar claramente que o item selecionado. Cores de seleção devem refletir o tema atual do Visual Studio.  
  
 ![Corrija o controle de exibição de árvore](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705&1;_TreeViewCorrect")  
  
 **Correto: realce do nó selecionado se encaixa em toda a largura do controle de exibição de árvore.**  
  
 ![Realce de exibição de árvore incorreto](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705&3;_TreeViewIncorrect2")  
  
 **Incorreta: realce do nó selecionado não é adequado para toda a largura do controle de exibição de árvore.**  
  
#### <a name="icons"></a>Ícones  
 Ícones só devem ser usados em controles de exibição de árvore se eles ajudar a identificar visualmente as diferenças entre os itens. Em geral, os ícones devem ser usados somente nas listas heterogêneas na qual os ícones transportam informações para diferenciar os tipos de elementos. Em uma lista homogênea usando ícones frequentemente podem ser visto como ruído e deve ser evitado. Nesse caso, o ícone do grupo (pai) pode transmitir o tipo de itens dentro dela. A exceção a essa regra seria se o ícone é dinâmico e é usado para indicar o estado.  
  
#### <a name="scroll-bars"></a>Barras de rolagem  
 Barras de rolagem sempre devem ser ocultadas se o conteúdo caiba no controle de exibição de árvore. É aceitável para barras de rolagem estar oculto ou semitransparente em uma janela rolável e aparecem quando a janela que contém o modo de exibição de árvore tem o foco ou no foco da árvore de exibição também.  
  
 ![Árvore de exibição com as barras de rolagem](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705&4;_Scrollbars")  
  
 **Ambas as barras de rolagem vertical e horizontal são exibidas porque o conteúdo excederam os limites do controle de exibição de árvore.**  
  
###  <a name="a-namebkmktreeviewinteractionsa-interactions"></a><a name="BKMK_TreeViewInteractions"></a>Interações  
  
#### <a name="context-menus"></a>Menus de contexto  
 Um nó do modo de exibição de árvore pode revelar as opções do submenu em um menu de contexto. Normalmente, isso ocorre quando um usuário pequeno um item ou pressionar a tecla de Menu em um teclado do Windows com o item selecionado. É importante que o nó obtém foco e está selecionado. Isso ajuda o usuário a identificar qual item de submenu pertence.  
  
 ![Menu de contexto e o nó selecionado na árvore](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705&5;_ContextMenu")  
  
 **O item que tem gerar o foco de ganhos do menu de contexto para notificar o usuário que o item foi selecionado.**  
  
#### <a name="keyboard"></a>Teclado  
 O modo de exibição de árvore deve fornecer a capacidade de expandir/recolher nós usando o teclado e selecionar itens. Isso garante que a navegação atenda aos nossos requisitos de acessibilidade.  
  
##### <a name="tree-view-control"></a>Controle de exibição de árvore  
 Controles de árvore Visual Studio devem seguir comuns de navegação de teclado:  
  
-   **Seta para cima:** selecione itens movendo a árvore  
  
-   **Seta para baixo:** selecione itens movendo para baixo da árvore  
  
-   **Seta para a direita:** expanda um nó na árvore  
  
-   **Seta para a esquerda:** recolher um nó na árvore  
  
-   **Insira a chave:** Iniciar, carregar, executar o item selecionado  
  
##### <a name="trid-tree-view-and-grid-view"></a>Trid (exibição de árvore e exibição de grade)  
 Um controle trid é um controle complexo que contém um modo de exibição de árvore em uma grade. Expandir, recolher e navegar a árvore devem respeitar os mesmos comandos de teclado que um modo de exibição de árvore, com as seguintes adições:  
  
-   **Seta para a direita:** expanda um nó. Depois que o nó é expandido, ele deve continuar navegando até a coluna mais à direita. Navegação deve parar no final da linha.  
  
-   **Guia:** navega para a célula mais próxima à direita.  No final da linha, navegação continua na próxima linha.  
  
-   **Shift + Tab:** navega para a célula mais à esquerda.  No início da linha, navegação continua a célula mais à direita na linha anterior.  
  
 ![Controle Trid no Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705&6;_Trid")  
  
 **Um controle trid no Visual Studio**
