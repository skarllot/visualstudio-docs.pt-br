---
title: Layout para o Visual Studio | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
caps.latest.revision: 2
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
ms.openlocfilehash: fad5b6c304473244fd26cd8acc612ab3d37eda67
ms.lasthandoff: 02/22/2017

---
# <a name="layout-for-visual-studio"></a>Layout do Visual Studio
A maioria das caixas de diálogo do Visual Studio [layout de caixa de diálogo utilitário](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout), que são o unthemed caixas de diálogo padrão que seguem [princípios de layout de caixa de diálogo Windows Desktop](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx). Como o Visual Studio vai para atualizar sua interface do usuário, algumas das caixas de diálogo mais proeminentes têm um novo design que estabelece a eles como definição de produto experiências. Essas [layout da caixa de diálogo com temas](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) têm uma aparência com temas.  
  
##  <a name="a-namebkmkutilitydialoglayouta-utility-dialog-layout"></a><a name="BKMK_UtilityDialogLayout"></a>Layout da caixa de diálogo Utilitário  
  
-   Todos os controles dentro de uma caixa de diálogo Utilitário devem iniciar na parte superior/esquerda e para baixo de fluxo.  
  
-   Nunca center controles em uma caixa de diálogo para preencher uma grande área.  
  
-   Use a fonte de ambiente de todo o texto de caixa de diálogo. Ao escrever uma especificação visual, especifique a fonte de ambiente em vez de selecionar uma fonte e tamanho. Consulte [a fonte de ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
-   Use espaçamento de controle consistente e posicionamento para suportar o objetivo de qualidade na habilidade.  
  
-   Caixas de diálogo podem se tornar mais complexas de um número maior de controles, um juxtaposition exclusivo de controles ou ambos. Para essas situações complexas, permitir espaço suficiente entre agrupamentos de controle para fornecer ao usuário um fluxo lógico para analisar.  
  
### <a name="utility-dialog-layout-examples"></a>Exemplos de layout da caixa de diálogo Utilitário  
 Todas as dimensões são expressas em pixels.  
  
 ![Espaçamento de caixa de diálogo para rótulos acima dos controles](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801 a_UtilitySpacingAbove")  
  
 **Figura 08.01-r: Diretrizes para caixas de diálogo do utilitário com rótulos acima dos controles de espaçamento**  
  
 ![Espaçamento de diálogo rótulos à esquerda dos controles de](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801 b_UtilitySpacingLeft")  
  
 **Figura 08.01-b: Diretrizes para caixas de diálogo do utilitário com rótulos à esquerda dos controles de espaçamento**  
  
### <a name="layout-details"></a>Detalhes de layout  
  
#### <a name="margins"></a>Margens  
  
-   Todas as caixas de diálogo devem ter uma borda de 12 pixels ao redor de todas as bordas.  
  
-   Margens de um quadro de grupo devem ser 9 pixels da borda do quadro.  
  
-   Margens de um controle de guia devem ser 6 pixels da borda do controle guia.  
  
#### <a name="command-buttons"></a>Botões de comando  
  
-   Botões de comando operam no quadro da caixa de diálogo, não no conteúdo. Eles devem ser colocados na parte inferior direita e devem ter espaço suficiente variável acima para definir os botões separadas.  
  
-   Se houver botões horizontal que operam na caixa de diálogo, a configuração de botão de comando alternativo é uma pilha vertical no canto superior direito. Consulte [botões de comando interna](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) abaixo.  
  
-   O espaço à esquerda dos botões de comando (inferior lado esquerdo da caixa de diálogo) é considerado parte da "faixa" dos controles de operação do diálogo. A única coisa que deve interferir em que o espaço é um link de Ajuda que é relevante para a tarefa ou a caixa de diálogo.  
  
-   Botões de comando devem ser 23 x 75 pixels.  
  
-   Botões de comando devem ser 6 pixels de distância.  
  
 ![Alinhamento de botão básico](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801 c_ButtonAlign")  
  
 **Figura 08.01-c: Alinhamento de botão básico**  
  
#### <a name="labels"></a>Rótulos  
  
-   Alinhar à esquerda todos os rótulos.  
  
-   Para rótulos que ficam acima de um controle, eles devem esquerda precisamente com o controle abaixo dele e a parte inferior do rótulo deve ser 5 pixels acima da parte superior de outro controle (por exemplo, uma caixa de combinação).  
  
-   Para rótulos que ficam à esquerda dos controles, a largura mínima entre o rótulo e o controle de entrada é de 10 pixels. Uma segunda coluna implícita deve ser estabelecida para alinhar as caixas de texto, caixas de combinação ou outros controles.  
  
-   Rótulos são sentença inteira e seguidos por dois pontos. Consulte [estilo de texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).  
  
#### <a name="distance-between-controls"></a>Distância entre controles  
 Controles de pilha razoavelmente. Não há nenhuma diretriz absoluto para o espaçamento entre controles empilhados. Tightness entre os controles podem variar ligeiramente entre as caixas de diálogo. O espaçamento recomendado é 20 pixels para controle vertical/pares e 9 pixels para controle horizontal/pares. O espaçamento mínimo controle pares horizontal é 6 pixels.  
  
 ![Recomendado a distância entre os controles](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801 d_ControlDistance")  
  
 **Figura 08.01-d Recomendações para a distância entre os controles**  
  
#### <a name="control-indentation"></a>Recuo de controle  
 Quando os controles são aninhados, alinhe controles internos horizontalmente com a borda esquerda do controle acima, geralmente o rótulo.  
  
 ![Aninhados alinhamento do controle](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801 e_ControlAlign")  
  
 **Figura 08.01-e: Alinhamento do controle aninhado**  
  
#### <a name="control-width"></a>Largura do controle  
 A largura de uma caixa de texto ou outros controles semelhantes deve ter menos de entrada para o campo média. A palavra em inglês média é cinco caracteres. Por exemplo, uma caixa de texto que requer um nome de caminho longo deve ser desde que permite que o layout horizontal, enquanto uma lista suspensa de nomes de plataforma só devem ser um comprimento que permite a entrada mais longa.  
  
#### <a name="helper-text"></a>Texto de ajuda  
  
-   Uma caixa de diálogo pode exibir o texto de Ajuda que fornece mais informações sobre a finalidade da caixa de diálogo. Isso normalmente fica na parte superior e pode ser de 1 a 2 frases.  
  
-   O comprimento da linha deve ser uma largura à vontade para um usuário analisar e ler. Uma caixa de diálogo média deve ser não mais de 550 pixels de largura.  
  
####  <a name="a-namebkmkinteriorcommandbuttonsa-interior-command-buttons"></a><a name="BKMK_InteriorCommandButtons"></a>Botões de comando interna  
 Em caixas de diálogo mais complexas, um controle interno pode ter seus próprios botões relacionados, o que podem afetar onde se encontram botões de confirmação da caixa de diálogo.  
  
-   Use os botões de alinhamento vertical (coluna) do interior quando **Okey**/**Cancelar** horizontal é exibido no canto inferior direito.  
  
-   Use um alinhamento horizontal (linha) do interior botões quando **Okey**/**Cancelar** são orientados verticalmente no canto superior direito. Essa situação é menos comum.  
  
-   Tamanho do botão interiores deve ter como destino o tamanho do botão padrão de 75 x 23 pixels, correspondência de tamanho de **Okey**/**Cancelar** botões quando possível. Se o rótulo do botão faz com que o botão exceder o tamanho do botão padrão, os outros botões no conjunto devem ser alinhada com esse tamanho maior.  
  
 ![Botões Okey horizontal e cancelar](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801 f_HorizOKCan")  
  
 **Figura 08.01-f: Botões de Interior Vertical com Okey/Cancelar horizontal**  
  
 ![Botões Okey vertical e cancelar](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801 g_VertOKCan")  
  
 **Figura 08.01-g Botões de interiores Horizontal com Okey/Cancelar vertical**  
  
#### <a name="browse-button"></a>[Procurar...] botão  
 **[Procurar...] ** botões que seguem uma caixa de texto devem explicitar "Procurar …" por completo, incluindo as reticências. Se o espaço total ou há vários **[procurar...] ** botões na tela, o botão podem ser reduzida para apenas as reticências.  
  
##  <a name="a-namebkmkthemeddialoglayouta-themed-dialog-layout"></a><a name="BKMK_ThemedDialogLayout"></a>Layout da caixa de diálogo com temas  
 Caixas de diálogo com temas no Visual Studio têm uma aparência mais clara e oferecem mais espaço em branco. Tipografia fornece mais ênfase e interesse, oferecendo mais aberto espaçamento entre linhas e uma variação de pesos e tamanhos de fonte. Sempre que possível, barras de título e chrome foram reduzidas ou removidas. O layout dessas caixas de diálogo deve seguir este padrão básico:  
  
1.  O plano de fundo da caixa de diálogo é branco.  
  
2.  Há uma borda da regra 1 pixel em um valor médio cinza.  
  
3.  O título da caixa de diálogo não reside em uma barra de título, mas fornece apelo visual e ênfase em um tamanho de ponto maior. (Consulte a seção de tamanho de fonte em [estilo de texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).)  
  
4.  Juntamente com o texto adicional, como uma descrição de rótulos devem ser **fonte do ambiente + negrito**.  
  
5.  Interiores colunas são separadas por uma regra de 1 pixel em cinza claro.  
  
6.  Links padrão têm sem sublinhado. Estados em foco e pressionados tem uma alteração de cor mais sublinhado.  
  
7.  Confirmar botões (como **Okey**/**Cancelar**) ficar no canto inferior direito.  
  
### <a name="themed-dialog-layout-examples"></a>Exemplos de layout de caixa de diálogo com temas  
 ![Layout da caixa de diálogo com temas](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801 h_ThemedDialog")  
  
 **Figura 08.01-h: Caixa de diálogo com temas**  
  
 ![Dimensões da caixa de diálogo com temas](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801 i_ThemedDialogDimensions")  
  
 **Figura 08.01-i: Temas diálogo – dimensões**  
  
 ![Fontes de tema diálogo](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801 j_ThemedDialogFonts")  
  
 **Figura 08.01-j: Temas diálogo – fontes**  
  
 ![Cores do tema diálogo](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801 k_ThemedDialogColors")  
  
 **Figura 08.01-k Com temas diálogo – cores**  
  
## <a name="see-also"></a>Consulte também  
 [Padrões de aplicativo para o Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)   
 [Controles (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx)   
 [Caixas de diálogo (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx)
