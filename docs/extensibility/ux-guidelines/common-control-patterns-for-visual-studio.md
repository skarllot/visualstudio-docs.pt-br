---
title: "Padrões de controle comuns para Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 04/26/2017
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9524ecc3cadef58821fba857de8e82e59eea9b43
ms.openlocfilehash: 185fc30458fed4303eb0cf6d59b5e6784840f89e
ms.contentlocale: pt-br
ms.lasthandoff: 05/04/2017

---
# <a name="common-control-patterns-for-visual-studio"></a>Padrões de controle comuns para Visual Studio
##  <a name="BKMK_CommonControls"></a>Controles comuns  
  
### <a name="overview"></a>Visão Geral  
Controles comuns representam a maioria da interface do usuário no Visual Studio. Controles comuns mais usados na interface do Visual Studio devem seguir o [diretrizes de interação de área de trabalho do Windows](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx). Este tópico é específico para o Visual Studio e abrange situações especiais ou detalhes que aumentar as diretrizes do Windows.  
  
#### <a name="common-controls-in-this-topic"></a>Controles comuns neste tópico  
  
-   [Barras de rolagem](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)  
  
-   [Campos de entrada](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)  
  
-   [Caixas de combinação e listas suspensas](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)  
  
-   [Caixas de seleção](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)  
  
-   [Botões de opção](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)  
  
-   [Quadros de grupo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)  
  
-   [Controles de texto](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
-   [Hiperlinks e botões](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
-   [Modos de exibição de árvore](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)  
  
#### <a name="visual-style"></a>Estilo Visual  
A primeira coisa a considerar ao estilo de controles é se os controles serão usados na interface do usuário com tema. Controles de interface do usuário padrão são a interface do usuário não com tema e devem seguir [estilo normal do Windows Desktop](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx), que significa que eles não são re-modelo e devem aparecer na sua aparência de controle padrão.  
  
-   **Caixas de diálogo padrão (utilitário):** não com tema. Não re-template. Use padrões de estilo do controle básico.  
  
-   **Ferramentas, editores de documento, superfícies de design e caixas de diálogo com tema:** usar especializada aparência com tema usando o serviço de cor.  
  
###  <a name="BKMK_Scrollbars"></a>Barras de rolagem  
 Barras de rolagem devem seguir [barras de rolagem de padrões comuns de interação para Windows](https://msdn.microsoft.com/en-us/library/windows/desktop/bb787527\(v=vs.85\).aspx) , a menos que eles são aumentados com informações de conteúdo, como no editor de códigos.  
  
###  <a name="BKMK_InputFields"></a>Campos de entrada  
 Para o comportamento de interação típica, siga o [diretrizes de área de trabalho do Windows para caixas de texto](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742442\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Estilo Visual  
  
-   Campos de entrada não devem ser colocados em caixas de diálogo do utilitário. Use o estilo básico intrínseco ao controle.  
  
-   Campos de entrada com tema só devem ser usados em caixas de diálogo com tema e janelas de ferramenta.  
  
#### <a name="specialized-interactions"></a>Interações especializadas  
  
-   Campos somente leitura terá um plano de fundo cinza (desabilitado) mas padrão (ativo) no primeiro plano.  
  
-   Necessário campos devem ter  **\<necessário >** como marcas d'água dentro deles. Você não deve alterar a cor do plano de fundo, exceto em situações raras.  
  
-   Validação de erro: consulte [notificações e o progresso do Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)  
  
-   Campos de entrada devem ser dimensionados para ajustar o conteúdo não se ajustar à largura da janela em que elas serão mostradas nem arbitrariamente corresponde ao tamanho de um campo longo, como um caminho. Comprimento pode ser uma indicação para o usuário das limitações quanto o número de caracteres é permitido no campo.  
  
     ![Tamanho do campo de entrada incorreta: é improvável que o nome será nesse longo.](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")<br />Tamanho do campo de entrada incorreta: é improvável que o nome será nesse longo.
  
     ![Corrija o comprimento do campo de entrada: o campo de entrada é uma largura razoável para o conteúdo esperado.](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />Corrija o comprimento do campo de entrada: o campo de entrada é uma largura razoável para o conteúdo esperado.
  
###  <a name="BKMK_ComboBoxesAndDropDowns"></a>Caixas de combinação e listas suspensas  
Para o comportamento de interação típica, siga o [diretrizes de área de trabalho do Windows para listas suspensas e caixas de combinação](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742404\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Estilo Visual  
  
-   Nas caixas de diálogo do utilitário, não re-modelo de controle. Use o estilo básico intrínseco ao controle.  
  
-   Na interface do usuário com tema, caixas de combinação e listas suspensas seguem o tema padrão para os controles.  
  
#### <a name="layout"></a>Layout  
Caixas de combinação e listas suspensas devem ser dimensionadas para ajustar o conteúdo não se ajustar à largura da janela em que elas serão mostradas nem arbitrariamente corresponde ao tamanho de um campo longo, como um caminho.  
  
![Incorreto: a largura da lista suspensa é muito longa para o conteúdo que será exibido.](~/docs/extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />Incorreto: a largura da lista suspensa é muito longa para o conteúdo que será exibido.
  
![Correto: na lista suspensa é dimensionada para permitir o crescimento de tradução, mas não desnecessariamente longas.](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707-04_CorrectDropDownLayout")<br />Correto: na lista suspensa é dimensionada para permitir o crescimento de tradução, mas não desnecessariamente longas. 
  
###  <a name="BKMK_CheckBoxes"></a>Caixas de seleção  
Para o comportamento de interação típica, siga o [diretrizes de área de trabalho do Windows para caixas de seleção](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742401\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Estilo Visual  
  
-   Nas caixas de diálogo do utilitário, não re-modelo de controle. Use o estilo básico intrínseco ao controle.  
  
-   Na interface do usuário com tema, caixas de seleção siga o tema padrão para os controles.  
  
#### <a name="specialized-interactions"></a>Interações especializadas  
  
-   Interação com uma caixa de seleção nunca deve ser exibida uma caixa de diálogo ou navegue para outra área.  
  
-   Alinhe as caixas de seleção com a linha de base da primeira linha do texto.  
  
     ![Incorreto: a caixa de seleção é centralizada no texto.](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />Incorreto: a caixa de seleção é centralizada no texto.
  
     ![Correto: a caixa de seleção é alinhada com a primeira linha do texto.](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />Correto: a caixa de seleção é alinhada com a primeira linha do texto.
  
###  <a name="BKMK_RadioButtons"></a>Botões de opção  
Para o comportamento de interação típica, siga o [diretrizes de área de trabalho do Windows para botões de opção](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742436\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Estilo Visual  
Nas caixas de diálogo do utilitário, faça não botões de opção de estilo. Use o estilo básico intrínseco ao controle.  
  
#### <a name="specialized-interactions"></a>Interações especializadas  
Não é necessário usar um quadro de grupo para incluir opções de rádio, a menos que você precisa manter distinção de grupo em um layout forte.  
  
###  <a name="BKMK_GroupFrames"></a>Quadros de grupo  
Para o comportamento de interação típica, siga o [diretrizes de área de trabalho do Windows para os quadros de grupo](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742405\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Estilo Visual  
No utilitário de caixas de diálogo, não estilo quadros de grupo. Use o estilo básico intrínseco ao controle.  
  
#### <a name="layout"></a>Layout  
  
-   Não é necessário usar um quadro de grupo para incluir opções de rádio, a menos que você precisa manter distinção de grupo em um layout forte.  
  
-   Nunca use um quadro de grupo para um único controle.  
  
-   Às vezes, é aceitável para usar uma regra horizontal em vez de um contêiner de quadro de grupo.  
  
##  <a name="BKMK_TextControls"></a>Controles de texto

### <a name="static-text-fields"></a>Campos de texto estático

Um campo de texto estático apresenta informações de somente leitura e não pode ser selecionado pelo usuário. Evite usá-lo para qualquer texto que o usuário talvez queira copiar na área de transferência. No entanto, somente leitura texto estático pode ser alterado para refletir uma alteração de estado. No exemplo a seguir, o texto estático de nome de saída em que as alterações de informações de grupo para refletir as alterações feitas na caixa de texto do Namespace raiz acima dele.

Há duas maneiras de exibir informações de texto estático.

Texto estático pode ser em seu próprio em uma caixa de diálogo sem qualquer contenção quando não há nenhum conflito de agrupamento. Decida se as linhas de uma caixa adicionais são realmente necessárias. Um exemplo é a exibição de um caminho de diretório em uma seção criada por uma linha de grupo, conforme mostrado abaixo:  

![Informações de texto estático em controles de texto](~/docs/extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />Informações de texto estático em controles de texto

Na caixa de diálogo onde existem outras áreas agrupadas e confinamento das informações de ajuda a legibilidade, e quando uma seção pode ser ocultada ou exibida (como no **janela propriedades** painel de descrição) ou você deseja ser consistente com a interface do usuário semelhante, coloque o texto dentro de uma caixa. Essa caixa de grupo deve ser uma única regra e colorida com o `ButtonShadow`:

![Texto estático na janela Propriedades](~/docs/extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />Texto estático na janela Propriedades

### <a name="read-only-text-box"></a>Caixa de texto somente leitura

Isso permite que o usuário selecionar o texto dentro do campo, mas não editá-lo. Essas caixas de texto são com borda por que o usual Cinzel 3D com um `ButtonShadow` preenchimento.

Uma caixa de texto pode se tornar ativa (editável) quando um usuário altera um controle, como verificação/desmarcar uma caixa de seleção ou selecionar/Cancelar a seleção um botão de opção. Por exemplo, no **ferramentas &gt; opções** página mostrada abaixo, o **Home Page** caixa de texto se torna ativa quando o **usar padrão** caixa de seleção está desmarcada.

![Caixa de texto somente leitura, mostrando os estados ativos e inativos](~/docs/extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Caixa de texto somente leitura, mostrando os estados ativos e inativos

### <a name="using-text-in-dialogs"></a>Usando texto em caixas de diálogo

Diretrizes importantes para texto em caixas de diálogo:

-   Rótulos para caixas de texto, caixas de listagem e quadros em caixas de diálogo unthemed iniciar com um verbo, tem um capital inicial em apenas a primeira palavra e terminam com um vírgula.

    > Controles de texto em caixas de diálogo com tema siga [diretrizes UX da área de trabalho do Windows](https://msdn.microsoft.com/library/windows/desktop/dn742479.aspx) e não tirar pontuação final, com exceção dos pontos de interrogação em links de Ajuda.

-   Rótulos para caixas de seleção e botões de opção começam com um verbo, um capital inicial em apenas a primeira palavra e tem sem pontuação final.

-   Rótulos de guias, menus, itens de menu e botões tem iniciais maiusculas em cada palavra (maiusculas/minúsculas).

-   Terminologia de rótulo deve ser consistente com rótulos semelhantes em outras caixas de diálogo.

-   Se possível, ter um editor de gravador/gravação ou aprovar o texto antes que ele passa para o desenvolvedor para implementação.

-   Todos os controles devem ter rótulos exceto em circunstâncias especiais em qual tabulação é suficiente.
Use texto auxiliar quando apropriado.

### <a name="helper-text"></a>Texto de ajuda

Incluído nas caixas de diálogo para ajudar o usuário a entender a finalidade da caixa de diálogo ou indicar qual ação realizar. Texto de Ajuda deve ser usado apenas quando necessário, para evitar problemas de caixas de diálogo simples. Duas variações do texto de ajuda são a caixa de diálogo e marca d'água.

Siga os locais comuns para texto de auxiliar e ser seletivo na introdução de novas áreas. Cenários comuns para texto de ajuda são:

-   Texto de auxiliar em caixas de diálogo, para dar a direção adicional sobre como interagir com uma caixa de diálogo complexas.

-   Texto de marca d'água em janelas de ferramentas vazio ou caixas de diálogo, para explicar por que não é visível a nenhum conteúdo.

-   Um painel de descrição, na parte inferior, como o **janela propriedades**.

-   Marca d'água de texto em um editor vazio, para explicar a ação que o usuário deve tomar para começar.
  
### <a name="dialog-helper-text"></a>Texto de Ajuda da caixa de diálogo

Um designer de experiência do usuário pode ajudar a determinar quando o texto de Ajuda é apropriado. O designer pode definir onde o texto de Ajuda aparece, bem como seu conteúdo geral. Assistência ao usuário pode gravar/editar o texto real.

### <a name="watermarks"></a>Marcas d'água

Caixas de diálogo se beneficiar com as diretrizes de marca d'água ligeiramente diferente. Como uma caixa de diálogo pode aparecer ocupada com muitos elementos de interface do usuário (rótulos, texto, botões e outros controles de contêiner com texto), especialmente quando os aparecem em preto, marcas d'água destacam melhor em cinza escuro (VSColor: `ButtonShadow`). Normalmente uma marca d'água aparece dentro de um controle como uma caixa de listagem com um plano de fundo branco (VSColor: `Window`).

-   O texto é exibido em cinza escuro (VSColor: `ButtonShadow`). No entanto, se a marca d'água aparece em um cinza ou outras cores (VSColor: `ButtonFace`) em segundo plano e não há preocupar sobre sua legibilidade, vá com texto em preto (VSColor: `WindowText`).

-   As marcas d'água podem ser centralizadas ou recuo à esquerda. Aplica regras de design padrão ao tomar decisões de alinhamento. A marca d'água não pode ser selecionada no plano de fundo.

![Exemplo de texto de marca d'água](~/docs/extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Exemplo de texto de marca d'água

### <a name="context-specific-dynamic-text"></a>Texto de contexto específico (dinâmico)

Texto dinâmico pode ser usado de duas maneiras em uma caixa de diálogo ou a interface do usuário sem janela restrita: como um rótulo dinâmico ou como o conteúdo dinâmico.

-   Rótulo dinâmico: é um uso comum de texto dinâmico em painéis descritivos que oferecem mais informações para o item selecionado, como em uma caixa de diálogo que contém uma lista de elementos e propriedades para esses elementos exibidos em uma grade à direita. O rótulo para a grade de propriedade pode ser dinâmico para que quando um item é selecionado à esquerda, a grade à direita mostra as informações desse item específico.

-   Texto dinâmico: pode ser útil em casos onde você precisa exibir informações específicas e as informações gerais não dessa maneira, mas tome cuidado para não sobrecarregar.

Se desejar que os usuários tenham a capacidade de copiar as informações, texto dinâmico deve ser um campo de texto somente leitura.
  
##  <a name="BKMK_ButtonsAndHyperlinks"></a>Hiperlinks e botões  
  
### <a name="overview"></a>Visão Geral  
Controles de botões e links (hiperlinks) devem seguir [diretrizes básicas de área de trabalho do Windows em hiperlinks](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742406\(v=vs.85\).aspx) para uso de palavras, dimensionamento e espaçamento.  
  
### <a name="choosing-between-buttons-and-links"></a>Escolhendo entre os botões e links  
Tradicionalmente, os botões foram usados para ações e hiperlinks foram reservados para navegação. Botões podem ser usados em todos os casos, mas a função de links foi expandida no Visual Studio para que os botões e links são mais intercambiáveis em algumas condições.  
  
Quando usar os botões de comando:  
  
-   Comandos primários  
  
-   Exibição do windows usado para coletar informações ou fazer escolhas, mesmo se eles são comandos secundários  
  
-   Ações destrutivas ou irreversíveis  
  
-   Botões de compromisso em assistentes e fluxos de página  
  
Evite botões de comando nas janelas de ferramentas, ou se você precisar de mais de duas palavras para o rótulo. Links podem ter mais rótulos.  
  
 Quando usar links:  
  
-   Navegação para outra janela, documento ou página da web  
  
-   Situações que exigem um maior rótulo ou uma frase curta para descrever a intenção da ação  
  
-   Espaços total em que um botão seria sobrecarregar a interface do usuário, desde que a ação não destrutiva ou irreversível  
  
-   Ocupando comandos secundários em situações em que há muitos comandos  
  
#### <a name="examples"></a>Exemplos  
![Links de comando usada na barra de informações a seguir de uma mensagem de status](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />Links de comando usada na barra de informações a seguir de uma mensagem de status
  
![Vínculos usados em pop-up do CodeLens](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />Vínculos usados em pop-up do CodeLens
  
![Usado para comandos secundários onde botões atrairia muita atenção de links](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />Usado para comandos secundários onde botões atrairia muita atenção de links
  
### <a name="common-buttons"></a>Botões comuns  
  
#### <a name="text"></a>Texto  
Siga as diretrizes de gravação em [UI texto e terminologia](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).  
  
#### <a name="visual-style"></a>Estilo Visual  
  
##### <a name="standard-unthemed"></a>Padrão (unthemed)  
A maioria dos botões no Visual Studio será exibido nas caixas de diálogo do utilitário e não deve ser o estilo. Eles devem refletir a aparência padrão dos botões conforme determinado pelo sistema operacional.  
  
##### <a name="themed"></a>Com tema  
Em algumas instâncias, botões podem ser usados dentro da interface do usuário com estilo e esses botões devem ser denominados adequadamente. Consulte [caixas de diálogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) para obter informações sobre controles com tema.  
  
### <a name="special-buttons"></a>Botões especiais  
  
#### <a name="browse-buttons"></a>Botões de navegação...  
**[Procurar...]**  botões são usados em grades, caixas de diálogo, janelas de ferramentas e outros elementos de interface do usuário sem janela restrita. Eles exibem um seletor que ajuda a preencher um valor em um controle de usuário. Há duas variações deste botão longas e curtas.  
  
![O botão [procurar...] longo](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />O botão [procurar...] longo
  
![O botão de reticências somente curto [...]](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />O botão de reticências somente curto [...]
  
Quando usar o botão curto somente reticências:  
  
-   Se houver mais de um longo **[procurar...]**  botão em uma caixa de diálogo, como quando vários campos permitem para navegação. Use curto **[...]**  botão para cada um evitar as chaves de acesso confuso criadas por essa situação (**& Procurar** e **p & rocurar** na mesma caixa de diálogo).  
  
-   Em uma caixa de diálogo rígida ou quando não há nenhum local razoável para colocar o botão longo.  
  
-   Se o botão será exibido em um controle de grade.  
  
Diretrizes para usar o botão:  
  
-   Não use uma chave de acesso. Para acessá-lo usando o teclado, o usuário deve guia do controle adjacente. Certifique-se de que a ordem de tabulação é, de modo que qualquer botão fica imediatamente após o campo será preenchido. Nunca use um sublinhado abaixo do primeiro ponto.  
  
-   Definir o Microsoft Active Accessibility (MSAA) **nome** propriedade **procurar...**  (incluindo as reticências) para que a tela leitores lerá como "Procurar" e não "ponto-ponto-ponto" ou "período período-período." Para controles gerenciados, isso significa que configuração de **AccessibleName** propriedade.  
  
-   Nunca use reticências **[...]**  botão para qualquer coisa, exceto uma ação de navegação. Por exemplo, se você precisar de um **[novo...]**  botão, mas não tem espaço suficiente para o texto, em seguida, a caixa de diálogo precisa ser reprojetada.  
  
##### <a name="sizing-and-spacing"></a>Espaçamento e dimensionamento  
![Botões de dimensionamento [procurar...]: versão padrão é de 75 x 23 pixels, versão curta é 26 horas 23 pixels](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />Botões de dimensionamento [procurar...]
  
![Botões de espaçamento [procurar...]: espaçamento entre controle relacionado e padrão pixels de 7 de botão de procura, o espaçamento entre controle relacionada e procurar curto botão 5 pixels](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />Botões de espaçamento [procurar...]
  
#### <a name="graphical-buttons"></a>Botões gráficos  
Alguns botões devem sempre usar uma imagem de gráfica e nunca incluir o texto para economizar espaço e evitar problemas de localização. São geralmente usados em seletores de campo e outras listas classificáveis.  
  
> **Observação:** os usuários precisam de guia para esses botões (não há nenhuma chave de acesso), portanto, coloque-os em uma ordem a sensata. Mapa de `name` propriedade do botão para a ação que leva para que os leitores de tela interpretam corretamente a ação do botão.  
  
| Função | Botão |  
| --- | --- |  
| Adicionar | ![Botão "Adicionar" gráfico](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703 08_ButtonAdd") |
| Remover | ![Botão gráfico "Remover"](~/docs/extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703 09_ButtonRemove") |
| Adicionar Tudo | ![Botão "Adicionar tudo" gráfico](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703 10_ButtonAddAll") |
| Remover Tudo | ![Botão gráfico de "Remover tudo"](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703 11_ButtonRemoveAll") |
| Mover Para Cima | ![Botão gráfico "Mover para cima"](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703 12_ButtonMoveUp") |
| Mover Para Baixo | ![Botão gráfico "Mover para baixo"](~/docs/extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703 13_ButtonMoveDown") |
| Excluir | ![Botão gráfico "Delete"](~/docs/extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703 14_ButtonDelete") |
  
##### <a name="sizing-and-spacing"></a>Espaçamento e dimensionamento  
Dimensionamento para botões gráfica é igual à versão resumida do **[procurar...]**  botão (26 x 23 pixels):  
  
![Aparência de uma imagem de gráfica no botão, com e sem cor transparente mostrando](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />Aparência de uma imagem de gráfica no botão, com e sem cor transparente mostrando
  
### <a name="hyperlinks"></a>Hiperlinks  
Os hiperlinks são adequados para ações com base em navegação, como abrir um tópico da Ajuda, a caixa de diálogo modal ou o assistente. Se for usado um hiperlink para um comando, ele sempre deve exibir uma alteração perceptível e visível na interface do usuário. Em geral, ações de confirmação para uma ação (como salvar, cancelar e excluir) são comunicadas melhor usando um botão.  
  
#### <a name="writing-style"></a>Estilo de escrita  
Siga o [orientação de área de trabalho do Windows para o texto de interface do usuário](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx). Não use "Saiba mais sobre," "Conte-me mais sobre" ou "Obter ajuda com esse" frases. Frase em vez disso, o texto do link de Ajuda em termos primário pergunta, o conteúdo da Ajuda. Por exemplo, "**como adicionar um servidor para o Gerenciador de servidores?**"  
  
#### <a name="visual-style"></a>Estilo Visual  
  
-   Hiperlinks sempre devem usar [o serviço de VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Se um hiperlink não tiver estilo corretamente, ele pisca em vermelho quando ativa ou mostra uma cor diferente depois de visitação.  
  
-   Não inclua um sublinhado no controle posicionar o estado, a menos que o link é um fragmento de sentença dentro de uma sentença completa, como em uma marca d'água.  
  
-   Um sublinhado não deve aparecer em foco. Em vez disso, os comentários para o usuário que o link está ativo são uma alteração de cor pequenas e o cursor de link apropriado.  
  
##  <a name="BKMK_TreeViews"></a>Modos de exibição de árvore  
  
Modos de exibição de árvore fornecem uma maneira de organizar complexo lista em grupos pai-filho. Um usuário pode expandir ou recolher grupos pai para revelar ou ocultar itens filho subjacente. Cada item em uma exibição de árvore pode ser selecionado para fornecer mais ação.  
  
###  <a name="BKMK_TreeViewVisualStyle"></a>Estilo visual do modo de exibição de árvore  
  
#### <a name="expanders"></a>Expansores  
Controles de exibição de árvore devem estar de acordo com o design de expansão usado pelo Windows e o Visual Studio. Cada nó usa um controle expander para mostrar ou ocultar os itens subjacentes. Usar um controle expander fornece consistência para usuários que podem ser encontrados modos de exibição de árvore diferente no Windows e o Visual Studio.  
  
![Correto: estilo adequado do nó do modo de exibição de árvore usando um controle expander](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Correto: estilo adequado do nó do modo de exibição de árvore usando um controle expander
  
![Incorreta: estilo de inadequada modo de exibição do nó de árvore](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />Incorreta: estilo de inadequada modo de exibição do nó de árvore
  
#### <a name="selection"></a>Seleção  
Quando um nó é selecionado na exibição de árvore, o realce deve expandir para a largura total do controle de exibição de árvore. Isso ajuda os usuários a identificar claramente o item selecionado. Cores de seleção devem refletir o tema atual do Visual Studio.  
  
![Correto: realce do nó selecionado se ajusta a toda a largura do controle de exibição de árvore.](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Correto: realce do nó selecionado se ajusta a toda a largura do controle de exibição de árvore.
  
![Incorreta: o realce do nó selecionado não couber toda a largura do controle de exibição de árvore.](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />Incorreta: o realce do nó selecionado não couber toda a largura do controle de exibição de árvore.
  
#### <a name="icons"></a>Ícones  
Ícones só devem ser usados em controles de exibição de árvore se eles ajudar a identificar visualmente as diferenças entre os itens. Em geral, os ícones devem ser usados somente nas listas heterogêneas em que os ícones de transportam informações para diferenciar os tipos de elementos. Em uma lista homogênea usando ícones com frequência podem ser visto como ruído e deve ser evitado. Nesse caso, o ícone do grupo (pai) pode transmitir o tipo de itens dentro dela. A exceção a essa regra seria se o ícone é dinâmico e é usado para indicar o estado.  
  
#### <a name="scroll-bars"></a>Barras de rolagem  
Barras de rolagem sempre devem ser ocultadas se o conteúdo caiba no controle de exibição de árvore. É aceitável para as barras de rolagem seja oculto ou semi-transparente em uma janela rolável e aparecem quando a janela que contém o modo de exibição de árvore tem o foco, ou após o foco da árvore de exibição também.  
  
![Ambas as barras de rolagem vertical e horizontal são exibidas porque o conteúdo excederam os limites do controle de exibição de árvore.](~/docs/extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />Ambas as barras de rolagem vertical e horizontal são exibidas porque o conteúdo excederam os limites do controle de exibição de árvore.
  
###  <a name="BKMK_TreeViewInteractions"></a>Interações de modo de exibição de árvore  
  
#### <a name="context-menus"></a>Menus de contexto  
Um nó de exibição de árvore pode revelar as opções do submenu em um menu de contexto. Normalmente, isso ocorre quando um usuário é pequeno um item ou pressionar a tecla de Menu em um teclado do Windows com o item selecionado. É importante que o nó ganha o foco e está selecionado. Isso ajuda o usuário a identificar qual item de submenu pertence.  
  
![O item que tem gerar o foco de ganhos de menu de contexto para notificar o usuário que o item foi selecionado.](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_ContextMenu")<br />O item que tem gerar o foco de ganhos de menu de contexto para notificar o usuário que o item foi selecionado.
  
#### <a name="keyboard"></a>Teclado  
O modo de exibição de árvore deve fornecer a capacidade de selecionar itens e expandir/recolher nós usando o teclado. Isso garante que a navegação atende às nossas necessidades de acessibilidade.  
  
##### <a name="tree-view-control"></a>Controle de exibição de árvore  
Controles em árvore Visual Studio devem seguir comuns de navegação de teclado:  
  
-   **Seta para cima:** selecionar itens movendo a árvore  
  
-   **Seta para baixo:** selecionar itens movendo para baixo da árvore  
  
-   **Seta para a direita:** expanda um nó na árvore  
  
-   **Seta para a esquerda:** recolher um nó na árvore  
  
-   **Insira a chave:** Iniciar, carregar, execute o item selecionado  
  
##### <a name="trid-tree-view-and-grid-view"></a>Trid (exibição de árvore e exibição de grade)  
Um controle trid é um controle complexo que contém uma exibição de árvore em uma grade. Expandindo, recolhendo e navegar a árvore devem respeitar os mesmos comandos de teclado como um modo de exibição de árvore, com as seguintes adições:  
  
-   **Seta para a direita:** expanda um nó. Depois que o nó é expandido, deverá continuar navegando até a coluna mais à direita. Navegação deve parar no final da linha.  
  
-   **Guia:** navega para a célula mais próxima à direita.  No final da linha, navegação continua para a próxima linha.  
  
-   **Shift + Tab:** navega para a célula mais próxima à esquerda.  No início da linha, navegação continua a célula mais à direita na linha anterior.  
  
![Um controle trid no Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />Um controle trid no Visual Studio
